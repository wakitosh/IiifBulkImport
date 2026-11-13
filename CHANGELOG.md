# Changelog

## v0.2.1 - 2026-11-13

### English

- **Security**:
  - The manifest label is now stripped of markup before it becomes the item title, like the other values taken from a manifest.
  - `homepage` and `seeAlso` addresses are stored as links only when they are `http` or `https` URLs. Other schemes were stored as they were and could end up as a script link on the item page.
  - Image service addresses listed in a manifest are no longer fetched when they are not `http`/`https`, or when their host is not the manifest's own host and resolves to a loopback, private or link-local address. Skipped addresses are reported in the job log. A public host that redirects to an internal one is not detected, so manifests should still come from sources you trust.
  - The import page is now closed to the `site_admin` role. It was meant for global administrators only, but Omeka grants `site_admin` every permission unless one is denied explicitly.
- **Bug Fixes**:
  - A service entry whose id is not a string no longer stops the job.
  - `module.ini` carried an old version number; it now matches the release.

### 日本語

- **セキュリティ**:
  - マニフェストの label を、マニフェストから取り込む他の値と同様に、マークアップを取り除いてからアイテムのタイトルにするようにしました。
  - `homepage` と `seeAlso` のアドレスは、`http` または `https` の URL の場合だけリンクとして保存します。従来は他のスキームもそのまま保存され、アイテムページでスクリプトのリンクになる可能性がありました。
  - マニフェストに書かれた画像サービスのアドレスは、`http`/`https` 以外の場合、またはホストがマニフェスト自身のホストと異なり、ループバック、プライベート、リンクローカルのアドレスに解決される場合は取得しません。取得しなかったアドレスはジョブログに記録します。内部アドレスへリダイレクトする公開ホストは検出できないため、マニフェストは引き続き信頼できる提供元のものを使ってください。
  - インポート画面を `site_admin` ロールでは開けないようにしました。全体管理者だけを想定していましたが、Omeka は明示的に拒否しない限り `site_admin` にすべての権限を与えます。
- **バグ修正**:
  - id が文字列でない service があってもジョブが止まらないようにしました。
  - `module.ini` のバージョン番号が古いままだったため、リリースと一致させました。

## v0.2.0 - 2025-09-06

### English

- **Added Settings Page**: Module behavior can now be configured from the admin interface.
  - Height-based fallback image sizes.
  - HTTP timeout and retry count.
  - Maximum image dimensions (width/height) to prevent processing errors.
- **Enhanced Robustness**:
  - Implemented a fallback to retry with specific image sizes (e.g., 4000px, 2400px height) if the default IIIF import fails.
  - Added a summary to job logs, including a sample of failed media URLs.
- **Bug Fixes**:
  - Resolved CSRF error and form saving issues on the settings page.
  - Improved fallback logic to fix an issue where media was not created for some manifests.

### 日本語

- **設定画面の追加**: モジュールの動作を管理画面から設定できるようになりました。
  - 高さベースのフォールバック画像サイズ
  - HTTPタイムアウトとリトライ回数
  - 処理エラーを防ぐための最大画像サイズ（幅・高さ）
- **堅牢性の強化**:
  - デフォルトのIIIFインポートに失敗した場合、特定の画像サイズ（例：高さ4000px, 2400px）でリトライするフォールバックを実装。
  - ジョブログに、失敗したメディアURLのサンプルを含む要約を追加。
- **バグ修正**:
  - 設定画面でのCSRFエラーとフォーム保存の問題を解決。
  - フォールバックロジックを改善し、一部のマニフェストでメディアが作成されない問題を修正。

---

## v0.1.0 - 2025-09-04

### English

- Initial public release.
- Accepts multiple manifest URLs to create items/media from each.
- Automatic application of "Base Resource" template and DCTERMS mapping (with EN/JA label support).
- Automatically assigns `dcterms:type=StillImage` if images are present.

### 日本語

- 初回公開リリース
- 複数マニフェストURLを受け付け、各マニフェストからアイテム/メディア作成
- Base Resource 自動適用、DCTERMSマッピング（英/日ラベル対応）
- 画像がある場合は dcterms:type=StillImage を自動付与

