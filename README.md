# IFMS Pension Project with Angular 18 and .Net 8.0 Core WebAPI

## Setup project

copy environment settings

```sh
cp .env.docker .env
```

Start docker containers

```sh
docker-compose up -d
```

Set connection string

```sh
docker-compose exec dotnet dotnet user-secrets set ConnectionStrings:DefaultConnection "Host=postgres;Database=ifmswb;Username=ifmswb;Password=ifmswb@1234"
```

Create database tables and seed data

```sh
docker-compose exec dotnet dotnet ef database update
```

Angular Frontend `http://ifmswb.test`

.Net Core Backend API `http://api.ifmswb.test/swagger/index.html`

Enjoy!!!







### Install .Net Tools EF(Entity Framework) Core

```sh
docker-compose exec dotnet dotnet tool update --global dotnet-ef
```

### [Setup ConnectionString Storage](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-8.0)

Only for new project run the following

```sh
docker-compose exec dotnet dotnet add package Microsoft.Extensions.Configuration
docker-compose exec dotnet dotnet add package Microsoft.Extensions.Configuration.UserSecrets
docker-compose exec dotnet dotnet user-secrets init
```

Setup connection string for existing project

```sh
docker-compose exec dotnet dotnet user-secrets set ConnectionStrings:DefaultConnection "Host=postgres;Database=ifmswb;Username=ifmswb;Password=ifmswb@1234"
```

Replace the values in the connection string as per your local environment setup


### Generate Migration Scafolds for new project

```sh
docker-compose exec dotnet dotnet ef migrations add InitialSchema
```
### Create database tables and seed data

```sh
docker-compose exec dotnet dotnet ef database update
```
