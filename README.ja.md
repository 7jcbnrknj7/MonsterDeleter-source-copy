[简体中文](README.md) | [日本語](README.ja.md) | [English](README.en.md)

# 🦖 大将怪獣デリーター · Desktop Monster Deleter

所有者が GitHub を初めて使った際に保存したソースコードのコピーです。出典：[531149627/MonsterDeleter](https://github.com/531149627/MonsterDeleter)。

Windows のデスクトップアプリです。怪獣を呼び出し、ファイルの近くまで歩いて蹴り飛ばす様子をアニメーションと効果音で演出します。実際の削除は `send2trash` による Windows のごみ箱への移動で、ごみ箱から復元できます。完全消去ではありません。

## 主な機能

- 半透明の照準画面と赤い十字カーソル。
- 登場、歩行、指さし、キック、爆発、飛び去る動作のコマアニメーションと透過素材。
- BGM、怪獣の音声、爆発音。
- 初回起動時に、現在の Windows ユーザー用のファイル右クリックメニュー「召唤大将怪兽摧毁」を登録。
- 右クリックメニューから対象パスを受け取り、画面上で演出位置を選択。

## パッケージ版の使い方

このリポジトリはソースと素材を提供しており、ビルド済みの `MonsterDeleter.exe` は含みません。別途入手、または自分でビルドした場合：

1. 一度起動して右クリックメニューを登録します。照準画面が表示されたら `Esc` キーか終了操作で閉じます。
2. 対象ファイルを右クリックして「召唤大将怪兽摧毁」を選び、暗くなった画面の赤い照準で演出位置を指定し、画面の案内に従います。

ごみ箱に移す対象は、メニューから渡されたファイルパスで決まります。`python main.py` のみでは手動デモを開き、対象ファイルが渡されていない場合はごみ箱への移動を実行できません。

## ソースから実行

Windows と Python 3 が必要です。現在のコードは PyQt6 を読み込み、send2trash を使ってファイルをごみ箱に移します。このコピーには `requirements.txt` がないため、次の依存パッケージをインストールします。

```powershell
python -m pip install PyQt6 send2trash
python main.py
python main.py "C:\path\to\your\file.txt"
```

2 行目は手動デモ、3 行目は対象ファイルを渡す実行例です。画面、音声、右クリックメニューの互換性は利用する PC で確認してください。

## パッケージ化の参考

PyInstaller をインストールし、リポジトリのルートで実行します。

```powershell
python -m pip install pyinstaller
pyinstaller --noconfirm --onefile --windowed --name MonsterDeleter --add-data "assets;assets" --hidden-import send2trash main.py
```

出力は `dist/MonsterDeleter.exe` です。単一ファイル形式では、展開された `sys._MEIPASS` 内の素材を読み込みます。このコマンドは参考手順であり、すべての Windows 環境での検証済み動作を示すものではありません。

## ファイル構成

| パス | 内容 |
| --- | --- |
| `main.py` | 画面、アニメーション、音声、メニュー登録、ごみ箱への移動 |
| `register_menu.py` | 独立したメニュー登録スクリプト |
| `assets/` | 画像、アニメーションフレーム、音声 |

旧説明にあった `requirements.txt`、`scripts/`、`tests/` は、このコピーには含まれていません。

## 出典と利用許諾

娯楽と学習を目的としたプロジェクトです。元のプロジェクトと各素材の許諾を確認してください。このコピーの説明は、追加の再配布権や商用利用権を与えるものではありません。
