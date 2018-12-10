FROM ubuntu:latest
MAINTAINER dina elmowafy "dina.elmowafy.5@gmail.com"

RUN apt-get update
RUN apt-get install -y python python-pip wget
RUN pip install Flask

COPY . ./nginx_d

WORKDIR /nginx_d

CMD ["python", "app.py"]

