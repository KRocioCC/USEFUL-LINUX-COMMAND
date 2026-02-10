# ZSH y Oh-My-ZSH

> Guía para instalar ZSH + Oh-My-ZSH con plugins y temas personalizados.

---

## Tabla de Contenidos

1. [ZSH](#zsh)
2. [Oh-My-ZSH](#oh-my-zsh)
3. [Plugins Disponibles](#plugins-disponibles)
4. [Temas](#temas)

---

## ZSH

**ZSH** (Z shell) es una versión mejorada de **Bash**, ofreciendo más funcionalidades y personalización.

### Ventajas principales:
- Mayor eficiencia y velocidad
- Completado de tabulador mejorado (autocompletado inteligente)
- Expansión de nombres de fichero mejorada
- Manejo de arrays más potente
- Totalmente personalizable

### Instalación

```bash
sudo apt update
sudo apt install zsh
```

También puedes usar:
```bash
sudo apt-get install zsh
```

**Verificar instalación:**
```bash
zsh --version
```

**Verificar que estás usando ZSH:**
```bash
echo $SHELL
# Debería mostrar: /usr/bin/zsh o /bin/zsh
```

**Ver tu shell actual:**
```bash
ps -p $$
```

---

## Oh-My-ZSH

**Oh-My-ZSH** es un framework que facilita la instalación y gestión de plugins y temas para ZSH.

### Instalación

#### Opción 1: Con CURL (Recomendado)
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

#### Opción 2: Con WGET
```bash
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

**La instalación:**
- Hace copia de seguridad de tu `.zshrc` actual (lo renombra a `.zshrc.pre-oh-my-zsh`)
- Crea un nuevo archivo `.zshrc` con configuración de Oh-My-ZSH
- Configura ZSH como shell por defecto automáticamente
- Instala el tema por defecto `robbyrussell`

---

## Plugins Disponibles


Luego, actualiza la configuración:
```bash
source ~/.zshrc
```

---

### Git Plugin

**Viene incluido en Oh-My-ZSH**. Para usarlo, agregue la palabra git a la matriz de plugins en el archivo zshrc.

**Activar:**
```zsh
plugins=(git ...)
```

| Alias | Comando | Descripción |
|-------|---------|-------------|
| `ga` | `git add` | Agregar archivos al stage |
| `gaa` | `git add --all` | Agregar todos los archivos |
| `gb` | `git branch` | Listar ramas |
| `gcmsg` | `git commit -m` | Hacer commit con mensaje |
| `gco` | `git checkout` | Cambiar de rama |
| `ggl` | `git pull origin $(rama_actual)` | Pull de la rama actual |
| `ggp` | `git push origin $(rama_actual)` | Push de la rama actual |
| `glo` | `git log --oneline --decorate` | Ver historial de commits |
| `gra` | `git remote add` | Agregar repositorio remoto |
| `grv` | `git remote -v` | Ver repositorios remotos |
| `gst` | `git status` | Ver estado del repositorio |
| `gss` | `git status -s` | Ver estado resumido |

[Documentación completa](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git)

---

---

### Composer Plugin

Aliases y autocompletado para **Composer** (gestor de dependencias PHP).

**Activar:**
```zsh
plugins=(
  git
  composer
)
```

| Alias | Comando | Descripción |
|-------|---------|-------------|
| `cpp` | `composer create-project` | Crear nuevo proyecto |
| `ci` | `composer install` | Instalar dependencias |
| `cr` | `composer require` | Agregar paquete |
| `cu` | `composer update` | Actualizar dependencias |

[Documentación completa](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/composer)

---

### Docker Compose Plugin

Aliases para **Docker Compose**.

**Activar:**
```zsh
plugins=(
  docker-compose
)
```

| Alias | Comando | Descripción |
|-------|---------|-------------|
| `dcb` | `docker-compose build` | Construir contenedores |
| `dce` | `docker-compose exec` | Ejecutar comando en contenedor |
| `dcr` | `docker-compose run` | Ejecutar comando |
| `dcstop` | `docker-compose stop` | Detener contenedores |
| `dcup` | `docker-compose up` | Iniciar servicios |
| `dcdn` | `docker-compose down` | Detener y remover |
| `dcstart` | `docker-compose start` | Iniciar contenedores |

[Documentación completa](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/docker-compose)

---

### Laravel Sail Plugin

Plugin para facilitarinteracción con **Laravel Sail**.

**Instalación:**
```bash
git clone https://github.com/ariaieboy/laravel-sail \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/laravel-sail
```

**Activar:**
```zsh
plugins=(laravel-sail)
```

| Alias | Comando | Descripción |
|-------|---------|-------------|
| `s` | `sail` | Ejecutar sail |
| `sup` | `sail up` | Iniciar servicios |
| `sud` | `sail up -d` | Iniciar en segundo plano |
| `sdown` | `sail down` | Detener servicios |
| `sb` | `sail build` | Construir imagen |
| `sa` | `sail artisan` | Ejecutar artisan |
| `sp` | `sail php` | Ejecutar PHP |
| `sc` | `sail composer` | Ejecutar composer |
| `sn` | `sail npm` | Ejecutar npm |

[Documentación completa](https://github.com/ariaieboy/laravel-sail)

---

### zsh-Syntax-Highlighting Plugin

Resalta comandos mientras escribes. **Altamente recomendado**.

**Colores:**
- Verde: comando válido
- Rojo: comando no válido
- Azul: ruta válida

**Instalación:**
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

**Activar:**
```zsh
plugins=(zsh-syntax-highlighting)
```

> Tip: Debe ser el último plugin en la lista para funcionar correctamente.

---

### zsh-Autosuggestions Plugin

Sugiere comandos basados en tu historial mientras escribes. **Altamente recomendado**.

**Instalación:**
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

**Activar:**
```zsh
plugins=(zsh-autosuggestions)
```

**Uso:**
- Aparecen sugerencias en gris mientras escribes
- Presiona `→` (flecha derecha) para aceptar la sugerencia completa
- Presiona `Ctrl + →` para aceptar una palabra de la sugerencia
- Presiona `Esc` para ignorar la sugerencia

---

## Temas

### Powerlevel10k

**Powerlevel10k** es el tema más popular. Ofrece un prompt hermoso y personalizable.

**Instalación:**
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

**Configurar en `~/.zshrc`:**
```zsh
ZSH_THEME="powerlevel10k/powerlevel10k"
```

**Personalizar:**
```bash
p10k configure
```

Esto abrirá un asistente interactivo para configurar la apariencia del prompt.
[Documentación completa](https://github.com/romkatv/powerlevel10k)



### Comandos útiles de Oh-My-ZSH:

**Actualizar Oh-My-ZSH:**
```bash
omz update
# o 
upgrade_oh_my_zsh
```

**Reiniciar ZSH completamente:**
```bash
exec zsh
```

**Desinstalar Oh-My-ZSH:**
```bash
uninstall_oh_my_zsh
```

### Atajos de teclado útiles:

**Navegación:**
- `Ctrl + A` - Ir al inicio de la línea
- `Ctrl + E` - Ir al final de la línea
- `Ctrl + U` - Borrar desde el cursor al inicio
- `Ctrl + K` - Borrar desde el cursor al final
- `Ctrl + W` - Borrar palabra anterior
- `Alt + B` - Retroceder una palabra
- `Alt + F` - Avanzar una palabra

**Historial:**
- `Ctrl + R` - Buscar en historial (reverse search)
- `Ctrl + P` o `↑` - Comando anterior
- `Ctrl + N` o `↓` - Comando siguiente
- `!!` - Ejecutar último comando
- `!$` - Último argumento del comando anterior
