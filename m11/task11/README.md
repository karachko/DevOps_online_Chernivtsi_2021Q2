# PART1 #
1.I installed EC2-Docker
- I selected EC2 from All services on AWS
- I selected Ubuntu Server 18.04 LTS
- I chose Instant Type t2.micro
- I pressed the button Next
- I pressed the button Next
- I pressed the button Add Tag
- I filled out the fields (key - name, value - Docker)
- I pressed the button Next
- I selected Add Rule and filled out the fields (Type - SSH, Protocol - TCP, Port Range -22,Source -Anywere 0.0.0.0/0, ::/0)
- I pressed the button Launch
- I selected Create key pair
- I entered the Dockerkey and pressed the button Download Key Dockerkey.pem.
- sudo usermod -aG sudo ubuntu
2. I installed Docker on the EC2-Docker
- sudo apt-get update
- sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
- curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
- sudo apt-key fingerprint 0EBFCD88
- sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
- sudo apt-get update
- sudo apt-get install docker-ce docker-ce-cli containerd.io

- I created user student  on the EC2-Docker
    - sudo useradd student
    - sudo passwd student
    - sudo mkdir /home/student
    - sudo chown student:student /home/student

- I added a user to the “docker” group
    - sudo usermod -aG docker student

- su - student
- mkdir dockerfiles
- cd dockerfiles
- touch Dockerfile
- nano Dockerfile

```
FROM ubuntu:16.04
RUN apt-get -y update
RUN apt-get -y install apache2
RUN echo 'Hi there, what is love?' > /var/www/html/index.html
RUN echo 'It is just a song ...' >> /var/www/html/index.html
CMD ["/usr/sbin/apache2ctl", "-DFOREGROUND"]
EXPOSE 80
```
- docker build -t tag .

- docker images  (tag:latest)
- docker run -d -p 9998:80 tag:latest
- docker stop 79880483fa2f04b371cf87f22a07892972630dac39de7ae8572b9affb415b7ab


 


- docker ps -a -q
- docker stop e2d3afb4b1d5
- docker rm e2d3afb4b1d5

## PART 2 ##
- I created a Python Flask app that displays random cat pix
- mkdir flask-app 
- cd flask-app

- nano Dockerfile

```
# our base image
FROM alpine:3.5
# Install python and pip
RUN apk add --update py2-pip
# upgrade pip
RUN pip install --upgrade pip
# install Python modules needed by the Python app
COPY requirements.txt /usr/src/app/
RUN pip install --no-cache-dir -r /usr/src/app/requirements.txt
# copy files required for the app to run
COPY app.py /usr/src/app/
COPY templates/index.html /usr/src/app/templates/
# tell the port number the container should expose
EXPOSE 5000
# run the application
CMD ["python", "/usr/src/app/app.py"]

```
- nano requirements.txt
```
Flask==0.10.1
```

- app.py
```
from flask import Flask, render_template
import random
app = Flask(__name__)

images = [ "https://media.giphy.com/media/jpbnoe3UIa8TU8LM13/giphy.gif",
           "https://media.giphy.com/media/VbnUQpnihPSIgIXuZv/giphy.gif",
           "https://media.giphy.com/media/lJNoBCvQYp7nq/giphy.gif"
]

@app.route('/')
def index():
    url = random.choice(images)
    return render_template('index.html',url=url)

if __name__ == '__main__':
    app.run(host="0.0.0.0")


```

- nano templates/index.html
```
<html>
<head>
<style type="text/css">
body {
background: black;
color: white;
}
div.container {
max-width: 500px;
margin: 100px auto;
border: 20px solid white;
padding: 10px;
text-align: center;
}
h4 {
text-transform: uppercase;
}
</style>
</head>
<body>
<div class="container">
<h4>Cat Gif of the day</h4>
<img src="{{url}}">
<p><small>Courtesy: <a href="http://www.buzzfeed.com/copyranter/the-best-cat-gif-post-in$
</div>
</body>
</html>


```





- docker build -t tag1 .
- docker run -d -p 8889:5000 tag1:latest
- http://54.167.2.109:8889/

- (docker1.jpg)
-  ![docker1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m11/task11/docker1.jpg)
- (cat.jpg)
-  ![cat.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m11/task11/cat.jpg)
