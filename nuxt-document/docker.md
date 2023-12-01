# Nuxt Docker構築手順

ディレクトリ構成

``` sh
.
Dockerfile
docker-compose.yml


```

``` docker-compose.yml
version: '3.9'

services:
  app:
    container_name: app
    build: .
    volumes:
      - ./front:/app
    ports:
      - "80:3000"
    tty: true
    environment:
      - HOST=0.0.0.0
      - port=80
      - CHOKIDAR_USEPOLLING=true
    command: sh -c "npm install && npm run dev"
    # command: sh -c "npm install && npx nodemon"
    # nodemonをプロジェクト/front内におくこと
    #永続化コマンド
```

``` Dockerfile
FROM node:18-slim
WORKDIR /app
RUN apt-get update \
    && apt-get install -y \
    git \
    vim
```

## nuxtをインストールする

コンテナ起動&コンテナ内に入る
`docker-compose up -d`
`docker-compose exec app bash`

npxを使って初期のNuxtを入れて環境を作る
`npx nuxi init . --force`
`npm install`
`npm run dev`

### 追加DL

`npm install sass`

## 自動コンパイル

`/front/nodemon.json`

``` json
{
  "watch": ["."],
  "ext": "js,json,ts",
  "ignore": ["node_modules"],
  "exec": "npm run dev"
}
```

[NuxtのDocker構築](https://qiita.com/A-Kira/items/5ce3e1bff34e179ebbc2)


