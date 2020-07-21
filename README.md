# README

## rails docker 運用

### 設定ファイル
docker-compose.yml
Dockerfile
Gemfile
Gemfile.lock

---
### コマンド
// Dockerfile, docker-compose.yml の修正
- volumes: /myapp -> app名
- Dockerfile 同様
// image 構築、コンテナの起動
- docker-compose run web rails new . --force --database=mysql --skip-bundle

// db の設定 を修正
- database.yml
  - defalut: &default
    - password: password
    - host: db
// build して コンテナ内に COPY
- docker-compose build
- docker-compose run web rails db:create
- docker-compose run web rails db:migrate
- docker-compose up -d

// Gemfile 内の ruby versionを 2.5.8 -> 2.5.1 に修正
- v Gemfile
- bundle install
