# Prueba Laravel 9
+ [URL del curso en Udemy](#)
+ [URL del repositorio en GitHub](https://github.com/petrix12/pruebalaravel2022.git)


## Antes de iniciar:
1. Crear proyecto en la página de [GitHub](https://github.com) con el nombre: **pruebalaravel2022**.
    + **Description**: Proyecto de Laravel 9 para realizar pruebas.
    + **Public**.
2. En la ubicación raíz del proyecto en la terminal de la máquina local:
    + $ git init
    + $ git add .
    + $ git commit -m "Proyecto Inicial"
    + $ git branch -M main
    + $ git remote add origin https://github.com/petrix12/pruebalaravel2022.git
    + $ git push -u origin main


## Creación del proyecto
1. Ejecutar:
    + $ laravel new pruebalaravel2022
    + $ composer require laravel/ui
    + $ php artisan ui bootstrap --auth
    + $ npm install
    + $ npm run dev
2. Crear base de datos **pruebalaravel9** en MySQL.
3. Ejecutar migraciones:
    + $ php artisan migrate
4. Subir a GitHub:
    + $ git add .
    + $ git commit -m "Sistema de autenticación"
    + $ git push -u origin main


## Deploy en DigitalOcean
1. Ir a [DigitalOcean](https://cloud.digitalocean.com/login)
2. Click en **Create > App**.
3. Seleccionar el repositorio GitHub: **pruebalaravel2022**.
4. Seleccionar la rama **main** y clickear en **Autodeploy** y click en **Next**.
5. Ajustar datos del formulario:
    + Type: Web Services
    + Environment Variables:
        + APP_ENV=production
        + APP_DEBUG=false
        + APP_KEY=base64:WOUjUbU6cQ8foyIL/8ssOpFgLmG7WxfBi/xSXJ0O5kg=
    + Build Command: 
        + composer install --no-dev --no-interaction --prefer-dist --optimize-autoloader
        + php artisan optimize
    + Run Command: heroku-php-apache2 public/
    + HTTP Port: 8080
6. Click en **Add a Database**.
    + Choose Name: db
    + Click en **Add Database**.
7. Click en **Next**.
8. Rellenar formulario:
    + Name: pruebalaravel-2022
    + Region: Seleccionar la más cercana (normalmente es la que viene por defecto)
9. Click en **Next**.
10. Seleccionar plan, RAM y CPU y click en **Launch Basic App**.
11. Para obtener las credenciales de la base de datos:
    + Ir a la pestaña **Overview** y seleccionar la base de datos.
        ```
        host     : app-9320fe88-1981-488b-9b89-a1a00c05e077-do-user-10795830-0.b.db.ondigitalocean.com
        port     : 25060
        username : db
        password : **********
        database : db
        sslmode  : require
        ```
12. Para agregar las credenciales de la base de datos como variables de entorno:
    + Ir a la pestaña **Overview** y seleccionar la apliciación.
    + Environment Variables:
        + DB_CONNECTION=pgsql
        + DB_HOST=app-9320fe88-1981-488b-9b89-a1a00c05e077-do-user-10795830-0.b.db.ondigitalocean.com
        + DB_PORT=25060
        + DB_DATABASE=db
        + DB_USERNAME=db
        + DB_PASSWORD=**********
    + Click en **Save**. (Esperar a que se ejeucte el deploy)
13. Para ejecutar las migraciones ir a la pestaña **Console**:
    + $ php artisan migrate
14. Ir a **Settings**, seleccionar el proyecto y agregar las siguientes intrucciones en **Commands > Build Command**:
    + php artisan storage:link
    + php artisan migrate --force
    + npm install
    + npm run prod
15. Para el almacenamiento masivo se recomienda usar **Sapces Object Storage** de DigitalOcean o Amazon S3.
15. Referencias:
    + https://aprendible.com/series/aprende-laravel-intermedio/lecciones/como-publicar-una-aplicacion-de-laravel-en-digital-ocean-app-platform
    + https://programacionymas.com/blog/hacer-deploy-app-laravel-digital-ocean



