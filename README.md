# RELink Site

RELink（Real Entity Link）の考え方、アーキテクチャ、想定ユースケース、開発ロードマップを紹介するプロジェクトサイトです。

AR-XML Core Draft 4を基礎とするWeb Runtime baseline、独立したRELink Testbed、Web Runtime Test Harnessを接続し、代表的な処理経路を実ブラウザ環境で検証済みです。確認範囲は、今回実行した代表ケースに限定されます。

Resolver Core 0.1、Resolver Lifecycle 0.1、Manifest 0.1、Conformance Catalog 0.1、Web Runtime Integration Contract 0.1等はFrozen baselineとなり、Reference Resolverの実装が始まっています。現在の次段階は、HTTPSベースのL1外部統合検証です。

## Website

**https://ranmaru50.github.io/relink-site/**

Technical guide:

**https://ranmaru50.github.io/relink-site/smart-home.html**

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
- `smart-home.html` — 照明と室温を題材にしたRELink技術解説
- `smart-home.css` — 技術解説ページ固有の図・コード・レスポンシブデザイン
- `script.js` — モバイルナビゲーション

## Related projects

- [relink-web-runtime](https://github.com/ranmaru50/relink-web-runtime)
- [relink-testbed](https://github.com/ranmaru50/relink-testbed)
- [relink-resolver](https://github.com/ranmaru50/relink-resolver)
- [Web Runtime Test Harness usage](https://github.com/ranmaru50/relink-web-runtime#web-runtime-test-harness)
- [AR-XML Core 0.1 Draft 4](https://github.com/ranmaru50/relink-web-runtime/blob/main/docs/specs/arxml-core-0.1-draft4.md)

## Validation status

実ブラウザで確認済みの代表経路:

```text
AR-XML retrieval
→ Draft 4 parse
→ Capability discovery
→ Explicit invocation
→ HTTP GET / POST
→ CORS / preflight
→ Response interpretation
→ Result / error mapping
```

`Representative E2E PASS` は、仕様上のすべての処理経路を検証したという意味ではありません。

## License

License information will be added as the project policy is finalized.
