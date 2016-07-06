# MySQL

![](https://upload.wikimedia.org/wikipedia/en/6/62/MySQL.svg)

MySQL is an open-source relational database management system (RDBMS); in July 2013, it was the world's second most widely used RDBMS, and the most widely used open-source client–server model RDBMS. It is named after co-founder Michael Widenius's daughter, My. The SQL abbreviation stands for Structured Query Language. The MySQL development project has made its source code available under the terms of the GNU General Public License, as well as under a variety of proprietary agreements. MySQL was owned and sponsored by a single for-profit firm, the Swedish company MySQL AB, now owned by Oracle Corporation. For proprietary use, several paid editions are available, and offer additional functionality.

# MySQL: Docker

### Docker Run

```
docker pull mysql
docker run -d \
  -p 3306:3306 \
  --env MYSQL_ROOT_PASSWORD=docker \
  --env MYSQL_DATABASE=docker \
  --env MYSQL_USER=docker \
  --env MYSQL_PASSWORD=docker \
  mysql
```

Note: On Windows, view your `0.0.0.0` IP by running below command line (or you can turn on Kitematic to view ip)

### Docker Compoose

**Step 1**: Clone Docker Project

```
git clone https://github.com/magizbox/docker-mysql.git
mv docker-mysql mysql
```

**Step 2**: Docker Compose

```
version: "2"

services:
 mysql:
  build: ./mysql/.
  ports:
   - 3306:3306
  environment:
   - MYSQL_ROOT_PASSWORD=docker
   - MYSQL_DATABASE=docker
   - MYSQL_USER=docker
   - MYSQL_PASSWORD=docker
  volumes:
   - ./data/mysql:/var/lib/mysql
```

### Docker Folder

```
mysql/
├── config
│   └── my.cnf
└── Dockerfile
```

### Verify

```
docker-machine ls
NAME      ACTIVE   DRIVER       STATE     URL                         SWARM
default   *        virtualbox   Running   tcp://192.168.99.100:2376
```

You can add phpmyadmin to see mysql works

```
 phpmyadmin:
  image: phpmyadmin/phpmyadmin
  links:
   - mysql
  environment:
   - PMA_ARBITRARY=1
  ports:
   - 80:80
```

See it works

1. Go to localhost
2. Login with Server=mysql, Username=docker, Password=docker
