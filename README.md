
# データ分析用開発環境セットアップ手順

このリポジトリは、Google Drive上のデータを活用したデータサイエンス・分析のための開発環境（Dev Container + conda）を簡単に構築できるテンプレートです。

前提条件： Windowsの場合
- すでにwsl2をインストールしている
- DockerDesktopをインストールしてUbuntuに設定
- VSCodeをインストール済み

---

## 構成
- Dev Container 対応
- conda環境（Python, numpy, pandas, matplotlib, jupyterlab, geopandas, gdal, scikit-learn, seaborn, japanize-matplotlib など）
- Google Drive連携によるデータ管理

---

## セットアップ手順
まずはリポジトリを任意の場所に clone　してください。

### 1. Google Driveの準備
1. Google DriveクライアントをPCにインストールし、同じGoogleアカウントでログイン
2. データ用フォルダ（例: `ResearchData`）をGoogle Drive上に作成
3. ローカルにGoogle Driveフォルダを同期（例: `/mnt/c/Users/ユーザー名/Google Drive/ResearchData`）
※　設定をミラーリングにすること

### 2. Google Drive データディレクトリのマウントについて

このリポジトリの devcontainer は、Google Drive 上のデータディレクトリを `/workspaces/ResearchEnv/workspace/data/` にマウントすることを想定しています。

各自の環境での設定方法

`.devcontainer/devcontainer.local.json` を作成し、以下の内容で自分の Google Drive データディレクトリのパスを指定してください。

例:

```
{
  "mounts": [
    "source=/mnt/c/Users/あなたのユーザー名/マイドライブ/ResearchData,target=/workspaces/ResearchEnv/workspace/data/,type=bind"
  ]
}
```

- `source=` の後ろは各自のPC環境に合わせて修正してください。
- `devcontainer.local.json` は **git管理しないでください**（`.gitignore` で除外しています）。

## 参考
- devcontainer の詳細: https://containers.dev/
- VS Code Dev Containers 拡張: https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers
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
