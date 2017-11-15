# wp dev env on docker

- WordPress の開発環境をDockerでこうちくする。

- docker-composeでMySQLとPHP(Apache)のコンテナを作成する。

- MySQLとPHP(Apache)の設定を別々に管理できるようになったいいなと考え、別々のコンテナにした。

- PHPのコンテナは公式そのままではなく、pdo_mysql を追加している。
    - 加工しているため、このリポジトリにそのDockerfileを含める。
	
- MySQLのコンテナは公式のものをそのまま使用しています。


## 詳しくはDockerのドキュメント見てください

*docker-compose.yml*のある階層で
```
$> docker-compose up -d
```

でコンテナとボリュームが作成され、
1. MySQLコンテナには
    - *wordpress*というデータベースが作成される
    - *wpuser*というMySQLユーザーが*wppass*というパスワードで作成される
    - confディレクトリがマウントされる
2. PHP(Apache)コンテナには
    - webrootディレクトリがマウントされる
	
という事が起きます。簡単。

あとはホスト側でwebrootディレクトリ上にWordPressを置いてwp-config.phpを調整すれば使えます。簡単！

```
$> docker-compose down -v
```

で、まとめてコンテナ削除とボリューム削除が行われます。
オプションの**-v**を入れないとボリュームが残ってしまいます。

