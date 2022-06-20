FROM mcr.microsoft.com/dotnet/runtime:5.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["Personal Challenges/Personal Challenges.csproj", "Personal Challenges/"]
RUN dotnet restore "Personal Challenges/Personal Challenges.csproj"
COPY . .
WORKDIR "/src/Personal Challenges"
RUN dotnet build "Personal Challenges.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Personal Challenges.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Personal Challenges.dll"]
