# RELink Site

RELink（Real Entity Link）の考え方、アーキテクチャ、想定ユースケース、開発ロードマップを紹介するプロジェクトサイトです。

## Website

**https://ranmaru50.github.io/relink-site/**

## Local preview

依存パッケージはありません。リポジトリのルートを任意の静的HTTPサーバで配信してください。

```bash
python3 -m http.server 8080
```

ブラウザで `http://localhost:8080` を開きます。

## Publishing with GitHub Pages

このサイトは、`main` ブランチのリポジトリルートをGitHub Pagesで配信します。ビルド処理や外部依存はありません。

### Initial setup

1. GitHubでリポジトリの **Settings** を開きます。
2. サイドバーから **Pages** を選択します。
3. **Build and deployment** の **Source** で `Deploy from a branch` を選択します。
4. **Branch** を `main`、フォルダーを `/(root)` にして **Save** を押します。
5. 公開処理の完了後、上記のWebsite URLへアクセスします。

### Updating the site

`index.html`、`styles.css`、`script.js` を変更して `main` ブランチへpushすると、GitHub Pagesへ自動的に再公開されます。反映には少し時間がかかる場合があります。

## Structure

- `index.html` — サイト本文
- `styles.css` — レスポンシブデザイン
- `script.js` — モバイルナビゲーション

## Related projects

- [relink-web-runtime](https://github.com/ranmaru50/relink-web-runtime)
- [relink-testbed](https://github.com/ranmaru50/relink-testbed)

## License

License information will be added as the project policy is finalized.
