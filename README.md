# Flutter開発環境

このリポジトリはFlutter開発用のDev container設定一式です。

## 開発環境の準備

1. あらかじめ用意するもの
   - Docker / Docker Desktop
   - VS Code
   - Remote - Containers拡張機能

2. 開発環境の起動
   ```bash
   # リポジトリをクローン
   git clone <repository-url>
   cd <repository-name>

   # コンテナ内での作業用ディレクトリを作る
   # あらかじめて作っておかないとDockerの仕様でroot所有で作成される
   mkdir work

   # VS Codeで開く(または、VSCode上でOpen FolderでもOK)
   code .
   ```

3. Dev containerの起動
   - VS Codeの左下の緑色のアイコン(「><」みたいなやつ)をクリック
   - "Reopen in Container"を選択

## プリインストールされているもの

- Flutter SDK
- Dart SDK
- VS Code拡張機能
  - Dart
  - Flutter
- VSCode設定
  - 自動フォーマット
  - コードアクションの自動適用

## 開発の始め方

1. プロジェクトの作成

   dev container起動時のディレクトリは`/usr/src/app`です。
   このディレクトリはホスト側の`work`ディレクトリにマウントされています。

   ```bash
   flutter create <your_app_name>
   ```
   `your_app_name`でアプリのディレクトリが作成されます。
   その後、dev container内でOpen folderして`your_app_name`を選択し、
   ワークスペースの場所を切り替えると良いでしょう。

2. アプリの実行

   ```bash
   flutter run -d web-server --web-hostname 0.0.0.0 --web-port 18888 
   ```

   profileモードやreleaeモードでの起動。
   ```bash
   flutter run -d web-server --web-hostname 0.0.0.0 --web-port 18888 --profile
   ```

   手元のブラウザで http://localhost:18888 にアクセスするとサンプルアプリの画面が表示されます。
