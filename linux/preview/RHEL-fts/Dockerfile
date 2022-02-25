# mssql-server-agent-fts-ha-tools

# Base OS layer: Red Hat 8 ubi

FROM registry.access.redhat.com/ubi8

USER root

# Install prerequistes since it is needed to get repo config for SQL server

RUN yum -y update

RUN curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/mssql-server-2019.repo

RUN curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/8/prod.repo

RUN yum install -y mssql-server

