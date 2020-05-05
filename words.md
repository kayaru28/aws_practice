# Compute
## EC2
* ハードウェア占有インスタンス
* Dedicated Host
* 自動配置
* ホストアフィニティ

## Auto Scaling
* AZRebalance

## Lambda
* 実行コンテキストの再利用

## スポットインスタンス
* スポットフリート
* スポットブロック

## Elastic Beanstalk
* Swap Enbironment URLs

## ECS
* タスクネットワーキング／awsvpcネットワークモード
* EC2起動タイプ／Fargate起動タイプ

## API gateway
* エッジ最適化 API エンドポイント
* リージョン API エンドポイント
* プライベート API エンドポイント

## Batch
* ジョブ／ジョブ定義／ジョブキュー
* コンピューティング環境
* コンテナレジストリ
* ストレージ


# Storage
## S3 
* Amazon S3 Transfer Acceleration
* S3 MFA delete
* リクエスタ支払いバケット
* Range HTTP ヘッダー／Range get

# Databases
## RDS
* クロスリージョンリードレプリカ
* AWS Database Migration Service
### Aurora
* 自動スケールアップ
* インスタンスエンドポイント/クラスターエンドポイント/読み込みエンドポイント

## DynamoDB
* クロスリージョンリードレプリケーション
* TTL
* DynamoDB グローバルテーブル

# Networking & Content Delivery

## ELB
* Proxy Protocol header
### ALB
* SNI（Server Name Indication）
* balancing to on premice servers

## Croud Front
* Origin Protocol policy
* オリジンフェイルーバー

## Direct Connect
* Virtual Privte Gateway
* Customer Gateway
* クロスネットワーク接続 (別名クロスコネクト)
* Direct Connect Gateway

## Transit Gateway
* Route Domain

# Management & Governance
## CloudTrail
* グローバルサービスイベント
* 整合性の検証

## Cloud Formation
* DeletionPolicy,Retain 属性
* スタックセット
* スタックインスタンス

## Service Catalog
* 製品
* ポートフォリオ
* 制約
* ポートフォリオへのアクセス権
* TagOptionライブラリ
* アカウント間ポートフォリオ共有
* ポートフォリオ課金

## AWS System Manager
* SSMエージェント／SSM APIへのアクセス経路／EC2ロール
* Change Calendar
* メンテナンスウィンドウ
* コンプライアンス
* インベントリ
* マネージドインスタンス
* ハイブリッドアクティベーション
* セッションマネージャー
* Run Command／Automation
* ステートマネージャ
* パッチマネージャー
* ディストリビューター
* パッチベースライン
* パッチグループ
* SSM ドキュメント
  * AWS-ConfigureWindowsUpdte
  * AWS-InstallWindowsUpdates
  * AWS-RunPatchBaseline

# Media Services
## Amazon Elastic Transcoder
* Pipline
* Job
* Preset
* User metadata

# Security, Identity & Compliance
## IAM
### IAMロール
* インスタンスプロファイル

## Organizations
* 組織単位(OU)
* 管理用ルート(root)
* サービス管理ポリシー(SCP)
* AWS generated tags／ユーザ定義タグ有効化

## Direcroty Service
* Simple AD
* snapshot backup
* DHCPオプションセット
* Simple Systems Manager(SSM)
* Active Directory フェデレーションサービス（ADFS）
* AD Connector（によるフェデレーション）

## Cognito
* User Pools (include IdP)
* Federated Identities
* Cognito Sync
* Amazon Cognito Push Sync
* Amazon Cognito Stream
* Amazon Cognito Events

# Analytics
## Athena
* Presto (in memory)
* AWS Glue Data Catalog
* column base
* CTAS
* S3/Glueへのアクセス権限

## Amazon Elasticsearch Service
* Amazon ES ドメイン

## EMR
* インスタンスフリート
* マスターノード／コアノード／タスクノード

# Machine Learning
## AmazonSageMaker
* ノートブックインスタンスタイプ
* IAMロール
* ラベリング／開発／学習／モデル変換／推論
* gitインテグレーション
* ライフサイクル設定
* instance_count

## Amazon Rekognition 
* RecognizeCelebrities

# Application Integration
## SQS
* standerd→FIFOは作り直し
### FIFOキュー
* メッセージ重複排除ID
* メッセージグループID
* シーケンス番号
* デッドレターキュー

## StepFunction
* ASL (Amazon States Language)
* ステートマシン
* State
* Activity
* InputPath/Parameters/ResultPath/OutputPath

## Amazon MQ
* メッセージブローカー
* Apache ActiveMQ
* AMQP/MQTT/OpenWire/STOMP
* FIFO/once-and-only-once
* Apache ActiveMQ Advisory Topics/Apache ActiveMQ統計プラグイン

## Data Pipeline
* パイプラインコンポーネント
* インスタンス
* 試行
* Task Runner パッケージソフト

# Developer Tools
## CodeCommit
* Git ×　(S3,DynamoDB,KMS)
* Commit Visualizer
* CodeCommitリポジトリトリガー
## CodeBuild
* Build project
## CodeDeploy
* AppSpecファイル(files/hooks)
* デプロイメント構成（One-at-a-time,Custome,Half-at-a-time,All-at-once）
* デプロイメントグループ（タグ、AutoScaling）
* デプロイメントタイプ（In-place/Blue-Green）
* IAMインスタンスプロファイル
* リビジョン/ターゲットリビジョン
* サービスロール
## CodePipeline
* アクションタイプ（Source,Build,Test,Deploy,Approbal,Invoke）
## CodeStar
* プロジェクトテンプレート
* CI/CD全体のダッシュボード

# other
* AWS Connector for vCenter
* ec2-bundle-instance API
* Forward Cookies
* AppStream 2.0

# Cooperation
* Kinesis Firehause → Redshift,S3,Amazon ES
* S3 event → SNS,SQS(standerd),Lambda
* RDS event → SNS
* AWS DMS ← on-premises DB,S3
* AWS DMS → on-premises DB,EC2-base DB,Amazon ES,RDS,Redshift,DynamoDB,S3,Kinesis Data Streams,DocumentDB
* CodeCommit Ripogitory Trigger → SNS,Lambda
* CodeBuild ← CodeCommit,S3,GitHub
* CodeDeploy ← S3,GitHub
* AutoScaling → EC2,ECS,DynamoDB,Aurora(Read Replica)
* WAF → CloudFront,ALB
* Shield → EC2,ELB,CloudFront,Route53
* snowball ←→ S3
* Batch ←→ S3,EFS
* Batch ← Lambda,CloudWtch Events
