# How to use

#### Create basic auth for web
1. Goto [bcrypt](https://passwordhashing.com/BCrypt) to generate password

2. paste password to elasticsearch/config/sg/sg_internal_users.yml
3. Add more user (if needed)
4. If you change password for logstash or kibanaserver, you must also change it in fluentd/conf/fluent.conf and kibana/config/kibana.yml

#### Jenkins
If you have jenkins_home data do copy it to ./jenkins/jenkins_home

```
# if you want just run only jenkins
# generate id_rsa key
cd jenkins
ssh-keygen -t rsa -b 4096 -C "your-email"
# when asked for path just type .

docker-compose -f docker-compose.jenkins.yml build
docker-compose up -f docker-compose.jenkins.yml
```

#### Run docker
cd < project-folder >

```
cp .env.example .env
nano .env # modify .env

# create elastic data folder
mkdir elasticdata
sudo chown 1000:1000 elasticdata
docker-compose build
docker-compose up -d

# wait a second then
docker-compose exec -T elasticsearch bin/init_sg.sh

# goto web localhost:5601
```

# AWS ECS
- ssh to ecs
```
mkdir -p /usr/share/elasticsearch
cd /usr/share/elasticsearch
mkdir data
mkdir config
cd config
vi elasticsearch.yml
# copy content to this file
# save & quit
```
- Create interal ALB
- Create target group
- Choose this ALB when create a service

*Note*

sudo chown 1000:1000 elasticdata # You must do it, check doc [here](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)
