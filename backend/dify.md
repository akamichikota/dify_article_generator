# 要件定義書

## プロジェクト名
**記事生成チャットボット統合プロジェクト**

## 概要
本プロジェクトでは、DifyのAPIを利用して、ユーザーが入力した複数のキーワードに基づく記事を生成するチャットボットをオリジナルアプリケーションに統合します。ユーザーは複数のキーワードを改行で入力し、それぞれのキーワードに対してDifyのAPIを並行して呼び出し、記事を生成します。ローカル環境のdifyを使います。

## 目的
1. **効率的な記事生成**：複数のキーワードに対して同時に記事を生成し、ユーザーの利便性を向上させる。
2. **迅速な応答**：並行処理を活用し、記事生成の待ち時間を短縮する。
3. **一貫性のあるユーザー体験**：直感的なUIを提供し、ユーザーが簡単に記事生成を行えるようにする。

## 技術スタック
- **フロントエンド**：React, Axios
- **バックエンド**：Node.js, Express.js
- **API**：Dify API
- **デプロイメント**：Docker, Kubernetes（必要に応じて）
- **データベース**：MongoDB（必要に応じて）

## 機能要件

### 1. キーワード入力フォーム
- **入力方法**：改行で複数のキーワードを入力できるテキストエリア。
- **UIライブラリ**：標準的なHTMLテキストエリアを使用。

### 2. 記事生成
- **API呼び出し**：DifyのAPIを利用して、各キーワードに基づく記事を生成。
- **並行処理**：複数のAPIリクエストを同時に送信し、記事を生成。

### 3. 記事表示
- **表示形式**：生成された記事をリスト形式で表示。
- **エラーハンドリング**：API呼び出し中にエラーが発生した場合の処理を含む。

## 詳細設計

### フロントエンド

#### キーワード入力フォーム
- **コンポーネント**：`ArticleGenerator`
- **状態管理**：Reactの`useState`フックを使用。
- **イベントハンドリング**：キーワード入力の変更、記事生成ボタンのクリック。

### バックエンド

#### APIエンドポイント
- **エンドポイント**：`/generate-articles`
- **メソッド**：POST
- **リクエストボディ**：キーワードの配列
- **レスポンス**：生成された記事の配列

