# mssql-server-agent-fts-ha-tools

# Base OS layer: Red Hat 8 ubi

FROM mcr.microsoft.com/mssql/rhel/server:2019-latest

USER root

# Install prerequistes since it is needed to get repo config for SQL server

RUN dnf -y update

# RUN yum install -y sudo

# RUN curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/mssql-server-2019.repo

# RUN curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/8/prod.repo

# RUN useradd -M -s /bin/bash -u 10001 -g 0 mssql

# RUN mkdir -p -m 770 /var/opt/mssql && chgrp -R 0 /var/opt/mssql

# RUN yum install -y mssql-server

# # RUN yum install -y mssql-server-fts

# RUN ACCEPT_EULA=Y yum install -y msodbcsql18

# RUN ACCEPT_EULA=Y yum install -y mssql-tools18 

# RUN yum install -y unixODBC-devel

# ENV PATH=${PATH}:/opt/mssql/bin:/opt/mssql-tools18/bin

# RUN mkdir -p /var/opt/mssql/data

# RUN chmod -R g=u /var/opt/mssql /etc/passwd

# COPY uid_entrypoint /opt/mssql-tools18/bin

# RUN chmod 755 /opt/mssql-tools18/bin/uid_entrypoint

RUN yum clean all


# # Grant sql the permissions to connect to ports <1024 as a non-root user
# #
# RUN setcap 'cap_net_bind_service+ep' /opt/mssql/bin/sqlservr

# # Add an ldconfig file because setcap causes the os to remove LD_LIBRARY_PATH
# # and other env variables that control dynamic linking
# #
# RUN mkdir -p /etc/ld.so.conf.d && touch /etc/ld.so.conf.d/mssql.conf
# RUN echo -e "# mssql libs\n/opt/mssql/lib" >> /etc/ld.so.conf.d/mssql.conf
# RUN ldconfig

# USER mssql

# # Default SQL Server TCP/Port

# EXPOSE 1433

# VOLUME /var/opt/mssql/data

# ### user name recognition at runtime w/ an arbitrary uid - for OpenShift deployments

# ENTRYPOINT [ "uid_entrypoint" ]

# CMD /opt/mssql/bin/sqlservr
