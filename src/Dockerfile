FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src

ENV ASPNETCORE_ENVIRONMENT Production

COPY ./DemoApp .

RUN dotnet restore
RUN dotnet build -c Release -o /app/build
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80

COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "DemoApp.dll"]
