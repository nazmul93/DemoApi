# NuGet restore
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /build
COPY . .
RUN dotnet restore
RUN dotnet publish -c Release -o /app

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS runtime
WORKDIR /app
COPY --from=build /app .
#ENTRYPOINT ["dotnet", "DemoApi.dll"]
# heroku uses the following
CMD ASPNETCORE_URLS=http://*:$PORT dotnet DemoApi.dll