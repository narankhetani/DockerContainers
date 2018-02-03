FROM nginx

COPY supervisor.conf /etc/supervisor/docker.conf
COPY ansible.cfg /var/www/ara/ansible.cfg
COPY ara.nginx /etc/nginx/conf.d/ara.conf
COPY ara.uwsgi /etc/uwsgi/apps-available/ara.ini

ENV ANSIBLE_CONFIG /var/www/ara/ansible.cfg

EXPOSE 80
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/docker.conf"]

RUN apt-get update && apt-get upgrade -y \
  && apt-get -y install supervisor \
  && apt-get -y install gcc python-dev libffi-dev libssl-dev \
  && apt-get -y install python-pip libxml2-dev libxslt1-dev \
  && pip install ansible tox uwsgi ara pymysql psycopg2 \
  && cp /usr/local/bin/ara-wsgi /var/www/ara/wsgi.py \
  && chown -R nginx:nginx /var/www/ara \
  && mkdir /var/log/uwsgi \
  && chmod 777 /var/log/uwsgi

RUN rm -f /etc/nginx/conf.d/default.conf
RUN /etc/init.d/nginx restart
RUN /etc/init.d/supervisor restart