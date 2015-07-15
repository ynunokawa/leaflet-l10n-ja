Leaflet への貢献
=======================

 1. [Leaflet プロジェクトへの関わり方](#getting-involved)
 2. [バグの報告](#reporting-bugs)
 3. [コードの貢献](#contributing-code)
 4. [ドキュメントの改善](#improving-documentation)

## Leaflet プロジェクトへの関わり方

サードパーティのパッチは最高のマッピング ライブラリを作成するためのリクエストのうえで絶対に欠かせないものです。しかし、それが Leaflet 開発に関わる唯一の方法というわけではありません。バグの発見と[報告](#reporting-bugs)、[ドキュメントの改良](#improving-documentation)、[Leaflet フォーラム](https://groups.google.com/forum/#!forum/leaflet-js)と [GitHub の Issues](https://github.com/Leaflet/Leaflet/issues) を通じたその他の援助、[Leaflet UserVoice ページ](http://leaflet.uservoice.com)上での提案、[@LeafletJS](http://twitter.com/LeafletJS) へのツイート、同僚や友達の間で Leaflet についての噂を広めることによって途方もないプロジェクトを支えることができます。

## バグの報告

プロジェクトの [Issues ページ](https://github.com/Leaflet/Leaflet/issues)でバグを報告する前に、まず報告しようとしている事象がアプリのコード（たとえば、メソッドの引数が不適切など）ではなく Leaflet によるものなのかを確認してください。次に、類似したケースについてすでに報告されていないか調査してください。もし、類似したケースの報告がすでにあれば、コメント内にその旨を追記してください。

新たに Leaflet のバグを発見した後は、より簡単に早く修正できるように報告するための以下の Tips を一覧してください。

* **内容がわかるようなタイトル**をつけてください。悪い例: *Problem with polylines*　良い例: *Doing X in IE9 causes Z*
* 説明文に**ブラウザー、OS、Leaflet のバージョン**を記載してください。
* バグを再現するための**シンプルなテスト ケース**を作成してください（例:  [JSFiddle](http://jsfiddle.net/) や [JS Bin](http://jsbin.com/) の使用）。
* **他のブラウザー**でバグが再現されるかどうかを確認してください。
* 安定したバージョン、master、あるいはその両方でバグが発生するか確認してください。
* *Bonus tip:* バグが安定したバージョンでは起きず、master バージョンでのみ起きる場合、バグを生じさせているコミットを発見するために `git bisect` を使用してください。

あなたのプロジェクトの援助をしてほしい場合は、[Leaflet フォーラム](https://groups.google.com/forum/#!forum/leaflet-js) を利用してください。

## コードの貢献

### パッチを受け入れるための検討

喜んでパッチを受け入れる間は、Leaflet をシンプルかつ軽量で高速に維持するためにコミットされます。
多くのコードを追加しないバグ修正やパフォーマンス最適化、小さい改良のためであればすぐに受け入れられる可能性が高いです。

新しい機能を含んだ Pull Request を送信する前に、以下の２つの質問を自身に投げかけ、同じ提案を以前に（[GitHub issues](https://github.com/Leaflet/Leaflet/issues)
あるいは [Leaflet UserVoice](http://leaflet.uservoice.com/) で）議論されていないか確認してください。

1. この新しい機能が Leaflet のコアとして十分にその存在を正当化することが重要であることを確認しましたか？あるいは別のリポジトリ内のプラグインとして存在する方が適切でしょうか？
2. コードベースに大容量のコードを追加しないシンプルで簡潔な方法で記述されているでしょうか？

あなたの機能あるいは API が master 内にマージされた場合、
これに対応する[ドキュメントの更新](#improving-documentation)を含んだ別の Pull Request を送信することを検討してください。

### ビルド システムのセットアップ

Leaflet のビルド システムは [Node](http://nodejs.org/) と [Jake](http://jakejs.com/) の JavaScript ビルド ツールを使用します。
Leaflet ビルド システムをセットアップするには、まず Node をインストールして、以下のコマンドでプロジェクトのルート ディレクトリに Jake をインストールしてください。

```
npm install -g jake
npm install
```
`jake`（`dist` フォルダー内のソースからビルドされます）を起動することによって縮小された Leadlet をビルドすることができます。
選択されたコンポーネントを含むカスタムのビルドを作成するには、ブラウザーで `build/build.html` を開いて、そこからの指示に従ってください。

### Leaflet ソースへの変更の作成

GitHub の手法（Fork, Pull Request など）にまだ慣れていない方は、GitHub ヘルプの [Fork A Repo](https://help.github.com/articles/fork-a-repo) を読めばすぐに GitHub を始めることができるでしょう。

必ず**自身のトピックのブランチ**内に変更内容の（機能、バグ修正など）各バッチを記述してください。
`master` ブランチにコミットしないでください。また関連しない変更を同じ Pull Request に含めないでください。

オリジナルのコードベースのコード スタイルと空白規則に従ってください。
具体的には、位置合わせ用のインデント用のタブとスペースを使用しましょう。

変更をコミットする前に、コード内の JavaScript エラーをキャッチするために `jake lint` を実行して、エラーがあれば修正しましょう。
Leaflet のソースに新しいファイルを追加する場合は、ビルド システムがそれらを認識するために `build/deps.js` にそれらを追加しているか確認しましょう。

また、Git 内で適切に[行末の設定](https://help.github.com/articles/dealing-with-line-endings)が行われていることを確認してください！それ以外の場合はdiffはファイルのすべての行が一つだけ触れた場合でも、変更されたことが表示されます。

Also, please make sure that you have [line endings configured properly](https://help.github.com/articles/dealing-with-line-endings) in Git! Otherwise the diff will show that all lines of a file were changed even if you touched only one.

コーディングを楽しもう！

## テストの実行

コマンドラインからテスト実行するために、[PhantomJS](http://phantomjs.org/) をインストールしましょう（そして、あなたの `PATH` 内にあるか確認しましょう）。インストールしたら、以下のコマンドを実行します。

```
jake test
```
同時に実際のブラウザーでテストを実行することもできます。

```
jake test --ff --chrome --safari --ie
```
手動でブラウザーでのテストを実行する場合は `spec/index.html` を開いてください。

## コードの範囲

テストの範囲について詳細なレポート（テストの改善に取り組んでいるときに大変役立ちます）を生成するには、以下のコマンドを実行します。

```
jake test --cov
```
実行後、レポートを確認するには `spec/coverage/<environment>/index.html` を開いてください。
個別の範囲の詳細を取得するにはフォルダー/ファイルをクリックしてください。

## ドキュメントの改善

すべてのドキュメントとサンプルを含む Leaflet Web サイト のコードは `gh-pages` ブランチに配置されています。[Jekyll](http://jekyllrb.com/) を使えば HTML とマークダウン ファイルのセットから自動生成することができます。

ブラウザーを離れずにタイプミスを修正するといったような、小さい改良を作成するもっとも簡単な方法はオンラインの GitHub エディターを使ってファイルを編集する方法です。
[gh-pages ブランチ](https://github.com/Leaflet/Leaflet/tree/gh-pages) を開いて、
編集する特定のファイル（たとえば、API リファレンスの `reference.html`）を選択し、
編集ボタンをクリックし、エディターの指示に従って変更を行い、
マージをしたら、Web サイト上に即座に変更が反映されます。

このプロセスでどのように見えるかを確認するためにローカル リポジトリで編集を行う必要がある場合、以下に従ってください。

 1. [Ruby](http://www.ruby-lang.org/en/) をインストールします。
 2. `gem install jekyll` を実行します。
 3. `Leaflet` のルート フォルダー内で `jekyll serve --watch` を実行します。
 4. ブラウザーで `localhost:4000` を開きます。

ページをリロードしているときに、自動的にファイルの変更は更新されます。
変更がコミットされたら、Pull Request を送信しましょう。

master バージョン（安定したバージョンではなく）内でのみ現れる新しい機能に従ってドキュメントを更新する必要がある場合は、
`gh-pages` の代わりに `gh-pages-master` ブランチに変更を作成する必要があります。
安定したバージョンとしてリリースされるときに、後者にマージされるでしょう。

## 謝辞（Thank you）

Leaflet プロジェクトとコミュニティへの貢献に感謝するとともにあなたを AWESOME（素晴らしい）メンバーにします。
[承認された AWESOME メンバーのリスト](https://github.com/Leaflet/Leaflet/graphs/contributors) に参加して、オンライン マップの可能性の限界を拡げましょう！
