# FROM microsoft/aspnetcore-build 
# ADD . /src
# WORKDIR /src

# # Copy csproj and restore as distinct layers
# #COPY *.csproj ./
# RUN dotnet restore

# # Copy everything else and build
# #COPY . ./
# RUN dotnet publish -o /app

# # Build runtime image
# #FROM microsoft/aspnetcore
# WORKDIR /app
# #COPY --from=build-env /app/out .
# ENTRYPOINT ["dotnet", "SimpleToAdvance.dll"]

# # The `FROM` instruction specifies the base image. You are
# # extending the `microsoft/aspnet` image.

# FROM microsoft/aspnet

# # The final instruction copies the site you published earlier into the container.
# COPY ./bin/Release/PublishOutput/ /inetpub/wwwroot


##V1 Dockerfile
FROM microsoft/aspnetcore-build:2.0 AS build-env
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o output

# Build runtime image
FROM microsoft/aspnetcore:2.0
WORKDIR /app
COPY --from=build-env /app/output .
ENTRYPOINT ["dotnet", "SimpleToAdvance.dll"]
##End V1 dockerfile