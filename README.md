# How to use

#### Create basic auth for web
1. Goto [htpasswd](http://www.htaccesstools.com/htpasswd-generator/) to generate username, password

2. create file in htpasswd folder # the file must be the same with your website (ex: kibana.danghung.top)
3. paste generated htpasswd

#### Jenkins
If you have jenkins_home data do copy it to ./jenkins/jenkins_home

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
```

*Note*

sudo chown 1000:1000 elasticdata # You must do it, check doc [here](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)
