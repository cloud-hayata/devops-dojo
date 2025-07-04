# 01 - Jenkins × EC2 による最小構成のCI/CDパイプライン構築

## ゴール

AWS上にEC2サーバーを立ててJenkinsを構築し、  
GitHubとの連携による自動デプロイ環境（CI/CD）を最小構成で実現する。  
実務でよくある「小規模な社内アプリの継続的デリバリ」をイメージした構成。

## 使用技術・サービス

- AWS EC2（Amazon Linux）
- Jenkins（CI/CDエンジン）
- GitHub（コード管理）
- GitHub Webhook
- （Optional: TerraformでEC2を構築）

## アーキテクチャ図

※構成図は現在作成中（外注予定）。以下は構成のイメージ：

[GitHub] → [Webhook] → [EC2 (Jenkins)] → [Deploy Script] → [アプリサーバ]

## 設計ポイント / 技術選定理由

- **Jenkins**を採用した理由：実務での導入事例が多く、CI/CDの王道的存在
- **EC2で構築**：クラウド理解を深める＆SSHやポート開放などの基本操作も練習可能
- **Webhook**による連携：Pushイベントから自動ビルド・デプロイを確認する

## 構築手順（概要）

1. EC2インスタンスの作成（Terraform or マネジメントコンソール）
2. Jenkinsのインストール・起動
3. GitHub Webhookの設定（Push時に通知を飛ばす）
4. Jenkins Job作成 → Git pull → アプリ起動（Shell script）

## 動作確認・成果物

- GitHubにPushすると、Jenkinsが自動でコードを取得し、サーバーにデプロイされる
- 確認用ログ or 動作確認スクリーンショット

## 学び・改善点・補足

- Jenkins Job作成時に環境変数で詰まった（解決方法：xxxx）
- 今後はCodePipelineやGitHub Actionsとの比較構成も試したい
