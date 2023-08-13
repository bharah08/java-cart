[![Build Status](https://travis-ci.org/microservices-demo/carts.svg?branch=master)](https://travis-ci.org/microservices-demo/carts) [![Coverage Status](https://coveralls.io/repos/github/microservices-demo/carts/badge.svg?branch=master)](https://coveralls.io/github/microservices-demo/carts?branch=master)
[![](https://images.microbadger.com/badges/image/weaveworksdemos/cart.svg)](http://microbadger.com/images/weaveworksdemos/cart "Get your own image badge on microbadger.com")
# cart
A microservices-demo service that provides shopping carts for users.

This build is built, tested and released by travis.

# API Spec

Checkout the API Spec [here](http://microservices-demo.github.io/api/index?url=https://raw.githubusercontent.com/microservices-demo/carts/master/api-spec/cart.json)

# Creating a dev environment

Platform : Ubuntu 16.04  

Setup Mongo DB
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list

sudo apt-get update

sudo apt-get install -y mongodb-org

sudo service mongod start

```

Validate mongodb

```
cat /var/log/mongodb/mongod.log

```


Setup Carts App

```
apt-get install -yq openjdk-8-jre-headless openjdk-8-jdk-headless
sudo apt-get install maven -yq

cd carts/

mvn compile
mvn test
mvn -DskipTests package

```

Run Carts App

```
mvn spring-boot:run


or

ls target/
java -jar target/carts.jar

```


# Build


## Java

`mvn -DskipTests package`

## Docker

`GROUP=weaveworksdemos COMMIT=test ./scripts/build.sh`

# Test

`./test/test.sh < python testing file >`. For example: `./test/test.sh unit.py`

# Run

`mvn spring-boot:run`

# Check

`curl http://localhost:8081/health`

# Use

`curl http://localhost:8081`

# Push

`GROUP=weaveworksdemos COMMIT=test ./scripts/push.sh`
