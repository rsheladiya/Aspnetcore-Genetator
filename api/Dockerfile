#Build Stage
FROM microsoft/aspnetcore-build:2.0.2 as build-env

WORKDIR /app

COPY api.csproj .
RUN dotnet restore

COPY . .
RUN dotnet publish -o /publish

# Runtime Image Stage
FROM microsoft/aspnetcore
WORKDIR /publish
COPY --from=build-env /publish .
ENTRYPOINT ["dotnet","api.dll"]