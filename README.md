# astro-sandbox

天体に関するいろいろな計算を、趣味で試して残しておくためのリポジトリです。
計算の種類ごとにディレクトリを分け、主に Google Colab 上のノートブックで動かすことを想定しています。

## ディレクトリ構成

| ディレクトリ | 内容 |
| --- | --- |
| [`distance/`](distance/) | 天体までの距離を、いくつかの方法で求める |

他の種類の計算(例: 軌道、明るさ、時刻・座標変換など)は、今後ディレクトリを追加していく予定です。

## Google Colab での使い方

ノートブック(`.ipynb`)は GitHub 上のファイルを Colab で直接開けます。

```
https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/<ディレクトリ>/<ノートブック名>.ipynb
```

各ディレクトリの README に、ノートブックごとの「Open in Colab」バッジを置く想定です。

```markdown
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/distance/xxx.ipynb)
```

Colab で編集した内容は「ファイル > GitHub にコピーを保存」でこのリポジトリに保存できます。

## 方針

- 1 つの計算方法につき 1 ノートブックを基本にする
- 使った式・定数・出典は、ノートブックか README に書いておく
- ディレクトリを追加したら、上の表にも追記する
