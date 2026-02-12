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

**ZSH** Es un intérprete de comandos, es una versión mejorada de **Bash**, ofreciendo más funcionalidades y personalización.

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

**Durante la instalación, se ejecutan automáticamente los siguientes pasos:**

1. **Backup de tu configuración actual:**
   ```bash
   # Copia de seguridad: .zshrc → .zshrc.pre-oh-my-zsh
   cp ~/.zshrc ~/.zshrc.pre-oh-my-zsh
   ```
   Tu archivo `.zshrc` anterior se guarda como `.zshrc.pre-oh-my-zsh` para poder revertir si es necesario.

2. **Crear nuevo archivo `.zshrc` con configuración de Oh-My-ZSH:**
   ```bash
   # Descarga y copia el repositorio original
   git clone https://github.com/ohmyzsh/ohmyzsh.git ~/.oh-my-zsh

   # Gwnera el nuevo .zshrc desde la plantilla
   cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
   ```
   Ahora tendras un `.zshrc` completamente nuevo optimizado para Oh-My-ZSH.

3. **Configurar ZSH como shell por defecto:**
   ```bash
   chsh -s $(which zsh)
   ```
   Tu próxima sesión de terminal usará automáticamente ZSH.

4. **Instalar el tema por defecto `robbyrussell`:**
   ```bash
   # Se activa automáticamente editando ~/.zshrc:
   # ZSH_THEME="robbyrussell"
   ```
   Verifica que en tu `~/.zshrc` aparezca esta línea (debe estar por defecto):
   ```bash
   grep "ZSH_THEME" ~/.zshrc
   ```

**Después de la instalación, recarga la configuración:**
```bash
source ~/.zshrc
# o simplemente reinicia la terminal
```

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
