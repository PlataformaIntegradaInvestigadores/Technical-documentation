<div style="text-align: center;">
  <h1>Como levantar CENTINELA</h1>
</div>

### Acceso al servidor

Para dar seguimiento o verificar el estado de la aplicación, se debe acceder por SSH a la IP de la máquina virtual `172.28.36.130`. Se recomienda utilizar herramientas como **PuTTY** o **MobaXterm**.

Una vez conectado, cambie al directorio `centinela`:

```bash
cd centinela
```

Dentro de la carpeta `centinela` se encuentran la aplicación de Angular y los respectivos backends. Cada aplicación se levanta mediante su propio archivo `docker-compose`. Es importante verificar los puertos que utiliza cada servicio:

- **Frontend:** Puerto `8082`
- **API de social_consensus:** Puerto `8000`
- **API del search:** Puerto `8001`

⚠️ **Nota importante:** Tenga mucho cuidado con los volúmenes, ya que contienen toda la información de las bases de datos.

### Comandos Docker

### Verificación de contenedores e imágenes:

```bash
# Ver los contenedores levantados
docker ps

# Ver las imágenes existentes
docker image ls

# Eliminar una imagen
docker image rm <id_de_la_imagen>
```

### Manejo de contenedores:

```bash
# Levantar aplicación
docker compose up -d

# Levantar aplicación con nueva imagen
docker compose up --build -d

# Bajar aplicación
docker compose down
```

Al levantar una aplicación con la opción `--build`, se genera una nueva imagen.

### Bases de datos

Investigue cómo conectarse a las bases de datos dentro de los contenedores para extraer información si es necesario. Asegúrese de respetar las configuraciones de los volúmenes para evitar pérdidas de datos.

### Configuración de Nginx

Además de Docker, la máquina virtual tiene instalado **Nginx**, un potente software de código abierto que actúa como servidor web, proxy inverso y balanceador de carga. Es ampliamente utilizado por su alto rendimiento, escalabilidad y bajo consumo de recursos.

### Comandos de Nginx:

```bash
# Verificar estado
systemctl status nginx

# Acceso a los logs
cat /var/log/nginx/error.log  # Errores
cat /var/log/nginx/access.log # Solicitudes HTTP

# Detener
systemctl stop nginx

# Levantar
systemctl start nginx

# Reiniciar
systemctl restart nginx
```

La configuración de Nginx se encuentra en el directorio `/etc/nginx/`. Es recomendable realizar un respaldo de los archivos antes de realizar cambios en la configuración.