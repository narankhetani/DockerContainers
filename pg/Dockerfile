#
# example Dockerfile for https://docs.docker.com/examples/postgresql_service/
#
FROM library/postgres:9.3

COPY init.sql /docker-entrypoint-initdb.d/
COPY setup-pg.sh /docker-entrypoint-initdb.d/set-config.sh

USER postgres

RUN /etc/init.d/postgresql start

EXPOSE 5432

# Add VOLUMEs to allow backup of config, logs and databases
# VOLUME  ["/etc/postgresql", "/var/log/postgresql", "/var/lib/postgresql"]

# Set the default command to run when starting the container
# CMD ["/usr/lib/postgresql/9.3/bin/postgres", "-D", "/var/lib/postgresql/9.3/main", "-c", "config_file=/etc/postgresql/9.3/main/postgresql.conf"]