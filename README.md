# loop-arranger-web

DRUM / BASS / MELODY / FX の4トラックのループ素材をブラウザにアップロードすると、
約3分の構成に自動で組み立ててダウンロードできる、サーバー不要の静的ツールです。

処理はすべて訪問者のブラウザ内（Web Audio API）で完結します。サーバーはこの1枚の
`index.html` を配るだけなので、アクセスが増えても処理負荷はかかりません。

## GitHub Pagesで公開する手順

1. GitHubで新しいリポジトリを作る（例: `loop-arranger-web`）
2. このフォルダの中身（`index.html`）をリポジトリ直下に置いてpush

   ```bash
   git init
   git add index.html
   git commit -m "Add loop arranger web tool"
   git branch -M main
   git remote add origin <あなたのリポジトリURL>
   git push -u origin main
   ```

3. リポジトリの **Settings → Pages** を開く
4. "Build and deployment" の Source を **Deploy from a branch** にする
5. Branch を `main` / フォルダを `/ (root)` にして **Save**
6. 数分待つと `https://<ユーザー名>.github.io/<リポジトリ名>/` で公開されます

## 中身について

- 依存ライブラリなし、外部サーバーへの通信もなし（Google Fontsのみ読み込み）
- アップロードされた音源はブラウザのメモリ上でのみ扱われ、どこにも送信されません
- ダウンロードは通常のブラウザのダウンロード機能を使います（`track.wav`を`.zip`にまとめて保存）
- 曲構成（intro→buildup→drop→break→buildup→drop→outro、108〜112小節）は
  `index.html` 内の `SECTIONS` 定数を書き換えれば自由に変更できます
