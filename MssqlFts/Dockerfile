FROM mcr.microsoft.com/mssql/server:2022-CU11-ubuntu-22.04
USER root

RUN apt-get update
RUN apt-get install -yq gnupg gnupg2 gnupg1 curl apt-transport-https

RUN curl https://packages.microsoft.com/keys/microsoft.asc -o /var/opt/mssql/ms-key.cer
RUN apt-key add /var/opt/mssql/ms-key.cer
RUN curl https://packages.microsoft.com/config/ubuntu/22.04/mssql-server-2022.list -o /etc/apt/sources.list.d/mssql-server-2022.list
RUN apt-get update

RUN apt-get install -y mssql-server-fts

RUN apt-get clean
RUN rm -rf /var/lib/apt/lists