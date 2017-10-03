Install docker: https://docs.docker.com/docker-for-windows/install/#download-docker-for-windows

https://github.com/dotnet/dotnet-docker

- `dotnet new sln --name docker.netcore`
- `dotnet new console --name docker.netcore`
- `dotnet sln add docker.netcore.csproj`
- edit the Progam.cs so that it does something you can see (to verify that it's working)
- create a dockerfile with the content below
- `dotnet restore`
- `dotnet publish -c Release -o out`
- `docker build -t docker.netcore .`
- `docker run -it --rm docker.netcore`

DockerFile
```
FROM microsoft/dotnet:runtime
WORKDIR /docker.netcore
COPY out .
ENTRYPOINT ["dotnet", "docker.netcore.dll"]
```
