FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /app

COPY slowapp.csproj ./slowapp.csproj
RUN dotnet restore ./slowapp.csproj

COPY . ./
RUN dotnet publish ./slowapp.csproj -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS run-env

WORKDIR /app
COPY --from=build-env /app/out .

ENTRYPOINT ["dotnet", "slowapp.dll"]
