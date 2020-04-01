### Running

```
# Running
% docker-compose -f "docker-compose.keycloak-postgres.yml" config
% docker-compose -f "docker-compose.keycloak-postgres.yml" config --volumes 
% docker-compose -f "docker-compose.keycloak-postgres.yml" up -d 
Creating network "keycloak_backend" with driver "bridge"


# Stopping containers and cleaning
% docker-compose down 
```

To see what is currently running:

```
% docker-compose ps 
% docker-compose logs -f keycloak 
```

### Networking in Compose

https://docs.docker.com/compose/networking/

https://runnable.com/docker/docker-compose-networking

https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/

https://devhints.io/docker-compose



### Welcome to Keycloak

Server will startup and on port 9090. 

http://localhost:9090/auth/

### Log in to the Admin Console

Click the Administration Console link on the Welcome page or go directly to the console URL

http://localhost:9090/auth/admin/

```
KEYCLOAK_USER: admin
KEYCLOAK_PASSWORD: Pa55w0rd
```

### Importing a Keycloak Realm at Admin console

Import the JSON file found in above GIT repo (keycloak/config)

https://www.keycloak.org/docs/latest/server_admin/#admin-console-export-import

https://hub.docker.com/r/jboss/keycloak/

Import quickstart-realm.json into your Keycloak. To do that, go to the Keycloak admin console (http://localhost:9090/auth/admin/) and select "Add realm" and then select the JSON file. It creates `Spring-boot-quickstart` realm.

![image-20200326160059971](./image-20200326160059971.png)

It will create realm, clients, roles and users for you (Demo purpose). You can create them manually as you wish.

- [Admin REST API](https://www.keycloak.org/docs/latest/server_development/#admin-rest-api)

```
# Get Token
curl --location --request POST 'http://localhost:9090/auth/realms/spring-boot-quickstart/protocol/openid-connect/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Basic YXBwLWF1dGh6LXJlc3Qtc3ByaW5nYm9vdDpzZWNyZXQ=' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'username=alice' \
--data-urlencode 'password=alice' \
--data-urlencode 'grant_type=password'
```

