# Go Lang + PostgreSQL + Docker

### Requisitos:
- Docker instalado
- Acceso a Internet (si es necesario exponer la aplicacion)

### Pasos a seguir

1. Copiar los siguientes archivos al proyecto en curso:

- .env
- docker-compose.yml
- Dockerfile

IMPORTANTE: Todas las variables DEBEN estar dentro del archivo .env. En caso de necesitar mas variables, es necesario, agregarlo al .env y al docker-compose.yml

2. Ejecutar `docker-compose build` para buildear las imagenes necesarias de la aplicacion.
3. Levantar el proyecto `docker-compose up`. Si necesitas "silenciar o ocultar" los logs en pantalla, solo necesitas agregar el parametros: `-d`, por ejemplo: `docker-compose up -d`.
4. Para bajar y/o apagar el servicio, se debe ejecutar `docker-compose down`.

### (Opcional) Si necesitas crear un contenedor general

5. Sigue los pasos de este link: https://github.com/danielnaranjo/flutter-web-dockerfile
6. Agregar el siguiente bloque en el archivo `docker-compose.yml`

```
flutter-web:
    image: flutter-web
    volumes:
      # Montamos nuestra web desde fuera en el directorio web del contenedor
      - ./flutter-web/:/var/www/html
    expose:
      - 80
    ports:
      - 80:1200
```

### Notas
La persistencia de la base de datos es externa con `docker volume`

### Comandos utiles
```
docker ps # procesos activos
docker images # listar imagenes
docker volume ls # listar volumenes 
docker network ls # listar red
docker service ls # listar servicios
```
