Packagist in Docker 
===================

    docker-compose up -d
    docker exec -it packagist_fpm_1 app/console d:d:c && app/console d:s:c
    docker exec -it packagist_fpm_1 app/console packagist:index --all --env=prod
    docker exec -it packagist_fpm_1 app/console packagist:stats:compile
    
    