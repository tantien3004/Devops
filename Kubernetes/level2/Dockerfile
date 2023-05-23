FROM nginx:latest
RUN apt-get update && apt-get install -y unzip
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY carserv.zip /usr/share/nginx/html
RUN unzip /usr/share/nginx/html/carserv.zip -d /usr/share/nginx/html/
