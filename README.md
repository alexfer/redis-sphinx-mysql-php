## Docker Environment

Helps to build Mysql8, PHP7.4, Redis Server & Sphinx search 2.

#### Before start
````
cp .env.dist .env
````
and change your configuration

#### To run & build execute following command:
````
docker-compose up -d --bild 
````
#### After that check the containers are working
````
docker ps
````
#### Build indices in sphinx search engine
````
docker-compose exec sphinx indexer --all --rotate
````
Open file `hosts` & add new line
````
127.0.0.1   example.local www.example.local
````