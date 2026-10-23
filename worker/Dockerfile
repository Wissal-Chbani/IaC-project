# stage 1 
FROM --platform=${BUILDPLATFORM} mcr.microsoft.com/dotnet/sdk:8.0 AS build

ARG TARGETPLATFORM 
ARG BUILDPLATFORM 
ARG TARGETARCH

RUN echo ${BUILDPLATFORM} ${TARGETPLATFORM} ${TARGETARCH}

WORKDIR /source

COPY . .

RUN dotnet restore -a $TARGETARCH && dotnet publish -c release -o /app -a $TARGETARCH --self-contained false --no-restore

# stage 2 
FROM mcr.microsoft.com/dotnet/runtime:8.0

WORKDIR /app

COPY --from=build /app .

CMD ["dotnet", "Worker.dll"]

