FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY . .
RUN dotnet restore
RUN dotnet publish -c Release -o out --no-restore
RUN ls
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build /app/out .
RUN ls
ENTRYPOINT ["dotnet", "ContosoCrafts.Website.dll"]
EXPOSE 80
