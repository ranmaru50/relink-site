# AGENTS.md

このファイルはリポジトリ全体に適用されます。RELink Siteを編集するagentは、変更前にこのファイルと `README.md` を読み、以下の方針を守ってください。

## Purpose

RELinkの目的、アーキテクチャ、実装状況、技術的な責務境界を、初見の読者にも正確に伝える静的プロジェクトサイトです。魅力的な説明と、確認済み事項・未検証事項の透明性を両立してください。

## Source of truth

- 編集前に既存ページ、navigation、design tokens、関連するRELinkリポジトリと現行仕様を確認する。
- AR-XML syntax、Web Runtime API、Resolverの用語を推測で記述しない。
- 実装状況が変わる内容は、対象リポジトリの現状を確認してからstatusと本文を同時に更新する。

## Architecture invariants

次の区別を崩さないでください。

```text
Entity ≠ Location
Capability ≠ Interface
Description ≠ Execution
Resolution ≠ Authentication
Retrieval URL ≠ Canonical Entity Identity
```

- `AR-XML = Entity Interface Description Language` と説明し、UI markupとして扱わない。
- ResolverはAnchor / UUIDを現在のAR-XML Description Locationへ解決する。Capability APIへアクセス、AR-XML parse、Interface選択、Capability Invocationは行わない。
- Web RuntimeはAR-XMLをload、parse、validate、evaluateし、CapabilityをApplicationへ公開する。
- RuntimeはCapabilityを自動実行しない。実行主体はHumanまたはApplicationである。
- Capability APIは通常のWeb APIであり、RELinkはそれを置き換えず、記述・発見・利用の入口を提供する。
- Resolution、integrity、authentication、authorizationを同一視しない。
- 相対Interface URLは最終AR-XML Document URLをbaseとして標準URL resolutionする。

## Status and claims

- `implemented`、`operational`、`in development`、`next`、`planned`、`future`を根拠に合わせて使い分ける。
- Representative E2Eの成功を、完全な仕様準拠や全ケース検証済みと表現しない。
- 根拠がない限り、`Full Conformance`、`Production Ready`、完全準拠などの表現を使用しない。
- 将来アーキテクチャを現在の実装フローとして見せない。必要なら `Target Architecture` や `Planned` と明示する。

## Information architecture and navigation

- `index.html` はプロジェクトの全体像、現在地、主要プロジェクトとGuideへの入口を担う。
- 詳細な技術解説は専用ページへ分離する。
- 新しい主要ページはグローバルナビゲーションから到達可能にする。
- 主要Guideにはナビゲーションだけでなく、Hero CTAまたはトップページの目立つ案内カードを設ける。
- 同一ページ内リンクには `↓`、現在の文書を離れるサイト内別ページ・外部リンクには `↗` を使用する。
- カード型リンクには明確なhover/focus stateを設け、可能ならカード全体をクリック可能にする。

## Implementation rules

- 既存の依存なし静的HTML/CSS/JavaScript構成を維持する。明確な必要性なしにframeworkやbuild stepを追加しない。
- 共通の色、文字、余白、layout、component styleは `styles.css` を再利用する。
- ページ固有の図やlayoutは、例として `smart-home.css` のようなページ固有CSSへ置く。
- 既存のブランドアイコン、status badge、レスポンシブbreakpoint、motion preferenceへの対応を維持する。
- 新規ページには適切なtitle、description、canonical URL、OGP/Twitter metadata、faviconを設定する。
- semantic HTMLを優先し、キーボードfocus、コントラスト、モバイル表示を損なわない。
- unrelatedなファイルやユーザーの変更を上書きしない。

## Validation before handoff

変更内容に応じて、少なくとも次を確認してください。

1. HTMLの入れ子、重複ID、内部アンカー、ページ間リンク。
2. 参照するGitHubリポジトリ、仕様、公開URLにリンク切れがないこと。
3. CSSのsyntaxとbrace、主要breakpointでのlayout。
4. キーボードfocusとリンク記号が編集方針に一致すること。
5. 静的HTTPサーバから対象HTML、CSS、JavaScript、SVGがHTTP 200で取得できること。
6. 技術説明が現行syntax/APIと一致し、自動実行や未証明の準拠を示唆しないこと。
7. 公開を依頼された場合は、`main` 反映後にGitHub Pages deploymentと公開URLを確認すること。

完了報告には、変更ファイル、主要な判断、実施した検証、未確認事項がある場合はその範囲を簡潔に記載してください。
