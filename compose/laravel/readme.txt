Laravel with mysql, nginx and php


$git clone https://github.com/laravel/laravel.git laravel-app


$cd ~/laravel-app

$docker run --rm -v $(pwd):/app composer install

$sudo chown -R $USER:$USER ~/laravel-app


setup Dockerfile, docker-compose.yml, php - local.ini, nginx - app.conf, mysql - my.cnf file's and laravel .env database config info

run 

$docker-compose up

login into app

$docker-compose exec app bash

$docker-compose exec app php artisan key:generate

$docker-compose exec app php artisan config:cache

login into db bash

$docker-compose exec db bash

$mysql -u root -p

$mysql>GRANT ALL ON laravel.* TO 'laraveluser'@'%' IDENTIFIED BY 'your_laravel_db_password';

$mysql>FLUSH PRIVILEGES;

exit

$docker-compose exec app php artisan migrate

make sure mysql internal port is 3306 and used the same in .env - DB_PORT, DB_HOST should be container_name/service name of mysql container

