# WordPress ローカル開発環境テンプレート

## 概要

ローカル環境で、Docker仮想環境を使ってWordPressの開発ができます。  
開発した内容は/htmlフォルダに保存されます。  

## 使い方(ローカル開発環境の起動方法)

Dockerをインストールする
docker-compose.ymlを、プロジェクトを作るディレクトリにコピーして  
`docker compose up -d --build` コマンドを実行すれば完了。  
http://localhost を開けば、WordPressが開けます。  
終了するときは、`docker compose down`で終了します。  

また、変更内容をコミットしたい場合は、.gitignoreファイルを編集して、不要な行をコメントアウトすること。

## 具体的なプロジェクト

smaple-usecaseブランチで、実際のプロジェクトのサンプルを確認できます。

## 参考

https://docs.docker.jp/compose/wordpress.html  
https://zenn.dev/persona/articles/50f87da99c92af  
https://github.com/github/gitignore/blob/main/WordPress.gitignore  
