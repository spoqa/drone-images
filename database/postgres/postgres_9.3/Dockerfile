FROM ubuntu:precise
ADD ACCC4CF8.asc /tmp/ACCC4CF8.asc
ADD pgdg.list /etc/apt/sources.list.d/pgdg.list
RUN apt-key add /tmp/ACCC4CF8.asc                                                                        && \
    rm /tmp/ACCC4CF8.asc                                                                                 && \
    apt-get -qq update                                                                                   && \
    LC_ALL=C DEBIAN_FRONTEND=noninteractive apt-get install -y -qq postgresql-9.3 postgresql-contrib-9.3 && \
    mkdir -p /usr/local/pgsql/data                                                                       
ADD pg_hba.conf /etc/postgresql/9.3/main/pg_hba.conf
ADD postgresql.conf /etc/postgresql/9.3/main/postgresql.conf
#ADD server.key /var/lib/postgresql/9.3/main/server.key
#RUN chmod og-rwx /var/lib/postgresql/9.3/main/server.key && chown postgres /var/lib/postgresql/9.3/main/server.key
USER postgres
EXPOSE 5432
ENTRYPOINT ["/usr/lib/postgresql/9.3/bin/postgres", "-D", "/var/lib/postgresql/9.3/main", "-c", "config_file=/etc/postgresql/9.3/main/postgresql.conf", "-c", "listen_addresses=*" ]


#ENTRYPOINT ["/bin/bash", "-c", "whoami && /usr/lib/postgresql/9.3/bin/postgres -D /var/lib/postgresql/9.3/main -c config_file=/etc/postgresql/9.3/main/postgresql.conf -c listen_addresses=*" ]




