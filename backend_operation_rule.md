# バックエンド運用ルール
バックエンド用の運用時のパッケージインストールの注意事項、Flake8・Black、VSCodeの設定・拡張機能について書かれたドキュメントです。 

## コンテナ内でライブラリを追加しても良いか

結論から言うと、コンテナ内で新しくライブラリをインストールして問題ありません。ただし、**developブランチにマージする際にメンバー全員にアナウンス**をお願いします。  
developが更新されたら各チームメンバーはインストールし直します。

## ライブラリインストール関連のコマンド
pipを用いてインストールし、**インストール後は必ずルートのrequirements.txtを更新します**。（poetryを使おうとして諦めました…）  

ライブラリインストール
```
pip install <ライブラリ名>
```

requirements.txtの更新
```
pip freeze > requirements.txt
```

requirements.txtからインストール
```
pip install -r requirements.txt
```


## Flake8, mypy, Black, isort
ビルド時に全て自動で設定されているので特に設定することはありません。
- Flack8：Pythonのリンター
- mypy：Pythonの型に関するリンター
- Black：Pythonのフォーマッター
- isort：Pythonのimport順に関するフォーマッター
- 規約に沿わないコーディングを見つけると赤や黄の波線が引かれます。
  - 基本的に赤や黄の波線は全て規約に沿ったコーディングになるよう修正します。
  - 他のメンバーに相談しても解消できない場合はその行だけFlake8, Blackの対象から外します。
- 保存すると自動フォーマットが走ります。
  - ちょっとした間違い（ " と ' など）は自動で修正してくれます。
  - Python 的に問題ないコードでも、コーディング規約に違反するとエラーになります。
- 時々Flake8, Blackがバグって修正しても赤い波線が消えないことがあります。DockerのReopenやRebuildを試してください。


## VSCodeの設定、拡張機能
.devcontainerを設定しているため、VSCodeの設定や拡張機能はDocker Containerを建てると自動で適用されます。詳細はバックエンドの[devcontainer.json](https://github.com/plant-management/hachiue-backend/blob/develop/.devcontainer/devcontainer.json)に書かれています。

### 設定 (settings)
pyファイルは以下の設定が適用されます。

- リンター、フォーマッターに関する各種設定
- 保存時にリンター、フォーマッターの設定に自動でフォーマット

### 拡張機能（extentions）
必須機能と便利機能を追加しました。変更したい、追加したいなどあればメンバーに相談しましょう。（むしろ便利な機能があれば教えて欲しい）

- "ms-python.python"： VSCodeのPython拡張機能
- "donjayamanne.githistory"：Githubの履歴機能
- "oderwat.indent-rainbow"：インデントをカラフルにする
- "mosapride.zenkaku"：全角スペース強調