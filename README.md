# データ分析用開発環境セットアップ手順

このリポジトリは、Google Drive上のデータを活用したデータサイエンス・分析のための開発環境（Dev Container + conda）を簡単に構築できるテンプレートです。

---

## 構成
- Dev Container 対応
- conda環境（Python, numpy, pandas, matplotlib, jupyterlab, geopandas, gdal, scikit-learn, seaborn, japanize-matplotlib など）
- Google Drive連携によるデータ管理

---

## セットアップ手順

### 1. Google Driveの準備
1. Google DriveクライアントをPCにインストールし、同じGoogleアカウントでログイン
2. データ用フォルダ（例: `ResearchData`）をGoogle Drive上に作成
3. ローカルにGoogle Driveフォルダを同期（例: `/mnt/c/Users/ユーザー名/Google Drive/ResearchData`）

### 2. .envファイルの編集
- `.env` ファイルの `GOOGLE_DRIVE_PATH` を自分の環境に合わせて編集してください。
  例:
  ```
  Windows上のパスが以下の場合
  "G:\マイドライブ\ResearchData"
  wsl用のパスは以下のようになる
  /mnt/g/マイドライブ/ResearchData
  ```

### 3. Dev Containerの起動
- VS Code にDevContainer拡張機能をインストール
- VS Codeでこのリポジトリを開き、「Reopen in Container」または「Dev Containerで開く」を選択
- 初回起動時にconda環境が自動構築されます

### 4. データの利用例
- コンテナ内から `/workspace/data` にアクセスすると、Google Drive上のデータが利用できます。

  例: Jupyter Notebook
  ```python
  import pandas as pd
  df = pd.read_csv('/workspace/data/sample.csv')
  ```

---

## 注意事項
- `.env` ファイルは各自の環境に合わせて編集し、**公開リポジトリには含めないでください**（`.gitignore`推奨）
- Google Driveのパスやユーザー名はPCごとに異なります
- Windows/WSLの場合は `/mnt/c/Users/ユーザー名/Google Drive/...` となります

---

## 推奨環境
- VS Code + Dev Containers拡張
- Google Driveクライアント
- Windows/WSL, Mac, Linux いずれも可

---
