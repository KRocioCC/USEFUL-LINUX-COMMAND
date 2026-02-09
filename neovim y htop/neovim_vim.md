# VIM y NEOVIM

## VIM
![VIM logo](https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/vim/vim-original.svg)

Vim es un editor de texto altamente configurable y eficiente, diseñado para hacer la edición de texto muy rápida. Es modal, lo que significa que tiene diferentes modos para distintas tareas.

### Instalación de Vim

```bash
sudo apt update
sudo apt install vim
```

También puedes usar:
```bash
sudo apt-get install vim
```

**Verificar la instalación:**
```bash
vim --version
```

### Abrir archivos con Vim

```bash
vim                      # Abre Vim vacío
vim archivo.txt          # Abre o crea un archivo

```

**Nota:** Al abrir Vim estarás en **Modo Normal** por defecto.

## Modos de Vim

Vim tiene 4 modos principales. Para cambiar entre ellos usa las teclas indicadas.

### 1. Modo Normal (Normal Mode)

Es el modo por defecto al abrir Vim. Se usa para navegar, copiar, pegar y ejecutar comandos.

**Cómo llegar:** Presiona `ESC` desde cualquier modo.

#### Navegación básica:
* `h` - Izquierda
* `j` - Abajo
* `k` - Arriba
* `l` - Derecha
* `w` - Siguiente palabra (inicio)
* `e` - Siguiente palabra (final)
* `b` - Palabra anterior
* `0` - Inicio de la línea
* `$` - Final de la línea
* `gg` - Inicio del documento
* `G` - Final del documento


**Cómo entrar desde Modo Normal:**
* `i` - Insertar antes del cursor
* `I` - Insertar al inicio de la línea
* `a` - Insertar después del cursor (append)
* `A` - Insertar al final de la línea
* `o` - Crear nueva línea abajo y entrar a inserción
* `O` - Crear nueva línea arriba y entrar a inserción

**Cómo salir:** Presiona `ESC` para volver al Modo Normal.rsor
* `A` - Insertar al final de la línea
* `o` - Crear nueva línea abajo
* `O` - Crear nueva línea arriba
* `ESC` - Volver al modo normal

Permite ejecutar comandos como guardar, salir, buscar y reemplazar.

**Cómo entrar:** Escribe `:` desde el Modo Normal.

#### Comandos esenciales:
* `:q` - Salir (solo si no hay cambios sin guardar)
* `:q!` - Salir sin guardar cambios (forzar salida)
* `:w` - Guardar (write)
* `:wq` o `:x` - Guardar y salir
* `:w archivo.txt` - Guardar como
* `:e archivo.txt` - Abrir otro archivo (edit)

#### Configuración:
* `:set number` - Mostrar números de línea
* `:set nonumber` - Ocultar números de línea
* `:syntax on` - Activar resaltado de sintaxis
* `:syntax off` - Desactivar resaltado de sintaxis

#### Búsqueda y reemplazo:
* `:%s/viejo/nuevo/g` - Reemplacopiar, cortar o realizar operaciones.

**Cómo entrar desde Modo Normal:**
* `v` - Modo visual carácter por carácter
* `V` - Modo visual línea por línea (selecciona líneas completas)
* `Ctrl + v` - Modo visual en bloque (selección rectangular)

**Operaciones en selección:**
* `y` - Copiar (yank) la selección
* `d` - Cortar (delete) la selección
* `p` - Pegar después del cursor
* `P` - Pegar antes del cursor

**Cómo salir:** Presiona `ESC` para volver al Modo Normal.

---

## Comandos Útiles de Edición (Modo Normal)

### Copiar, Cortar y Pegar:
* `yy` - Copiar (yank) la línea completa
* `dd` - Cortar (delete) la línea completa
* `x` - Borrar el carácter bajo el cursor
* `p` - Pegar después del cursor o línea
* `P` - Pegar antes del cursor o línea
* `número + dd` - Borrar número de líneas (ej: `3dd` borra 3 líneas)
* `número + yy` - Copiar número de líneas (ej: `2yy` copia 2 líneas)

### Deshacer y Rehacer:
* `u` - Deshacer (undo) último cambio
* `Ctrl + r` - Rehacer (redo)
* `.` - Repetir último comando de edición

### Búsqueda:
* `/texto` - Buscar "texto" hacia adelante
* `?texto` - Buscar "texto" hacia atrás
* `n` - Ir al siguiente resultado
* `N` - Ir al resultado anterior
* `*` - Buscar la palabra bajo el cursor

### Reemplazar:
* `r + caracter` - Reemplazar el carácter bajo el cursor
* `R` - Entrar en modo reemplazo (sobrescribe)
* `cw` - Cambiar palabra (borra y entra en modo inserción)
* `u` - Deshacer
* `Ctrl + r` - Rehacer
* `.` - Repetir último comando

**Búsqueda:**
* `/texto` - Buscar hacia adelante
* `?texto` - Buscar hacia atrás
* `n` - Siguiente resultado
* `N` - Resultado anterior

---

## NEOVIM

![Neovim logo](https://cdn.worldvectorlogo.com/logos/neovim.svg)

Neovim es un fork moderno de Vim, compatible y más actualizado.

Si ya sabes usar Vim, Neovim es prácticamente lo mismo. Lo importante es que Neovim es más moderno y trae nuevas características.

**Características nuevas más importantes:**
* **Nuevo sistema de plugins** que permite multitud de lenguajes: clojure, lisp, go, haskell, lua, javascript, perl, python, ruby y rust.
* **Nuevas rutas de configuración** que mantienen una carpeta de usuario más limpia.

### Instalación

```bash
sudo apt update
sudo apt install neovim
```

También puedes usar:

```bash
sudo apt-get install neovim
```

Verificar:
```bash
nvim --version
```

### Rutas de configuración

* Vim: `~/.vimrc`
* Neovim: `~/.config/nvim/init.vim`
* (Opcional) `~/.config/nvim/init.lua`

### Administradores de plugins (resumen)

Antes se copiaban los archivos de plugins en directorios específicos de forma manual; eso dificultaba actualizarlos.
Neovim soluciona esto con administradores de plugins que se encargan de mantenerlos al día.

Algunos de los más usados:
* **pathogen**
* **vundle**
* **dein**
* **vim-plug**

### Plugins (vim-plug, básico)

Para instalar **vim-plug** necesitas `git` y `curl`. Luego ejecuta:
```bash
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
  https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Configurar:
```bash
nvim ~/.config/nvim/init.vim
```

```vim
call plug#begin('~/.local/share/nvim/plugged')
Plug 'iCyMind/NeoSolarized'
call plug#end()

set termguicolors
set background=dark
colorscheme NeoSolarized
```

Instalar plugins (en Neovim):
```vim
:PlugInstall
```

Recargar configuración (opcional):
```vim
:so ~/.config/nvim/init.vim
```

Cierra la instalación con `q`.

Si quieres revisar más sobre el tema: [Solarized](https://ethanschoonover.com/solarized/).
