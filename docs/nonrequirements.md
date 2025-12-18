# 非機能要件 (non-functional requirements)

概要
- 本リポジトリは PoC 環境を想定しており、高度な非機能要件は求められない。以下は最小限の非機能要件を記載する。

環境・スケーリング
- Azure Functions の Consumption Plan を使用するため、スケーリングはプラットフォームに委ねる。
- リージョンは Azure 東日本。

パフォーマンス
- PoC のため、厳密なレスポンスタイム SLA は不要。ただし、通常のリクエストは数百ミリ秒以内で応答することを目安とする。

可用性・信頼性
- PoC のため高可用性設計は不要。ただし、Functions の再起動や短時間の停止に耐えられる設計とする。

運用・監視
- 主要なログは Azure Application Insights に送ることを推奨するが、必須ではない。
- エラーログおよびリクエストログを最低限収集すること。

セキュリティ
- API はパブリック公開で認証なしとする（PoC のため）。本番環境では認証・認可を追加する必要がある。

開発プロセス
- Python 依存管理は requirements.txt を使用。
- 単体テストを `tests/` に配置。CI は任意。

制約
- Consumption Plan の実行時間制限や Cold Start の可能性を考慮する。

付録
- 今後、本番移行を検討する場合は以下を追記すること:
  - 認証（Azure AD / API Key）
  - 詳細な SLA、モニタリング、ログ保持ポリシー
  - CI/CD パイプライン（GitHub Actions など）
