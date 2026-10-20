# cosmology — 宇宙の膨張と赤方偏移

[`distance/`](../distance/) で求めた天体の距離を使って、宇宙の膨張の速さや歴史、赤方偏移について調べるディレクトリです。
方法ごとにノートブックを分け、Google Colab で実行できるようにしていきます。

## テーマ一覧

| テーマ | 概要 | ノートブック |
| --- | --- | --- |
| 膨張の歴史を当てはめる | 超新星のハッブル図に Ωm・ΩΛ・w を当てはめ、加速に転じた時期や宇宙年齢を求める | [sn_cosmology_fit.ipynb](sn_cosmology_fit.ipynb) |
| 膨張速度 H(z) を手法ごとに比較 | 宇宙クロノメーター・BAO・超新星で測った H(z) を重ねる | [hz_comparison.ipynb](hz_comparison.ipynb) |
| ハッブル・テンションの比較 | セファイド・TRGB・CMB など、手法ごとの H₀ を並べる | [hubble_tension.ipynb](hubble_tension.ipynb) |
| 赤方偏移を自分で測る | SDSS の銀河スペクトルの輝線から z を測る | [measure_redshift.ipynb](measure_redshift.ipynb) |
| 赤方偏移の種類を比べる | zHEL・zCMB・zHD の違い、固有運動、ドップラーと宇宙論的赤方偏移 | [redshift_types.ipynb](redshift_types.ipynb) |
| 「距離」の定義の違い | 光度距離・角径距離・共動距離・光行距離を比べる | [cosmic_distances.ipynb](cosmic_distances.ipynb) |

## ノートブック一覧

### [Ia 型超新星で宇宙の膨張の歴史を当てはめる](sn_cosmology_fit.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/cosmology/sn_cosmology_fit.ipynb)

- Pantheon+ の超新星と、統計誤差+系統誤差の共分散行列を使って χ² を計算
- 平坦 ΛCDM の Ωm(実行すると約 0.33)、曲率ありの Ωm–ΩΛ 平面、平坦 wCDM の w(約 −0.9)を格子で求める
- 同じ当てはめとセファイド較正の M_B から H₀(約 73 km/s/Mpc)
- 減速パラメータ q(z)、加速に転じた赤方偏移(z ≈ 0.6、約 50 億年前)、膨張の速さ da/dt、宇宙年齢
- データ: Pantheon+ / SH0ES の公開データ(GitHub。ライセンスの明記はなく、論文を引用して利用)

### [宇宙の膨張速度 H(z) を 3 つの方法で測って比べる](hz_comparison.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/cosmology/hz_comparison.ipynb)

- 宇宙クロノメーター(銀河の年齢差)で H(z) を直接測り、系統誤差の共分散も入れて H₀ ≈ 66 ± 6 を求める
- DESI DR2 の BAO から Ωm ≈ 0.298 と H₀r_d を求め、r_d に CMB の値を使うと H₀ ≈ 69
- 超新星から、ΛCDM を仮定せずに H(z)/H₀ を折れ線で推定
- 3 つを重ねると、膨張の歴史の形はそろうが、H₀ の絶対値は物差しによって 67〜69 と 73 に分かれる(ハッブル・テンション)
- データ: Moresco の宇宙クロノメーター(GitLab)、DESI DR2 BAO(Cobaya の bao_data)、Pantheon+。いずれもライセンスの明記はなく、論文を引用して利用

### [ハッブル・テンション: 方法ごとの H₀ を並べて比べる](hubble_tension.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/cosmology/hubble_tension.ipynb)

- CMB・BAO・セファイド・TRGB・重力レンズ・重力波などで発表された H₀ を並べ、食い違いが何σかを計算
- CMB を使わず、DESI BAO とビッグバン元素合成(BBN)の ω_b だけから H₀ ≈ 68.5 を求める
- テンションを消すのに必要な r_d(約 6% 小さい)と LMC の距離(約 8% 遠い)を計算。cepheid.ipynb の自分の LMC 距離も入れられる
- 超新星を赤方偏移で分けて H₀ を出し、近くだけ速く膨張しているわけではないことを確認
- データ: 各論文の H₀(出典はノートブックに記載)、DESI DR2 BAO、Pantheon+

### [銀河のスペクトルから赤方偏移を自分で測る](measure_redshift.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/cosmology/measure_redshift.ipynb)

- SDSS DR17 から、z = 0.01〜0.6 の銀河のスペクトルを取ってくる
- 輝線・吸収線のリストを z だけ伸ばした型紙との相互相関で、おおよその z を探す
- 1 本ずつガウス関数を当てはめて z を精密に決め、どの線も同じ倍率 1+z で伸びていることを確かめる
- SDSS のパイプラインの z と比べる(輝線銀河で数十 km/s 以内、吸収線だけの銀河で 100 km/s 程度)
- データ: SDSS DR17(自由に利用可。SDSS への謝辞と論文を引用)

### [赤方偏移の「種類」を比べる](redshift_types.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/cosmology/redshift_types.ipynb)

- Pantheon+ の zHEL と zCMB の差から、太陽系が CMB に対して動く速さ(約 370 km/s)と向きを求める
- zCMB → zHD の固有運動補正と、近くの超新星では固有運動が距離の誤差になること(z > 0.023 を使う理由)
- 近くの銀河の速度と距離。アンドロメダ銀河の青方偏移から、タイミング論法で局所銀河群の質量(約 4 × 10¹² 太陽質量)を見積もる
- 赤方偏移をドップラー効果と見た速度と、空間の膨張と見た遠ざかる速さ(z ≈ 1.5 で光速を超える)を比べる
- 地球の自転から宇宙膨張まで、赤方偏移を生む効果の大きさを並べる
- データ: Pantheon+、近くの銀河の値は NED などのおおよその値

### [宇宙論の「距離」はいくつもある](cosmic_distances.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/coxless/astro-sandbox/blob/main/cosmology/cosmic_distances.ipynb)

- 光度距離・共動距離・角径距離・光行距離を z の関数として比べる(z ≈ 0.01 で 1%、z > 1 では何倍も違う)
- 角径距離は z ≈ 1.6 で最大になり、それより遠い天体は大きく見えてくる。CMB の音響ピークの角度 0.596° を再現
- 「135 億年前の光」の銀河(JADES-GS-z14-0)が今どこにいるか、観測できる宇宙の半径(約 460 億光年)
- 距離双対性 d_L = (1+z)² D_A を、Pantheon+ の超新星と DESI の BAO で確かめる
- データ: astropy の Planck18、Pantheon+、DESI DR2 BAO

## 式のメモ

- フリードマン方程式: $H(z)^2 = H_0^2 \left[\Omega_m (1+z)^3 + \Omega_k (1+z)^2 + \Omega_{\mathrm{DE}} (1+z)^{3(1+w)}\right]$
- 光度距離(平坦): $d_L = (1+z)\, c \displaystyle\int_0^z \frac{dz'}{H(z')}$
- 減速パラメータ: $q = -\ddot{a}a/\dot{a}^2$、平坦 ΛCDM で $q_0 = \Omega_m/2 - \Omega_\Lambda$
- ハッブル時間: $1/H_0 = 977.8 / (H_0\,[\mathrm{km/s/Mpc}])$ Gyr
