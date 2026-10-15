
# base image
FROM mcr.microsoft.com/dotnet/aspnet:8.0 as base
WORKDIR /app
EXPOSE 8080


#step 1
FROM mcr.microsoft.com/dotnet/sdk:8.0 as build
WORKDIR /src

# retsore layer
COPY "./OurFirstDockerApp.csproj" .
RUN dotnet restore "./OurFirstDockerApp.csproj"

COPY . .
RUN dotnet publish "./OurFirstDockerApp.csproj" -c Release -o /app/publish --no restore

# restore + build + publish


#step 2
FROM base as final
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet","OurFirstDockerApp.dll"]