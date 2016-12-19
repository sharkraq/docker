logicaldoc-db
============

Example usage: 
     `docker run -dit --name logicaldoc-db -p 3306 \
-e MYSQL_ROOT_PASSWORD=Silversky5 -e MYSQL_USER=logicaldoc \
-e MYSQL_PASSWORD=Silversky5 -e MYSQL_DATABASE=logicaldoc \
-d -v /data/logicaldoc-db/mysql:/var/lib/mysql:rw per5-dockerregistry.silversky.com:5443/logicaldoc-db`

Environment variables
---------------------

 - `MYSQL_ROOT_PASSWORD`: The password for the root user. Defaults to a blank password
 - `MYSQL_DATABASE`: A database to automatically create. If not provided, does not create a database.
 - `MYSQL_USER`: A user to create that has access to the database specified by `MYSQL_DATABASE`.
 - `MYSQL_PASSWORD`: The password for `MYSQL_USER`. Defaults to a blank password.
 
 
 
 
 logicaldoc-app
 ============
Get ip of db container:
docker inspect container-id


docker run -itd --restart=always -e MYSQL_SERVER=logicaldoc-db -p 8080:8080 -v \
/data/logicaldoc-app/LogicalDOC-Community:/LogicalDOC-Community:rw --name logicaldoc-app \
--link logicaldoc-db:mysql per5-dockerregistry.silversky.com:5443/logicaldoc-app

After the app run finishes you will need to run a command to start container.

docker start logicaldoc-app
