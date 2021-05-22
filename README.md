```bash
/opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P password
```

```
CREATE DATABASE database_name
GO
```


/opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P Your_password123 -Q "CREATE DATABASE testdb;"



## Package
https://www.nuget.org/packages

Add a package to .csproj file
Example:
```
<PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="5.0.6" />
```

Cmd:
```
dotnet list package
# Install
dotnet pack
dotnet restore
```

Dockerfile for production
https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/docker/building-net-docker-images?view=aspnetcore-5.0#the-dockerfile

## Setup https for Docker
Run command App in Docker
```
dotnet dev-certs https -ep aspnetapp.pfx -p mypassword123
```
Copy aspnetapp.pfx to /https

Add to Environment file
```
ASPNETCORE_ENVIRONMENT=Development
ASPNETCORE_HTTPS_PORT=5001
ASPNETCORE_URLS=https://+:5001;http://+:5000
DOTNET_USE_POLLING_FILE_WATCHER=1
ASPNETCORE_Kestrel__Certificates__Default__Password=mypassword123
ASPNETCORE_Kestrel__Certificates__Default__Path=/https/aspnetapp.pfx
```

```
dotnet dev-certs https --clean
dotnet dev-certs https --trust
```