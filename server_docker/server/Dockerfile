

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build 

WORKDIR /server

COPY *.csproj .

RUN dotnet restore 

COPY . . 

RUN dotnet publish -c Release -o /publish 



FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime

WORKDIR /publish

COPY --from=build /publish .

EXPOSE 80

ENTRYPOINT ["dotnet", "Return-It.dll"]
