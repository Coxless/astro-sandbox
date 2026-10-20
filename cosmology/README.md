# cosmology — 宇宙の膨張と赤方偏移

[`distance/`](../distance/) で求めた天体の距離を使って、宇宙の膨張の速さや歴史、赤方偏移について調べるディレクトリです。
方法ごとにノートブックを分け、Google Colab で実行できるようにしていきます。

## 予定しているテーマ

| テーマ | 概要 | ノートブック |
| --- | --- | --- |
| 膨張の歴史を当てはめる | 超新星のハッブル図に Ωm・ΩΛ・w を当てはめ、加速に転じた時期や宇宙年齢を求める | [sn_cosmology_fit.ipynb](sn_cosmology_fit.ipynb) |
| 膨張速度 H(z) を手法ごとに比較 | 宇宙クロノメーター・BAO・超新星で測った H(z) を重ねる | (予定) |
| ハッブル・テンションの比較 | セファイド・TRGB・CMB など、手法ごとの H₀ を並べる | (予定) |
| 赤方偏移を自分で測る | SDSS の銀河スペクトルの輝線から z を測る | (予定) |
| 赤方偏移の種類を比べる | zHEL・zCMB・zHD の違い、固有運動、ドップラーと宇宙論的赤方偏移 | (予定) |
| 「距離」の定義の違い | 光度距離・角径距離・共動距離・光行距離を比べる | (予定) |

## ノートブック一覧

### [Ia 型超新星で宇宙の膨張の歴史を当てはめる](sn_cosmology_fit.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/cosmology/sn_cosmology_fit.ipynb)

- Pantheon+ の超新星と、統計誤差+系統誤差の共分散行列を使って χ² を計算
- 平坦 ΛCDM の Ωm(実行すると約 0.33)、曲率ありの Ωm–ΩΛ 平面、平坦 wCDM の w(約 −0.9)を格子で求める
- 同じ当てはめとセファイド較正の M_B から H₀(約 73 km/s/Mpc)
- 減速パラメータ q(z)、加速に転じた赤方偏移(z ≈ 0.6、約 50 億年前)、膨張の速さ da/dt、宇宙年齢
- データ: Pantheon+ / SH0ES の公開データ(GitHub。ライセンスの明記はなく、論文を引用して利用)

## 式のメモ

- フリードマン方程式: $H(z)^2 = H_0^2 \left[\Omega_m (1+z)^3 + \Omega_k (1+z)^2 + \Omega_{\mathrm{DE}} (1+z)^{3(1+w)}\right]$
- 光度距離(平坦): $d_L = (1+z)\, c \displaystyle\int_0^z \frac{dz'}{H(z')}$
- 減速パラメータ: $q = -\ddot{a}a/\dot{a}^2$、平坦 ΛCDM で $q_0 = \Omega_m/2 - \Omega_\Lambda$
- ハッブル時間: $1/H_0 = 977.8 / (H_0\,[\mathrm{km/s/Mpc}])$ Gyr
