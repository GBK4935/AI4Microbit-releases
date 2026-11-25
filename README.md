# AI4Microbit — Descargas del curso

Repositorio **solo de distribución**. Aquí no hay código fuente editable: únicamente se publican los paquetes listos para descargar.

## Descarga

| Sistema | Archivo | Enlace |
|---|---|---|
| Windows 10/11 (64 bits) | `AI4Microbit_v1.1.0_Windows_Portable.zip` | [Descargar](https://github.com/GBK4935/AI4Microbit-releases/releases/download/v1.1.0-curso/AI4Microbit_v1.1.0_Windows_Portable.zip) |
| Linux x86_64 | `AI4Microbit_v1.1.0_Linux.tar.gz` | [Descargar](https://github.com/GBK4935/AI4Microbit-releases/releases/download/v1.1.0-curso/AI4Microbit_v1.1.0_Linux.tar.gz) |

También puedes ver todos los archivos en la página del release:

<https://github.com/GBK4935/AI4Microbit-releases/releases/tag/v1.1.0-curso>

No hace falta cuenta de GitHub para descargar.

## Verificación de integridad

Comprueba el SHA-256 después de descargar:

```text
DF389FF5F9FEACDDFCC14CCF8BFAAD9825D2DC958807DAEBCBE29FE813624854  AI4Microbit_v1.1.0_Windows_Portable.zip
40E3702798C9A3D81872192094053C7491613BAE3EE9B5ACFF9B601C63D9FF57  AI4Microbit_v1.1.0_Linux.tar.gz
```

Windows (PowerShell):

```powershell
Get-FileHash .\AI4Microbit_v1.1.0_Windows_Portable.zip -Algorithm SHA256
```

Linux:

```bash
sha256sum AI4Microbit_v1.1.0_Linux.tar.gz
```

Si el hash no coincide, no ejecutes el archivo: vuelve a descargarlo desde este repositorio.

## Windows: instalación

1. Descarga y descomprime el ZIP en una carpeta local. No lo ejecutes desde dentro del ZIP.
2. Entra en la carpeta `AI4Microbit_v1.1.0_Windows`.
3. Doble clic en `iniciar_ai4microbit.bat`.
4. Se abrirá el navegador en `http://localhost:8765`.

El paquete **ya incluye Python 3.12.8 y las librerías**. No hace falta instalar Python, crear un entorno virtual ni tener permisos de administrador.

Si Windows SmartScreen muestra un aviso por ser un archivo descargado de Internet:

1. Comprueba primero el SHA-256.
2. Pulsa **Más información** → **Ejecutar de todas formas**.

## Linux: instalación

1. Descarga y extrae:

```bash
tar -xzf AI4Microbit_v1.1.0_Linux.tar.gz
cd AI4Microbit_v1.1.0_Linux
chmod +x scripts/*.sh
```

2. Necesitas Python 3.10 o superior con `venv`:

```bash
sudo apt install python3 python3-venv python3-pip
```

3. Arranca:

```bash
./scripts/iniciar_ai4microbit.sh
```

Para usar la micro:bit física sin permisos de administrador, añade tu usuario al grupo `dialout` y vuelve a iniciar sesión:

```bash
sudo usermod -aG dialout $USER
```

## Requisitos y funcionamiento

- **Obligatorio:** Windows 10/11 de 64 bits o Linux x86_64.
- **Opcional:** una placa BBC micro:bit V1/V2 conectada por USB. Sin placa, la aplicación funciona en **modo simulador**.
- **Opcional:** [Ollama](https://ollama.com) para IA local. Sin Ollama, la aplicación usa el **modo educativo offline** con plantillas y lógica heurística.

Para activar la IA local:

```bash
ollama pull qwen2.5:1.5b
```

El modelo `qwen2.5:1.5b` es el predeterminado y funciona en equipos modestos. También puedes usar otros modelos instalados desde la interfaz.

### Modo solo local

Por defecto el servidor escucha en toda la red del aula, para que el profesor pueda compartir `http://IP-DEL-PROFESOR:8765`. Si trabajas en un equipo personal y quieres que solo sea accesible desde ese ordenador:

```bat
iniciar_ai4microbit.bat --local-only
```

```bash
./scripts/iniciar_ai4microbit.sh --local-only
```

## Privacidad y seguridad

- La aplicación se ejecuta **en tu ordenador**. No envía proyectos ni datos a la nube.
- Los paquetes **no incluyen claves de API, tokens ni archivos de configuración local**.
- Si usas el buzón de incidencias con un token de GitHub, ese token se guarda localmente en `github_config.json`. No compartas ni comprimas la carpeta después de configurarlo.
- No publiques capturas con tokens, rutas personales o datos de alumnos.

## Problemas frecuentes

**El puerto 8765 está ocupado**  
Cierra otra instancia de AI4Microbit o reinicia el equipo.

**Ollama no aparece conectado**  
Comprueba que Ollama está arrancado (`ollama serve`) y que has descargado un modelo (`ollama list`). La aplicación lo detecta automáticamente en unos segundos, sin reiniciar.

**La micro:bit no aparece**  
Prueba otro cable USB (algunos solo cargan), otro puerto y revisa el grupo `dialout` en Linux. Mientras tanto, usa el simulador.

**El antivirus bloquea el Python portable**  
Es un falso positivo habitual de ejecutables embebidos. Verifica el SHA-256 y, si el centro lo permite, añade una exclusión para la carpeta de la aplicación.

**No se abre el navegador**  
Abre manualmente <http://localhost:8765>.

## Licencia

MIT. Consulta [LICENSE](LICENSE).

El código fuente se mantiene en un repositorio privado; este repositorio público solo contiene los paquetes de distribución y su documentación de uso.
