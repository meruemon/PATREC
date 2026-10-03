# パターン認識特論 2026 ノートブック演習

関西大学大学院「パターン認識特論」の演習用 Jupyter ノートブックです．
講義スライドの式を NumPy でそのまま動かし，数値で確かめます．
ノートブックは講義の進捗にあわせて，このレポジトリに順次追加します．

## 公開状況

| 回 | テーマ | ノートブック | 状態 |
|---|---|---|---|
| 1 | パターン認識とニューラルネットワーク | （演習なし） | － |
| 2 | ニューラルネットワークの基礎アーキテクチャ | [第02回_演習.ipynb](第02回_演習.ipynb) | 公開 |
| 3 | 誤差逆伝播法とニューラルネットワークの訓練 | [第03回_演習.ipynb](第03回_演習.ipynb) | 公開 |
| 4 以降 | | | 講義後に追加 |

## 1．準備（初回のみ）

### 1.1 Anaconda のインストール

[Anaconda Distribution](https://www.anaconda.com/download) をインストールします．
Miniconda や Miniforge でも同じ手順で動きます．

以降のコマンドは次の画面で実行します．

- Windows：スタートメニューの **Anaconda Prompt**
- macOS／Linux：ターミナル

### 1.2 レポジトリの取得

Git を使う場合（推奨．後の更新が1コマンドで済みます）：

```bash
git clone https://github.com/<ユーザ名>/<レポジトリ名>.git
cd <レポジトリ名>
```

Git を使わない場合は，GitHub のページで **Code → Download ZIP** を選び，展開したフォルダへ `cd` で移動します．

### 1.3 conda 環境の作成

`environment.yml` のあるフォルダで実行します．数分かかります．

```bash
conda env create -f environment.yml
```

`patrec2026` という名前の環境ができます．確認：

```bash
conda env list
```

## 2．ノートブックの実行（毎回）

```bash
conda activate patrec
jupyter lab
```

ブラウザが開くので，左のファイル一覧から該当回の `.ipynb` を開きます．
セルは **Shift + Enter** で上から順に実行します．
終了するときは，ターミナルで **Ctrl + C** を押します．

VS Code を使う場合は，`.ipynb` を開いて右上の「カーネルの選択」から `patrec` を選びます．

## 3．講義ごとの更新

新しい回のノートブックは講義後に追加します．講義の前に最新版を取得してください．

```bash
git pull
```

ZIP で取得した人は，もう一度 ZIP をダウンロードします．

自分で書き換えたノートブックがあると `git pull` が失敗することがあります．
演習の前に，配布されたファイルをコピーしてから編集すると安全です
（例：`第02回_演習.ipynb` → `第02回_演習_自分用.ipynb`）．

`environment.yml` が更新されたとき（この README で告知します）は，環境も更新します．

```bash
conda env update -f environment.yml --prune
```

## 4．環境の内容

| パッケージ | 用途 |
|---|---|
| Python 3.12 | |
| NumPy，Matplotlib | 全回で使用 |
| JupyterLab，Notebook | ノートブックの実行 |
| PyTorch，torchvision（CPU 版） | 各回の「任意」の節と，後半の回で使用 |

第2回・第3回は NumPy と Matplotlib だけで動きます．PyTorch の節は読み飛ばしても支障ありません．

GPU 版の PyTorch を使いたい場合は，環境を作った後に [PyTorch 公式の手順](https://pytorch.org/get-started/locally/) に従って入れ直してください．講義の演習は CPU で数秒〜数十秒で終わるように作っています．

## 5．ノートブックの使い方

- 各節の最後に **やってみよう** があります．`# TODO` の行を書き換えて実行します．
- 直後に **解答** セルがあります．先に自分で試してから見てください．
- 冒頭の表に，対応するスライドのページを載せています．

## 6．うまくいかないとき

| 症状 | 対処 |
|---|---|
| `conda` が見つからない | Anaconda Prompt（Windows）で実行しているか確認する．macOS／Linux は `conda init` の後にターミナルを開き直す |
| 環境の作成が終わらない・失敗する | `conda update -n base conda` の後にやり直す．学内ネットワークではプロキシ設定が必要な場合がある |
| 作り直したい | `conda env remove -n patrec2026` の後に 1.3 をやり直す |
| `ModuleNotFoundError` | `conda activate patrec2026` を忘れていないか確認する．VS Code はカーネルが `patrec2026` か確認する |
| 図の日本語が □ になる | 図のラベルは英語にしてあるので通常は起きない．自分で日本語を入れる場合は `pip install japanize-matplotlib` の後に `import japanize_matplotlib` を追加する |
| 結果がおかしい | メニューの **Kernel → Restart Kernel and Run All Cells** で最初から実行し直す |

解決しない場合は，エラーメッセージの全文を添えて担当教員に連絡してください．

## 7．利用について

本レポジトリの教材は，上記講義の受講者の学習用に公開しています．
