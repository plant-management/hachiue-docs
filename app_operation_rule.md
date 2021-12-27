# スマホアプリ運用ルール
スマホアプリ用の運用時のパッケージインストールの注意事項、ESLint、Prettier、VSCodeの設定・拡張機能について書かれたドキュメントです。 

## コンテナ内でパッケージを追加しても良いか

結論から言うと、コンテナ内で新しくパッケージをインストールして問題ありません。ただし、**developブランチにマージする際にメンバー全員にアナウンス**をお願いします。  
パッケージをインストールした人以外はビルドし直す必要があります。また、パッケージをインストールした人もチェックアウトした際にはビルドし直す必要があります。（[Docker環境構築方法](./docker_operation.md)）  
※インストールし直しでもOKです

## npm関連のコマンド
パッケージインストール
```
npm install <パッケージ名>
```

パッケージアンインストール
```
npm uninstall <パッケージ名>
```

アプリ起動
```
npm start
```

アプリ起動中のコマンド  
r：npm restart  
w：Web版起動、[http://localhost:19006](http://localhost:19006)でアクセスできる

## ESLint, Prettier, standard
ビルド時に全て自動で設定されているので特に設定することはありません。
- ESLint：JavaScriptのリンター
- Prettier：JavaScript, CSSのフォーマッター
- standard：コーディング規約の一種、ESLintで設定している
- 規約に沿わないコーディングを見つけると赤や黄の波線が引かれます。
  - 基本的に赤や黄の波線は全て規約に沿ったコーディングになるよう修正します。
  - 他のメンバーに相談しても解消できない場合はその行だけESLintの対象から外します。
- 保存すると自動フォーマットが走ります。
  - ちょっとした間違い（ " と ' など）は自動で修正してくれます。
  - React Native, TypeScript 的に問題ないコードでも、コーディング規約に違反するとエラーになります。
- `npm start` を実行中は時々ESLintやPrettierがバグって修正しても赤い波線が消えないことがあります。その場合は `Ctrl + c` で `npm start` を終了して、もう一度 `npm start` してください。


## VSCodeの設定、拡張機能
.devcontainerを設定しているため、VSCodeの設定や拡張機能はDocker Containerを建てると自動で適用されます。詳細はアプリの[devcontainer.json](https://github.com/plant-management/hachiue-app/blob/develop/.devcontainer/devcontainer.json)に書かれています。

### 設定 (settings)
js, jsx, ts, tsxファイルは以下の設定が適用されます。

- 基本的にJavaScriptのコーディング規約の1つ[standard](https://standardjs.com/rules.html)に従います。
- 保存時にESLint, Prettierの設定に自動でフォーマットがかかります。

### 拡張機能
必須機能と便利機能を追加しました。変更したい、追加したいなどあればメンバーに相談しましょう。（むしろ便利な機能があれば教えて欲しい）

- "dbaeumer.vscode-eslint"：JS用Linter
- "esbenp.prettier-vscode"：JS用Prettier
- "formulahendry.auto-rename-tag"：HTML開始タグの編集を終了タグにも伝える
- "donjayamanne.githistory"：Gitの履歴確認
- "mosapride.zenkaku"：全角スペース
- "oderwat.indent-rainbow"：インデントをカラフルにする
- "xabikos.javascriptsnippets"：JS用Snippets
- "yzhang.markdown-all-in-one"：Markdownツール
- "dsznajder.es7-react-js-snippets"：React用snippet