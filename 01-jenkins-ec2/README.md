# 01 - Jenkins × EC2 による最小構成のCI/CDパイプライン構築

## ゴール

AWS上にEC2サーバーを立ててJenkinsを構築し、  
GitHubとの連携による自動デプロイ環境（CI/CD）を**最小構成**で実現する。  
実務でよくある「小規模な社内アプリの継続的デリバリ」をイメージした構成。

---

## 使用技術・サービス

- AWS EC2（Amazon Linux）
- Jenkins（CI/CDエンジン）
- GitHub（ソースコード管理）
- GitHub Webhook（Pushトリガー）
- （Optional）Terraform（EC2構築をコード化）

---

## アーキテクチャ図

※構成図は現在作成中（外注予定）。以下は構成のイメージ：

[GitHub] → [Webhook] → [EC2 (Jenkins)] → [Deploy Script] → [アプリサーバ]

---

## 設計ポイント / 技術選定理由

- **Jenkins採用理由**：CI/CDの定番ツールであり、実務導入例が豊富
- **EC2利用理由**：クラウド基本操作（SSH, セキュリティグループなど）の訓練に最適
- **Webhook連携理由**：Pushイベントでの“自動化”実現が目的

---

## 構築手順（概要）

1. EC2インスタンスの作成（Terraform or マネジメントコンソール）
2. Jenkinsのインストール・起動
3. GitHub Webhookの設定（PushトリガーをJenkinsに送信）
4. Jenkinsジョブ作成：
    - GitリポジトリをPull
    - `deploy.sh`を実行してアプリ反映

---

## 動作確認・成果物

- GitHubへのPushをトリガーに、Jenkinsがビルド＆自動デプロイを実行
- Jenkins上のログ出力 or EC2上のアプリ起動確認

---

## 学び・改善点・補足メモ

- Jenkinsジョブ作成時、環境変数の設定ミスで詰まった（後述で補足）
- GitHub WebhookとJenkins連携における**セキュリティの取り扱い**も今後整理予定
- 今後の比較予定構成：
    - GitHub Actions × EC2
    - AWS CodePipeline × S3 or Lambda

---

## 関連リポジトリ

- [`cloud-architecture-portfolio`](https://github.com/cloud-hayata/cloud-architecture-portfolio)  
　← Step6 までの土台を構築済（VPC / Terraform / ECS / CI/CD / CloudWatch etc.）

---

> **未経験から年収600万を目指す修行の第1本目。**  
> **ここからすべてが始まる。**
