```markdown
# ⚙️ Tienda de Alimentos para Perritos - Backend

Este repositorio contiene la API REST y la lógica de negocio de la aplicación. Es el encargado de recibir las peticiones del Frontend, procesarlas y gestionar la comunicación con la base de datos MySQL.

## 🏗️ Arquitectura y Seguridad
Por diseño de seguridad, este servicio está desplegado en una instancia EC2 dentro de una **subred privada**. No es accesible desde el internet público. Solo recibe tráfico interno desde el Frontend en el puerto `3001` y se comunica con la Base de Datos a través de la red local de AWS (VPC).

## 🔌 Variables de Entorno
Para que el contenedor pueda conectarse a la base de datos, se le deben pasar los siguientes parámetros en tiempo de ejecución:
* `DB_HOST`: Dirección IP privada de la máquina de Base de Datos.
* `DB_USER`: Usuario de la BD.
* `DB_PASSWORD`: Contraseña de la BD.
* `DB_NAME`: Nombre de la base de datos.

## 🚀 Comando de Despliegue (Docker)
El servicio se levanta inyectando las variables de entorno directamente en el comando `docker run`:

```bash
sudo docker run -d -p 3001:3001 \
  -e DB_HOST=<IP_PRIVADA_DB> \
  -e DB_USER=alumno \
  -e DB_PASSWORD=alumno123 \
  -e DB_NAME=tienda_perritos \
  --name contenedor_backend backend
