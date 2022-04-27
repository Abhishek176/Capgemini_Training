```
docker compose up  -d : To create and run the container
docker compose down : To delete the containers
docker compose  -f test.yml up  -d : To create and run the container if the docker compose file name is different
docker compose ps : To check the containers started by docker compose
docker compose stop : To stop the container started by docker compose
docker compose kill : To kill the container started by docker compose
docker compose start : To start the container stopped by docker compose
docker compose restart : To restart the container stopped by docker compose
docker compose pause : To pause the container started by docker compose
docker compose unpause : To unpause the container started by docker compose
docker compose rm : To remove the container started by docker compose
docker compose exec <service_name> <command> : To run command inside the container
docker compose logs  -f : To check the logs of the container
```