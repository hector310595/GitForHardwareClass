# Antes de la sesión 13: checklist de preparación

⏱️ **Tiempo estimado: 30 minutos.** Hazlo **antes** de la clase. Si llegas sin esto, pierdes la primera media hora de la sesión instalando.

Al final de esta guía hay una **prueba final**. Si la pasa, estás listo.

---

## 1. Crea tu cuenta de GitHub

1. Entra a <https://github.com/signup> y crea una cuenta. Puedes usar tu correo PUCP.
2. Elige un nombre de usuario profesional (lo verán futuros empleadores): `jperez-mecatronica` mejor que `xXgamer99Xx`.
3. Verifica tu correo.

## 2. Instala Git

| Sistema | Qué hacer |
|---------|-----------|
| **Windows** | Descarga **Git for Windows** de <https://git-scm.com/download/win> e instálalo con las opciones por defecto. Esto instala también **Git Bash**, la terminal que usaremos en clase. |
| **macOS** | Abre la app **Terminal** y escribe `git --version`. Si no está instalado, macOS te ofrecerá instalar las "Command Line Developer Tools": acepta. |
| **Linux** | `sudo apt install git` (Ubuntu/Debian) o el equivalente de tu distribución. |

> 💡 **En clase siempre usaremos una terminal:** *Git Bash* en Windows, *Terminal* en macOS/Linux. Todos los comandos de las guías funcionan igual en ambas.

## 3. Instala KiCad 10 y un editor de texto

- **KiCad 10** (la última versión 10.0.x): <https://www.kicad.org/download/>. Si tienes KiCad 9 instalado, puedes conservarlo: las versiones conviven sin problema.
- **Visual Studio Code** (para editar el README): <https://code.visualstudio.com/>

## 4. Configura la autenticación con GitHub

GitHub ya no acepta tu contraseña desde la terminal. Hay que configurar un método de acceso:

- **Windows:** no hagas nada. Git for Windows trae el *Git Credential Manager*: la primera vez que hagas `git push` se abrirá el navegador para que inicies sesión en GitHub.
- **macOS / Linux:** instala la herramienta de GitHub (`gh`) y úsala para autenticarte:
  ```bash
  # macOS (necesitas Homebrew: https://brew.sh)
  brew install gh
  # Ubuntu/Debian: ver https://github.com/cli/cli/blob/trunk/docs/install_linux.md

  gh auth login
  ```
  Responde: **GitHub.com** → **HTTPS** → *Authenticate Git with your GitHub credentials?* **Yes** → **Login with a web browser**.

## 5. Configura Git (una sola vez por computadora)

Abre la terminal y copia estos comandos **cambiando nombre y correo**:

```bash
git config --global user.name "Juan Pérez"
git config --global user.email "tu-correo@pucp.edu.pe"
git config --global init.defaultBranch main
git config --global core.editor "code --wait"
```

| Comando | Para qué sirve |
|---------|----------------|
| `user.name` / `user.email` | Firma de tus commits. Usa el **mismo correo** de tu cuenta GitHub. |
| `init.defaultBranch main` | La rama principal se llamará `main`, igual que en GitHub. |
| `core.editor "code --wait"` | Si Git necesita que escribas un mensaje, abrirá VS Code (y no *vim*, del que es difícil salir). |

Verifica:

```bash
git config --global --list
```

## 6. ✅ Prueba final

En la terminal:

```bash
git --version
mkdir -p ~/proyectos
cd ~/proyectos
git clone https://github.com/hector310595/GitForHardwareClass.git curso
ls curso
```

**Debes ver** algo como:

```
git version 2.4x.x
Cloning into 'curso'...
README.md  guia  inicio  recursos
```

Si llegaste aquí: **estás listo para la sesión.** 🎉

> ⚠️ **No trabajes dentro de OneDrive, Google Drive ni Dropbox.** Sincronizar una carpeta de Git con la nube puede corromper el repositorio. Por eso usamos `~/proyectos` (en Windows es `C:\Users\TU_USUARIO\proyectos`).

---

### ¿Problemas?

| Síntoma | Solución |
|---------|----------|
| `git: command not found` | Cierra y vuelve a abrir la terminal. En Windows asegúrate de abrir **Git Bash**, no CMD. |
| `code: command not found` | En VS Code: `Ctrl/Cmd+Shift+P` → *Shell Command: Install 'code' command in PATH*. En Windows reinstala VS Code marcando "Add to PATH". |
| Windows: `~/proyectos` no aparece en el Explorador | Está en `C:\Users\TU_USUARIO\proyectos`. Desde Git Bash puedes escribir `explorer .` para abrir la carpeta actual. |
| `gh auth login` falla | Usa la opción de pegar un *token*: GitHub → Settings → Developer settings → Personal access tokens. |

Si nada funciona, escribe al docente **antes** de la clase con una captura del error.
