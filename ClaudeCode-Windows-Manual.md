# Claude Code for Windows インストールマニュアル

## 概要

Claude Code は、Anthropic が開発した AI コーディングアシスタントツールです。バージョン 0.51 より、Windows Subsystem for Linux (WSL) を必要とせず、Windows でネイティブに動作するようになりました。

### 主な特徴
- Windows ネイティブサポート（WSL 不要）
- 無料で利用可能
- npm パッケージとして提供
- Windows 11 で動作確認済み

## システム要件

### 対応 OS
- Windows 11（編集部確認済み）
- Windows 10（互換性があると予想されるが未確認）

### 必須ソフトウェア
以下のソフトウェアが事前にインストールされている必要があります：

1. **Node.js**
   - JavaScript ランタイム環境
   - npm（Node Package Manager）が含まれる

2. **Git for Windows**
   - バージョン管理システム
   - Windows 環境での Git コマンド実行に必要

## インストール前の準備

### PowerShell 実行ポリシーの設定

初期状態で PowerShell を開くと、スクリプト実行が制限されているため赤文字でエラーが表示される場合があります。（赤文字が表示されていない人は正常に動いていますので、このセクションはスキップしてください。）

これは Windows のセキュリティ機能でスクリプトの実行が制限されているためです。以下の方法で解決できます。

**解決方法:**

1. 管理者権限で PowerShell を開く
2. 以下のコマンドを実行：

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

3. 確認メッセージが表示されたら `Y` を入力して ENTER キーを押す

これにより、ローカルで作成されたスクリプトと、インターネットからダウンロードされた署名済みスクリプトの実行が許可されます。

## インストール手順

### ステップ 1: Node.js のインストール

Windows Package Manager (winget) を使用してインストールします：

```powershell
winget install OpenJS.NodeJS
```

**注意事項:**
- 管理者権限が必要な場合があります
- インストール中に UAC ダイアログが表示される可能性があります

### ステップ 2: Git for Windows のインストール

同様に winget を使用してインストールします：

```powershell
winget install Git.Git
```

### ステップ 3: ターミナルの再起動

Node.js と Git のインストール後、環境変数を適用するためにターミナル（PowerShell、コマンドプロンプト、Windows Terminal など）を再起動することを推奨します。

### ステップ 4: Claude Code のインストール

npm を使用してグローバルにインストールします：

```powershell
npm install -g @anthropic-ai/claude-code
```

**インストール確認:**
以下のコマンドでバージョンを確認できます：

```powershell
claude --version
```

### ステップ 5: Claude Code の起動

インストールが完了したら、以下のコマンドで起動します：

```powershell
claude
```

## トラブルシューティング

### 一般的な問題と解決方法

#### 1. PowerShell でスクリプト実行エラー（赤文字）が表示される
**症状:** 初期状態で PowerShell を開くとスクリプト実行が制限されている旨の赤文字エラーが表示される

**原因:** Windows のセキュリティ機能でスクリプトの実行が制限されている

**解決方法:**
1. 管理者権限で PowerShell を開く
2. 以下のコマンドを実行：
   ```powershell
   Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
   ```
3. 確認メッセージが表示されたら `Y` を入力して ENTER キーを押す

#### 2. 「claude」コマンドが認識されない
**原因:** PATH 環境変数に npm のグローバルパッケージのパスが含まれていない

**解決方法:**
- ターミナルを再起動する
- 必要に応じて PATH 環境変数を手動で設定する

#### 3. npm install 時にエラーが発生する
**原因:** Node.js または npm が正しくインストールされていない

**解決方法:**
- Node.js の再インストール
- 以下のコマンドで npm のバージョンを確認：
  ```powershell
  npm --version
  ```

#### 4. 管理者権限エラー
**原因:** インストール時に管理者権限が必要

**解決方法:**
- PowerShell を管理者として実行
- または、各コマンドの実行時に UAC ダイアログで承認

### 推奨事項

1. **定期的なアップデート**
   ```powershell
   npm update -g @anthropic-ai/claude-code
   ```

2. **アンインストール方法**
   ```powershell
   npm uninstall -g @anthropic-ai/claude-code
   ```

## バージョン情報

- **Claude Code 最新バージョン:** 1.0.31（2025年6月21日リリース）
- **Windows ネイティブサポート:** バージョン 0.51 以降

## 参考リンク

- [元記事（INTERNET Watch）](https://forest.watch.impress.co.jp/docs/news/2030822.html)
- [Anthropic 公式サイト](https://www.anthropic.com/)

---

最終更新日: 2025年7月29日