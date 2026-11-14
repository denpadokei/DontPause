# DontPause

[![Build and Release](https://github.com/denpadokei/DontPause/actions/workflows/build-and-release.yml/badge.svg)](https://github.com/denpadokei/DontPause/actions/workflows/build-and-release.yml)

HMD を外したり、コントローラの接続が切れたりしても曲を止めずに続行する MOD です。

## 機能

- `PauseController.HandleHMDUnmounted` を無効化し、HMD を外しても自動ポーズしない
- `PauseController.HandleInputFocusWasCaptured` を無効化し、フォーカスが外れても自動ポーズしない
- `PauseController.HandleControllersDidDisconnectEvent` を無効化し、コントローラの切断で自動ポーズしない
- 上記 3 メソッドを `HarmonyTargetMethods` でまとめて対象にし、Prefix で元の処理を止める
- プラグインの無効化時にパッチを解除する

## 動作環境

| 項目 | 内容 |
| --- | --- |
| Beat Saber | 1.34.0 |
| 依存 MOD | BSIPA ^4.2.0 |

## インストール

1. Beat Saber を 1.34.0 に合わせる (BSManager などのバージョン管理ツールを推奨)
2. BSIPA と上記の依存 MOD をインストールする
3. [Releases](https://github.com/denpadokei/DontPause/releases) から `DontPause-0.0.3-bs1.34.0.zip` をダウンロードし、`Plugins` フォルダをゲームフォルダへ上書きコピーする

## 使い方

ゲーム内に UI や設定はありません。自動ポーズだけが無効になり、ポーズメニューを開くなどの手動のポーズは通常どおり動作します。

## ビルド

```powershell
git clone https://github.com/denpadokei/DontPause.git
cd DontPause
dotnet build .\DontPause\DontPause.csproj -c Release
```

`BeatSaberDir` (または `GameDirectory`) に Beat Saber のインストール先を設定すると、ゲームの参照アセンブリを解決できます。

GitHub Actions の `build-and-release.yml` が push ごとにビルドし、`X.X.X` 形式のタグを push するとリリースを作成します。

## ライセンス

ライセンスファイルはありません。
