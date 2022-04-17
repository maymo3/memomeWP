# pugとSassを監視してコンパイルする
## プロジェクトをnpmで管理するために初期化する
```sh
npm init
```

## 必要なパッケージのインストール
```sh
npm install pug pug-cli sass npm-run-all watch --save-dev
```
| パッケージ | 役割 |
----|---- 
| pug | .pugファイルのコンパイル |
| pug-cli | コマンドラインでpugを使えるようにする |
| sass | .sassファイルのコンパイル |
| npm-run-all | 複数のnpmスクリプトを同時に走らせる |
| watch | 特定のディレクトリを監視する |
## プロジェクトの構成
```
projectname/
├╴ node_modules/
├┬ public/
│├┬ css/
││├╴ normalize.css
││├╴ reset.css
││└╴ style.css
│├╴ img/
│├┬ js/
││└╴ script.js
│└─ index.html
├┬ source/
│├┬ pug/
││└╴ index.pug
│├╴ pug_parts/
│└┬ sass/
│ ├╴ _variable.sass
│ └╴ style.sass
├╴ .gitignore
├╴ package-lock.json
└╴ package.json
```
## npm scriptsを書く
`package.json`の`"scripts": {}`内を以下のように書き換える。
```json
  "scripts": {
    "start": "run-p watch/*",
    "sass": "sass --no-source-map source/sass:public/css",
    "pug": "pug ./source/pug --out ./public --pretty",
    "watch/sass": "watch 'npm run sass' ./source/sass",
    "watch/pug": "watch 'npm run pug' ./source/pug"
  },
```
## 監視とコンパイル
__.pugファイルと.sassファイルの監視とコンパイル__
```sh
npm start
```
__監視とコンパイルを終了する__
```sh
^C
```
.pugファイルのみコンパイル
```sh
npm run pug
```
.sassファイルのみコンパイル
```sh
npm run sass
```
## gitを使う
プロジェクトにgitを適用する
```sh
git init
```
リポジトリ内の変更があったすべてのファイルをaddする
```sh
git add -A
```
参考：[git add -u と git add -A と git add . の違い | note.nkmk.me](https://note.nkmk.me/git-add-u-a-period/)
```sh
git commit -m "編集内容"
```
```sh
git status
```
## GitHubを使う
まずブラウザからGitHubで新しいリポジトリを作成する。

次にローカルのプロジェクトを作成したリポジトリに紐付ける。
```sh
git remote add origin git@github.com:your-github-username/projectname.git
```
GitHubに変更を適用する
```sh
git push -u origin master
```

## ライセンス
このリポジトリの内容は[MIT License](https://licenses.opensource.jp/MIT/MIT.html)です。また、以下のMITライセンスのコンテンツを含みます。
* normalize.css v8.0.1
    
    [Normalize.css: Make browsers render all elements more consistently.](http://necolas.github.io/normalize.css/)
* HTML5 Doctor CSS Reset CSS v1.6.1

    [HTML5 Reset Stylesheet | HTML5 Doctor](https://html5doctor.com/html-5-reset-stylesheet/)
* Hatena-Blog-Theme-Boilerplate

    [hatena/Hatena-Blog-Theme-Boilerplate](https://github.com/hatena/Hatena-Blog-Theme-Boilerplate)
