#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["Test.Workflow/Test.Workflow.csproj", "Test.Workflow/"]
RUN dotnet restore "Test.Workflow/Test.Workflow.csproj"
COPY . .
WORKDIR "/src/Test.Workflow"
RUN dotnet build "Test.Workflow.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Test.Workflow.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Test.Workflow.dll"]