# syntax=docker/dockerfile:1
FROM mcr.microsoft.com/dotnet/sdk:5.0
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./