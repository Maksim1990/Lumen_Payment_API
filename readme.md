**HOT TO INSTALL APP**
--
     
* *Copy ``.env`` environment config file and set all required settings in it:*

    cp .env.dist .env
     
* *Start app and build required Docker containers:*

        docker-compose up -d
      
* *Install all composer dependencies:*

        docker exec -it payment_api_app composer install
            
* *Run all required migrations:*

        docker exec -it payment_api_app php artisan migrate
  
      
* *Change permission for 'storage' folder:*
    
        docker exec -it payment_api_app  chmod +x ./services/docker/set_storage_read_write_permissions.sh
        docker exec -it payment_api_app  ./services/docker/set_storage_read_write_permissions.sh

App is available on ``8303`` port
--
    http://127.0.0.1:8303
