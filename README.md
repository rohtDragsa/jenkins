# Jenkins

[Jenkins Download](https://www.jenkins.io/download/)
[Jenkins docs](https://www.jenkins.io/doc/book/)

#### Docker

```bash
docker pull jenkins/jenkins
docker run -p 8080:8080 -p 50000:50000 -v ~/jenkins-data-docker:/var/jenkins_home jenkins/jenkins
```

#### ESXI VM CentOs8

```bash
sudo dnf install java-1.8.0-openjdk-devel
sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
sudo yum install jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp
sudo firewall-cmd --reload
```

### Reverse Proxy

https://www.jenkins.io/doc/book/system-administration/reverse-proxy-configuration-nginx/

- setup/install epel-release && nginx
- update firewall with prot 80 and
- `setsebool -P httpd_can_network_connect 1`
- remove server entry from /etc/nginx/nginx.conf
- create new file /etc/nginx/conf.d/jenkins.conf with the content below

```bash

upstream jenkins {
    server 127.0.0.1:8080;
}

server {
    listen       80 default_server;
    listen       [::]:80 default_server;
    server_name  jenkins-main;

    access_log /var/log/nginx/jenkins.access.log;
    error_log  /var/log/nginx/jenkis.error.log;

    proxy_buffers 16 64k;
    proxy_buffer_size 128k;


    location / {
        proxy_pass http://jenkins;
        proxy_next_upstream error timeout invalid_header http_500 http_502 http_503 http_504;
        proxy_redirect off;

        proxy_set_header        Host                    $host;
        proxy_set_header        X-Real-IP               $remote_addr;
        proxy_set_header        X-Forwarded-For         $proxy_add_x_forwarded_for;
        proxy_set_header        X-Forwarded-Proto       https;
    }
}
```

#### Credentials

- on the jenkins machine create ssh key
- update github with pub ssh key
- in jenkins go to credentials and add github username and private key generated on the jenkins machine

#### Local setup

- Jenkins on the VM
- user ngrok
- install github integration plugin in jenkins
- add webhook to the repo `http://xxxx.ngrok.io/github-webhook/`


### Pipelines