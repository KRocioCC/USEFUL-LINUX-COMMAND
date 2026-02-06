# COMANDOS DE LINUX

> Guia de comandos esenciales para administración de sistemas Linux en Ubuntu/Debian.

---

## Tabla de Contenidos

1. [GESTIÓN DEL SISTEMA](#gestión-del-sistema)
2. [GESTIÓN DE PAQUETES](#gestión-de-paquetes)
3. [CONFIGURACIÓN DEL SISTEMA](#configuración-del-sistema)
4. [GESTIÓN DE ARCHIVOS Y DIRECTORIOS](#gestión-de-archivos-y-directorios)
5. [PERMISOS Y PROPIEDAD DE ARCHIVOS](#permisos-y-propiedad-de-archivos)
6. [GESTIÓN DE USUARIOS Y GRUPOS](#gestión-de-usuarios-y-grupos)
7. [BÚSQUEDA Y FILTRADO](#búsqueda-y-filtrado)
8. [EDICIÓN DE ARCHIVOS](#edición-de-archivos)
9. [RED Y CONECTIVIDAD](#red-y-conectividad)
10. [PROCESOS Y SERVICIOS](#procesos-y-servicios)
11. [GESTIÓN DE ALMACENAMIENTO](#gestión-de-almacenamiento)
12. [EXTENSIONES GNOME](#extensiones-gnome)

---

## GESTIÓN DEL SISTEMA

### Gestionar el Nombre del Host

**Ver el nombre del host actual:**
```bash
hostnamectl
```

**Cambiar el nombre del host:**
```bash
sudo hostnamectl set-hostname nuevo-nombre-host
```
> Después de cambiar, reinicia la sesión o ejecuta `exec bash` para aplicar los cambios.

---

## GESTIÓN DE PAQUETES

### Actualización del Sistema

La actualización del sistema es fundamental para la seguridad.

| Comando | Descripción | Uso |
|---------|-------------|-----|
| `sudo apt update` | Actualiza la lista de paquetes disponibles | **Siempre primero** |
| `sudo apt upgrade` | Actualiza los paquetes instalados | Actualizaciones normales |
| `sudo apt full-upgrade` | Actualiza eliminando paquetes obsoletos si es necesario | Más agresivo que upgrade |


**Secuencia recomendada de actualización:**
```bash
# Paso 1: Actualizar lista de paquetes
sudo apt update

# Paso 2: Actualizar paquetes
sudo apt upgrade

# Paso 3: Limpiar paquetes innecesarios
sudo apt autoremove

# Paso 4: Limpiar caché
sudo apt autoclean
```

### Comandos de Limpieza

| Comando | Descripción |
|---------|-------------|
| `sudo apt autoremove` | Elimina paquetes instalados automáticamente que ya no son necesarios |
| `sudo apt autoclean` | Elimina archivos .deb en caché más antiguos que los instalados |
| `sudo apt clean` | Borra completamente el caché de paquetes |


---

## CONFIGURACIÓN DEL SISTEMA

### Reinicio/Apagado del Sistema

```bash
# Reiniciar inmediatamente
sudo reboot now

# Apagar el sistema
sudo shutdown -h now
```

### Información del Sistema

```bash
# Ver información del kernel
uname -a

# Ver información detallada del sistema
lsb_release -a

# Ver uso de disco
df -h

# Ver uso de memoria
free -h

# Ver información de CPU
lscpu
```

---

## GESTIÓN DE ARCHIVOS Y DIRECTORIOS

### Listar Archivos

```bash
# Listar archivos simples
ls

# Listar con detalles
ls -l

# Listar todos (incluyendo ocultos)
ls -a

# Listar con tamaño legible
ls -lh

# Mostrar todo con detalles y tamaño
ls -lahS
```

### Navegar por Directorios

```bash
# Ir al directorio home
cd ~

# Ir al directorio anterior
cd -

# Ir al directorio padre
cd ..

# Mostrar directorio actual
pwd

# Cambiar a un directorio específico
cd /ruta/del/directorio
```

### Crear y Eliminar

```bash
# Crear directorio
mkdir nombre-directorio

# Crear archivo vacío
touch nombre-archivo.txt

# Copiar archivo
cp archivo-origen.txt archivo-copia.txt

# Mover/renombrar archivo o directorio
mv archivo-viejo.txt archivo-nuevo.txt

# Mover archivo a otro directorio
mv archivo.txt /ruta/destino/

# Eliminar archivo
rm archivo.txt

# Eliminar directorio vacío
rmdir directorio-vacio

# Eliminar directorio con contenido
rm -r directorio-con-contenido

# Eliminar con confirmación
rm -i archivo.txt
```

### Ver Contenido de Archivos

```bash
# Ver contenido completo
cat archivo.txt

# Ver en tiempo real (útil para logs)
tail -f /var/log/archivo.log

```

---

## PERMISOS Y PROPIEDAD DE ARCHIVOS

### Cambiar Permisos

```bash
# Cambiar permisos (notación octal)
# 7 = rwx (lectura, escritura, ejecución)
# 6 = rw- (lectura, escritura)
# 5 = r-x (lectura, ejecución)
# 4 = r-- (solo lectura)
# 0 = --- (sin permisos)

chmod 755 script.sh          # rwxr-xr-x
chmod 644 archivo.txt        # rw-r--r--
chmod 700 archivo-privado    # rwx------
chmod +x script.sh           # Agregar permiso de ejecución
chmod -x archivo.txt         # Quitar permiso de ejecución
chmod u+w archivo.txt        # Agregar escritura al propietario
chmod g-r archivo.txt        # Quitar lectura al grupo
chmod o=r archivo.txt        # Solo lectura para otros
```

---

## GESTIÓN DE USUARIOS Y GRUPOS

### Información del Usuario Actual

```bash
# Ver usuario actual
whoami

# Ver ID del usuario y grupos
id

# Ver usuarios conectados
who

```

---

## BÚSQUEDA Y FILTRADO

### Buscar Archivos

```bash
# Buscar por nombre
find . -name "*.txt"

# Buscar archivos modificados hace 7 días
find . -mtime -7

```

## EDICIÓN DE ARCHIVOS

### Editores de Texto

```bash
# Editor nano (recomendado para principiantes)
nano archivo.txt

# Editor vim
vim archivo.txt

# Editor vi
vi archivo.txt

# Editar como root
sudo nano archivo.txt
```

### Operaciones Básicas con cat y echo

```bash
# Escribir contenido en archivo (sobrescribir)
echo "Contenido nuevo" > archivo.txt

# Agregar contenido al final
echo "Contenido adicional" >> archivo.txt

```

---

## RED Y CONECTIVIDAD

### Información de Red

```bash
# Ver configuración IP
ip addr show

# Ver interfaces de red
ifconfig

# Ver tabla de enrutamiento
ip route show

# Ver puertos en escucha
ss -tulpn

# Ver conexiones activas
netstat -tulpn

# Probar conectividad
ping google.com

# Ver información de red resumida
ifconfig -a

```

### SSH y Control Remoto

```bash
# Conectar por SSH
ssh usuario@host

# Conectar en puerto específico
ssh -p 2222 usuario@host


# Generar claves SSH
ssh-keygen -t rsa -b 4096
```

---


## TIPS DE PRODUCTIVIDAD

### Atajos de Teclado Útiles

| Atajo | Función |
|-------|---------|
| `Ctrl + C` | Interrumpir comando actual |
| `Ctrl + D` | Salir de terminal |
| `Ctrl + L` | Limpiar pantalla |
| `Ctrl + A` | Ir al inicio de la línea |
| `Ctrl + E` | Ir al final de la línea |
| `Ctrl + R` | Buscar en historial |
| `Ctrl + Z` | Suspender proceso |
| `Tab` | Autocompletar |
| `Tab Tab` | Mostrar opciones de autocompletado |

### Comandos de Ayuda

```bash
# Mostrar manual
man comando


# Mostrar ayuda del comando
comando --help
comando -h

# Mostrar información del comando
info comando
```

---

## EXTENSIONES GNOME

Las extensiones GNOME permiten personalizar y extender la funcionalidad del escritorio GNOME.

### Instalación

1. Instala la integración en tu navegador:
   - Chrome/Chromium/Vivaldi: https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep
   - Firefox: https://addons.mozilla.org/en-US/firefox/addon/gnome-shell-integration/

2. Instala los paquetes de soporte:
```bash
sudo apt install gnome-shell-extensions
sudo apt install chrome-gnome-shell
```

3. Descarga extensiones desde: https://extensions.gnome.org

### Extensiones Recomendadas

| Extensión | Descripción | Enlace |
|-----------|-------------|--------|
| Hide Top Bar | Oculta la barra superior de GNOME | https://extensions.gnome.org/extension/545/hide-top-bar/ |
| Custom Hot Corners Extended | Configura acciones en esquinas activas | https://extensions.gnome.org/extension/1362/custom-hot-corners/ |
| Clipboard Indicator | Historial del portapapeles | https://extensions.gnome.org/extension/779/clipboard-indicator/ |
| Dash to Dock | Dock estilo macOS | https://extensions.gnome.org/extension/307/dash-to-dock/ |


### Notas

- Requiere la integración de navegador instalada
- Después de instalar: Presiona Alt + F2, escribe `r` y presiona Enter para reiniciar GNOME

---

## RECURSOS ADICIONALES

- [Documentación oficial de GNOME](https://help.gnome.org/)
- [Sitio de extensiones GNOME](https://extensions.gnome.org/)
- [Documentación de APT](https://manpages.ubuntu.com/manpages/focal/man8/apt.8.html)