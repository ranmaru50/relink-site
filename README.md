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

サイトのHTML、CSS、JavaScriptを変更して `main` ブランチへpushすると、GitHub Pagesへ自動的に再公開されます。反映には少し時間がかかる場合があります。公開後はトップページと変更対象ページの両方を確認してください。

## Structure

- `index.html` — サイト本文
- `styles.css` — レスポンシブデザイン
- `smart-home.html` — 照明と室温を題材にしたRELink技術解説
- `smart-home.css` — 技術解説ページ固有の図・コード・レスポンシブデザイン
- `script.js` — モバイルナビゲーション

## Editing policy

このサイトは、RELinkの構想だけでなく、検証済みの範囲と次の開発段階を第三者が区別して評価できることを重視します。

### Page roles

- トップページは、RELinkの目的、全体アーキテクチャ、開発状況、主要プロジェクトへの入口を示します。
- Guideページは、具体的なシナリオ、コード、責務境界を使って技術を詳しく説明します。
- 詳細をトップページへ詰め込みすぎず、重要な新規ページをナビゲーションだけに埋もれさせません。

### Discoverability and link markers

- 重要な新規ページには、グローバルナビゲーションに加えて、トップページのHero CTAまたは目立つ案内カードを設けます。
- `↓` は同一ページ内のセクションへ移動するリンクに使用します。
- `↗` は現在の文書を離れるリンクに使用します。サイト内の別ページと外部サイトのどちらにも適用し、リンク先のラベルから行き先を判別できるようにします。
- カードを導線として使う場合は、可能な範囲でカード全体をクリック可能にし、キーボード操作で確認できるfocus stateを用意します。

### Technical accuracy

掲載するsyntax、API、用語、実装状況は、関連リポジトリと現行仕様を確認してから更新します。特に次の境界を維持します。

```text
Entity ≠ Location
Capability ≠ Interface
Description ≠ Execution
Resolution ≠ Authentication
```

- AR-XMLはEntity Interface Description Languageであり、UI記述言語ではありません。
- ResolverはAnchor / UUIDから現在のAR-XML Description Locationへ解決する層であり、Capabilityを実行しません。
- Web RuntimeはAR-XMLを取得・検証してCapabilityをApplicationへ公開しますが、自動実行しません。
- Capability InvocationはHumanまたはApplicationの明示的な要求で発生します。
- 相対Interface URLは、Host Web Appではなく、最終AR-XML Document URLを基準に解決します。
- 検証済み、実装中、計画中を区別し、`Full Conformance` や `Production Ready` など未証明の状態を示す表現は使用しません。

### Design and accessibility

- 既存の配色、タイポグラフィ、余白、カード、status badge、アイコン表現を優先して再利用します。
- 共通デザインは `styles.css`、ページ固有の表現はページ名に対応するCSSへ置きます。
- モバイル表示、キーボードfocus、十分なコントラスト、リンク先が理解できるラベルを維持します。
- 現在の規模では、依存なしの静的HTML/CSS/JavaScript構成を維持します。

### Checklist for a new page

1. 現行仕様と関連実装を確認し、推測したsyntaxやAPIを書かない。
2. canonical URL、description、OGP/Twitter metadata、faviconを設定する。
3. グローバルナビゲーションとトップページの目立つ導線から到達可能にする。
4. ページ間リンクに `↗`、同一ページ内リンクに `↓` を使用する。
5. モバイル幅とキーボード操作を確認する。
6. HTMLの重複ID、内部アンカー、リンク切れ、CSS syntaxを確認する。
7. ローカルHTTPサーバで各ページとassetが正常に配信されることを確認する。
8. `main` への反映後、GitHub Pagesのdeployment成功と公開URLを確認する。

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
