# Docker 環境構築方法

Docker を用いて開発環境を構築する方法について書かれたドキュメントです。VSCode の GUI の操作方法のみ記載しています。

## 初めに

本アプリ「HACHIUE」は[スマホアプリ](https://github.com/plant-management/hachiue-docs)と[バックエンド](https://github.com/plant-management/hachiue-backend)の2つのリポジトリに分けて構成されています。そのため、スマホ側とバックエンド側の両方をCloneし、Dockerを起動する必要があります。

## 準備

始めにDockerとリポジトリの準備を行います。

1. Dockerの準備を行います。
   - `docker`コマンドと`docker-compose`コマンドが動くようにします。Dockerの[公式サイト](https://docs.docker.com/get-docker/)などを見ながらインストールしたください。
   - VSCode の拡張機能の Remote - Containers (または Remote Development) と Docker(← 拡張機能名です)をインストールします。VSCodeの左タブのExtentions（拡張機能）からそれぞれ検索してインストールしましょう。
2. 任意のフォルダに移動後、下記コマンドで2つのリポジトリをクローンします。  
   - Mac or Linuxの場合
    ```
    git clone https://github.com/plant-management/hachiue-app.git
    git clone https://github.com/plant-management/hachiue-backend.git
    ```
   - Windowsの場合
    ```
    git clone --config core.autocrlf=false https://github.com/plant-management/hachiue-app.git
    git clone --config core.autocrlf=false https://github.com/plant-management/hachiue-backend.git
    ```


## Rebuild 方法

パッケージや拡張機能を追加した際は Rebuild が必要になります。

1. 左下の緑色の「Dev Container: bifb」をクリックします。  
   ![rebuild](https://github.com/yochimonji/bifb/blob/images/rebuild.png)
2. 「Rebuild Container」をクリックしてしばらく待ちます。
3. Rebuild 前と同じ画面に戻ってきたら完了です。

## コンテナ削除方法

何らかの不具合などでコンテナを削除する方法です。

1. コンテナ内にいる場合、左下の緑色の「Dev Container: bifb」をクリックします。  
   ![rebuild](https://github.com/yochimonji/bifb/blob/images/rebuild.png)
2. 「Reopen Folder Locally」をクリックしてローカル環境に戻ります。
3. 左の Activity bar の Docker アイコンをクリックします。
4. コンテナを削除します。CONTANERS -> bifb -> bifb_node を右クリックして、「Remove」をクリックします。警告も「Remove」をクリックします。  
   ![rm_container](https://github.com/yochimonji/bifb/blob/images/rm_container.png)
5. イメージを削除します。IMAGES -> bifb_node -> latest を右クリックして、「Remove」をクリックします。警告も「Remove」をクリックします。  
   ![rm_image](https://github.com/yochimonji/bifb/blob/images/rm_image.png)
6. [Build方法](#build-方法)の 4. 以降をもう一度行い、Buildしなおします。
