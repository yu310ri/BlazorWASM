FROM mcr.microsoft.com/dotnet/core/sdk:latest AS build-env
WORKDIR /app
# 対象プロジェクトをapp配下にコピー
COPY ../WorkSpace/HelloBlazor .
# csprojがある階層で実行
RUN dotnet publish -c Release -o output

FROM nginx:alpine
WORKDIR /var/wwwroot
# 発行されたプロジェクトのwwwrootをnginxの公開フォルダにコピー
COPY --from=build-env /app/output/wwwroot .
COPY nginx.conf /etc/nginx/nginx.conf
