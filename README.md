# Docker MariaDB Setup

Este proyecto configura un contenedor Docker para MariaDB con un usuario adicional, acceso desde cualquier host y un script de inicialización.

## Requisitos

- Docker
- Docker Compose

## Uso

1. Clona este repositorio:

    ```sh
    git clone https://github.com/NicodeV2/docker-mariadb.git
    cd docker-mariadb
    ```

2. Asegúrate de que el archivo `init.sql` esté dentro de la carpeta `scripts`:

    ```sh
    scripts/init.sql
    ```

3. Levanta el contenedor usando Docker Compose:

    ```sh
    docker-compose up -d
    ```

4. Verifica que el contenedor esté corriendo:

    ```sh
    docker ps
    ```

## Configuración

El archivo `docker-compose.yml` está configurado con las siguientes credenciales y opciones:

- **Root User**:
  - Usuario: `root`
  - Contraseña: `rootTest`
- **Database**: `test`
- **Additional User**:
  - Usuario: `userTest`
  - Contraseña: `passwordTest`
- **Puertos**:
  - `3306:3306`

El script `init.sql` se encuentra en la carpeta `scripts` y se ejecutará al iniciar el contenedor. Aquí hay un ejemplo de lo que podría contener:

```sql
-- init.sql

CREATE TABLE IF NOT EXISTS users (
    id_users INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(25) NOT NULL,
    email VARCHAR(50) NOT NULL,
    password VARCHAR(255) NOT NULL
);

INSERT INTO users (username, email, password) VALUES
('user1', 'user1@email.com', 'password1'),
('user2', 'user2@email.com', 'password2');


