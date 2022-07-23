# 使い方

## これらのファイルを追加する
```
cd ..
touch {.gitignore,.env}
```

```
/.env
```

```
# commons
WORKDIR=app
CONTAINER_PORT=3000
API_PORT=3000
FRONT_PORT=8080

# db
POSTGRES_PASSWORD=password
```

## imageを作成
```
docker-compose build
```

## [api & db]アプリ作成を作成 
```
// いらない！
docker-compose run --rm api rails new . -f -B -d postgresql --api

// gemfile反映させる
docker-compose build api

// db作成
 docker-compose run --rm api rails db:create

// 起動 http://localhost:3000 でアクセス可
 docker-compose up api
```

## [front]アプリ作成を作成 
```
// 削除する
rm -rf front

mkdir front

// 記事を参考に作り直す
touch front/Dockerfile

// node_modules がないので、これで作り直す ※時間かかるけどok
docker-compose run --rm front yarn create nuxt-app --overwrite-dir

// 立ち上がる
docker-compose up front
```

### 以下を参考に、初期情報を登録するだけ

https://blog.cloud-acct.com/posts/u-docker-rails-nuxtjs-heroku/#root%E3%83%87%E3%82%A3%E3%83%AC%E3%82%AF%E3%83%88%E3%83%AA%E3%81%AE%E4%BD%9C%E6%A5%AD