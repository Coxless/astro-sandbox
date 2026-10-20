# distance — 天体の距離計算

天体までの距離を、いろいろな方法で求めてみるディレクトリです。
方法ごとにノートブックを分け、Google Colab で実行できるようにしていきます。

## 予定している方法

| 方法 | 主な対象 | 概要 | ノートブック |
| --- | --- | --- | --- |
| 年周視差 | 近くの恒星 | 視差 p [秒角] から d [pc] = 1 / p | [parallax.ipynb](parallax.ipynb) |
| 距離指数・主系列フィッティング | 星団 | m − M = 5 log₁₀(d / 10 pc) | [distance_modulus.ipynb](distance_modulus.ipynb) |
| セファイド変光星 | 近傍銀河 | 周期−光度関係で M を求め、距離指数へ | [cepheid.ipynb](cepheid.ipynb) |
| Ia 型超新星・ハッブル=ルメートルの法則 | 遠方銀河 | 最大光度の標準化で距離指数へ、v = H₀ d で H₀ を推定 | [sn_ia_hubble.ipynb](sn_ia_hubble.ipynb) |

順番や対象は試しながら変えていきます。

## ノートブック一覧

ノートブックを追加したら、ここに Colab バッジ付きで並べます。

### [年周視差](parallax.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/distance/parallax.ipynb)

- 有名な近傍星(プロキシマ・ケンタウリなど)の視差を Gaia DR3 から取得し、`1/p` で距離を計算
- 視差誤差が大きいと `1/p` が偏る様子をシミュレーションで確認
- ランダムな Gaia の星で、`1/p` と Bailer-Jones et al. (2021) のベイズ推定距離を比較
- データ: Gaia DR3、Bailer-Jones et al. (2021) の距離カタログ、SIMBAD(すべてオープン)

### [距離指数・主系列フィッティング](distance_modulus.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/distance/distance_modulus.ipynb)

- 50 pc 以内の星で HR 図を描き、主系列の「色 → 絶対等級」の関係を多項式で当てはめ
- 固有運動でプレアデス星団の星を選び、主系列を重ねて距離指数を求める
- 同じ星の Gaia 視差による距離と比べて答え合わせ
- データ: Gaia DR3(オープン)

### [セファイド変光星](cepheid.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/distance/cepheid.ipynb)

- Gaia DR3 の古典的セファイド(基本振動)を取得し、減光の影響を打ち消すヴェーゼンハイト等級を使う
- 視差のよい天の川銀河のセファイドで周期−光度関係を較正
- 大マゼラン雲(LMC)のセファイドに当てはめて LMC までの距離を求め、食連星による精密な値と比べる
- データ: Gaia DR3(オープン)

### [Ia 型超新星とハッブル図](sn_ia_hubble.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/distance/sn_ia_hubble.ipynb)

- セファイドで距離が分かっている銀河の超新星で、超新星の絶対等級 M_B を較正
- 0.023 < z < 0.15 の超新星からハッブル定数 H₀ を推定(実行すると約 73 km/s/Mpc)
- z ≈ 2 までのハッブル図で、宇宙の加速膨張を確認
- データ: Pantheon+ / SH0ES の公開データ(GitHub。ライセンスの明記はなく、論文を引用して利用)

## 距離はしごのつながり

```
年周視差 ──→ 主系列フィッティング(星団)
   │
   └──→ セファイド変光星(LMC・近傍銀河)──→ Ia 型超新星 ──→ ハッブル定数
```

## 単位メモ

- 1 pc(パーセク)≈ 3.2616 光年 ≈ 3.0857 × 10¹⁶ m
- 1 au(天文単位)= 1.495978707 × 10¹¹ m
- 1 光年 ≈ 9.4607 × 10¹⁵ m
