# Docker Study #01

---

# Overview

- 軽量な仮想化環境を実現するためのツール
- OSやアプリケーションを設定したものを丸ごと実行イメージとして保存できる
- Dockerが導入されている別のマシンにそのまま持っていくことができる
- 「Build onece, run anywhere」と呼ばれ、環境の違いを意識することなくアプリケーションを導入できる

---

![alt](assets/docker_vs_hv.png)

---

# Install

## Docker For Mac (brew cask)

```
$ brew cask install docker
```

## Docker For Mac (dmg)

https://www.docker.com/docker-mac

## GUI Settings

```
$ open /Applications/Docker.app
```

画面に沿って設定する。

---

# Example

https://github.com/shin1x1/laravel-ddd-sample

---

## 環境構築

```
git clone https://github.com/shin1x1/laravel-ddd-sample
cd laravel-ddd-sample

docker-compose up -d
docker-compose run web composer install
cp -a .env.example .env
docker-compose run web php artisan key:generate
```

---?code=docker-compose.yml

---

## マイグレーション

```
docker-compose run web php artisan migrate
docker-compose run web php artisan db:seed
```

---

## ブラウザ表示

```
open http://localhost:8000
```

---

## PostgreSQLログイン

```
docker-compose run db psql --version
docker-compose exec db psql -U app app
```

---

## コンテナ停止

```
docker-compose down
```

---

## コンテナをすべて削除する

```
docker rm $(docker ps -aq)
```
