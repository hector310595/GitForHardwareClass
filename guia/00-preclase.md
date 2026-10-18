# Antes de la sesión 9: checklist de preparación

**1MTR68 · Prototipado y Manufactura de Productos Mecatrónicos**

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
>
> ⚠️ **Windows: usa Git Bash, no PowerShell ni CMD.** Algunos comandos de la guía (`ls -a`, `cp -r`, `mkdir -p`) no funcionan igual en PowerShell. Para abrir Git Bash: menú Inicio → escribe *Git Bash*, o clic derecho dentro de una carpeta → *Open Git Bash here* (en Windows 11: *Mostrar más opciones* → *Open Git Bash here*).
>
> **¿Usas clic derecho → *Abrir en Terminal*?** En Windows 11 eso abre PowerShell por defecto. Cámbialo una sola vez: abre *Terminal* → flecha **⌄** junto a la pestaña → **Configuración** → **Inicio** → **Perfil predeterminado** → **Git Bash** → **Guardar**. Si Git Bash no aparece en la lista, reinstala Git for Windows marcando *Add a Git Bash Profile to Windows Terminal*.
>
> **¿Cómo sé en cuál estoy?** PowerShell muestra `PS C:\...>`. Git Bash muestra `usuario@PC MINGW64 ~` y debajo un `$`.

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

## 6. Elige tu carpeta de trabajo

Todo lo de la sesión vivirá en **una carpeta de trabajo**: ahí estarán el material del curso (`curso/`) y tu proyecto (`demogit/`), uno al lado del otro. Elige **una** de estas opciones y úsala siempre:

**Opción A (recomendada): la carpeta `proyectos` en tu usuario.** Abre la terminal en cualquier lugar y escribe:

```bash
mkdir -p ~/proyectos
cd ~/proyectos
```

`~` significa **tu carpeta de usuario** (en Windows, `C:\Users\TU_USUARIO`; en macOS, `/Users/TU_USUARIO`). Estos comandos te llevan a `~/proyectos` **aunque hayas abierto la terminal en otra carpeta**.

**Opción B: una carpeta que tú ya tienes** (por ejemplo `D:\Proyectos\1MTR68`). Ábrela en el Explorador, clic derecho → *Open Git Bash here*. **No** escribas los comandos de la opción A: ya estás donde debes.

> En Git Bash las unidades se escriben distinto: `D:\Proyectos\1MTR68` es `/d/Proyectos/1MTR68`. Para ir ahí: `cd /d/Proyectos/1MTR68`.

Sea cual sea tu opción, comprueba dónde estás:

```bash
pwd
```

🔍 Debe mostrar tu carpeta de trabajo (por ejemplo `/c/Users/jperez/proyectos` o `/d/Proyectos/1MTR68`). **Anótala**: en clase empezarás siempre desde ahí.

## 7. ✅ Prueba final

Desde tu carpeta de trabajo:

```bash
git --version
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

> ⚠️ **Tu carpeta de trabajo no debe estar dentro de OneDrive, Google Drive ni Dropbox.** Sincronizar una carpeta de Git con la nube puede corromper el repositorio. Ojo: en muchas PCs con Windows, *Documentos* y *Escritorio* están dentro de OneDrive.

---

### ¿Problemas?

| Síntoma | Solución |
|---------|----------|
| `git: command not found` | Cierra y vuelve a abrir la terminal. En Windows asegúrate de abrir **Git Bash**, no CMD ni PowerShell. |
| `curso` se creó en otra carpeta | Clonaste desde una carpeta distinta a tu carpeta de trabajo. Muévela: `mv RUTA/curso .` desde tu carpeta de trabajo, o vuelve a clonar ahí. Usa `pwd` para saber dónde estás. |
| `code: command not found` | En VS Code: `Ctrl/Cmd+Shift+P` → *Shell Command: Install 'code' command in PATH*. En Windows reinstala VS Code marcando "Add to PATH". |
| No encuentro mi carpeta en el Explorador | Desde Git Bash escribe `explorer .` (con el punto): abre en el Explorador la carpeta donde estás. |
| `gh auth login` falla | Usa la opción de pegar un *token*: GitHub → Settings → Developer settings → Personal access tokens. |

Si nada funciona, escribe al docente **antes** de la clase con una captura del error.
