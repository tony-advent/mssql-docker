# mssql-server-agent-fts-ha-tools

# Base OS layer: Red Hat 8 ubi

FROM registry.access.redhat.com/ubi8

LABEL name="microsoft/mssql-server-linux" \
      vendor="Microsoft" \
      run='docker run --name ${name} \
         -e ACCEPT_EULA=Y \
         -e MSSQL_SA_PASSWORD=yourStrong@Password \
         -p 1433:1433 \
         -d ${IMAGE}' \
      io.openshift.description="MS SQL Server" \
      io.openshift.display-name="MS SQL Server"

USER root

# Install prerequistes since it is needed to get repo config for SQL server

RUN yum -y update

RUN curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/mssql-server-2019.repo

RUN curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/8/prod.repo

RUN yum install -y mssql-server

# RUN yum install -y mssql-server-fts

RUN ACCEPT_EULA=Y yum install -y msodbcsql18

RUN ACCEPT_EULA=Y yum install -y mssql-tools18 

RUN yum install -y unixODBC-devel

ENV PATH=${PATH}:/opt/mssql/bin:/opt/mssql-tools18/bin

RUN mkdir -p /var/opt/mssql/data

RUN chmod -R g=u /var/opt/mssql /etc/passwd

COPY uid_entrypoint /opt/mssql-tools18/bin

RUN chmod 755 /opt/mssql-tools18/bin/uid_entrypoint

RUN yum clean all

USER 10001

# Default SQL Server TCP/Port

EXPOSE 1433

VOLUME /var/opt/mssql/data

### user name recognition at runtime w/ an arbitrary uid - for OpenShift deployments

ENTRYPOINT [ "uid_entrypoint" ]

CMD /opt/mssql/bin/sqlservr
