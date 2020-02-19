# laravel_docker_base
Create a laravel app container with nginx, php72-fpm, memcached, redis and mysql

- Step 1: move to source code folder and run composer:

docker run --rm -v $(pwd):/app composer install

- Step 2: copy env file:

cp .env.example .env

- Step 3: Start app:   

docker-compose up -d

- Step 4: update env file:

docker-compose exec app nano .env

and add this rows below:

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laraveluser
DB_PASSWORD=your_laravel_db_password

- Step 5: set application key:

docker-compose exec app php artisan key:generate

- Step 6: remove cache:

docker-compose exec app php artisan config:cache

Go to check:  http://localhost:8088
