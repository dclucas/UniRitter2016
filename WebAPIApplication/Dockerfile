#fixme: using 'latest' is a really bad idea...
FROM microsoft/dotnet:onbuild

RUN mkdir /app
COPY project.lock.json /app
WORKDIR /app
RUN dotnet restore
COPY . /app
RUN dotnet build

ARG CONTAINER_PORT=5000
ARG SERVER_URLS=http://*:$CONTAINER_PORT
ENV SERVER.URLS $SERVER_URLS
EXPOSE $CONTAINER_PORT

ENTRYPOINT ["dotnet", "run"]

#ENTRYPOINT ["dnx", "-p", "project.json", "Microsoft.AspNet.Server.Kestrel", "--server.urls", "http://0.0.0.0:5000"]
#FROM microsoft/aspnet:1.0.0-rc1-update1
#COPY project.json /app/
#WORKDIR /app
#RUN ["dnu", "restore"]
#COPY . /app

#ARG CONTAINER_PORT=5000
#ARG SERVER_URLS=http://*:$CONTAINER_PORT
#ENV SERVER.URLS $SERVER_URLS
#EXPOSE $CONTAINER_PORT

#ENTRYPOINT ["dnx", "-p", "project.json", "web"]