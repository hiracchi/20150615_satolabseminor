---

# ProteinDF software packages

2015.06.15
平野 敏行

---

## 量子化学シミュレーションの概要

![QM simlation scheme](./data/QM_simulation_scheme.png "QM simulation scheme")

--

## ProteinDF software packages の概要

* [site](http://proteindf.github.io/)
* Software
  * ProteinDF
  * ProteinDF_bridge
  * ProteinDF_pytools
  * QCLObot

---

# ProteinDF の使い方

2015.06.15
平野 敏行

---

## ProteinDF の概要

* 大規模分子系のカノニカル分子軌道計算が可能な  
  量子化学(QM)計算プログラム
* 第三世代密度汎関数計算法を実装
* C++で記述
* MPI/OpenMP ハイブリッド並列

---

## インストール

+ [git](https://github.com/ProteinDF/ProteinDF)からソースを取得する
+ bootstrap.sh を実行する
  * 今後この手順は無くす予定
+ configureを実行し、Makefileを作成する
+ make && make install を実行する

---

## 実行

* 環境変数**PDF_HOME**を  
  インストールディレクトリに指定する
* 入力ファイル(デフォルト: fl_Userinput)を用意
* 作業用ディレクトリ(デフォルト: fl_Work)を用意
* 実行
  * シリアル版(OpenMPスレッド並列)

```
${PDF_HOME}/bin/PDF.x
```

* MPI並列版

```
mpirun -n ${NCPU} ${PDF_HOME}/bin/PPDF.x
```

---

## キーワード

* ほとんどのキーワードは  
  出力ファイル(デフォルト: fl_Out_Std)に  
  記載されている

```
[0:2015/06/09 11:27:45:INFO]  >>>> Input Parameters <<<<
[0:2015/06/09 11:27:45:INFO]   1:  pdf_param_path [pdfparam.mpac]
[0:2015/06/09 11:27:45:INFO]   2:  step_control [create integral guess scf]
[0:2015/06/09 11:27:45:INFO]   3:  comment []
[0:2015/06/09 11:27:45:INFO]   4:  linear_algebra_package [lapack]
[0:2015/06/09 11:27:45:INFO]   5:  scalapack_block_size [64]
[0:2015/06/09 11:27:45:INFO]   6:  save_distributed_matrix_to_local_disk [no]
[0:2015/06/09 11:27:45:INFO]   7:  local_disk_path [/tmp]
[0:2015/06/09 11:27:45:INFO]   8:  memory_size [1GB]
[0:2015/06/09 11:27:45:INFO]   9:  use_mapfile [no]
[0:2015/06/09 11:27:45:INFO]  10:  mapfile_size [auto]
[0:2015/06/09 11:27:45:INFO]  11:  mapfile_basename [pdf]
[0:2015/06/09 11:27:45:INFO]  12:  work_on_disk [no]
[0:2015/06/09 11:27:45:INFO]  13:  parallel_processing_type [divide_and_conquer]
[0:2015/06/09 11:27:45:INFO]  14:  cleanup [no]
[0:2015/06/09 11:27:45:INFO]  15:  show_keyword [no]
[0:2015/06/09 11:27:45:INFO]  16:  show_input [yes]
[0:2015/06/09 11:27:45:INFO]  17:  show_coordinates [yes]
[0:2015/06/09 11:27:45:INFO]  18:  show_orbital_basis [gamess]
[0:2015/06/09 11:27:45:INFO]  19:  guess [harris]
[0:2015/06/09 11:27:45:INFO]  20:  guess/normalize_density_matrix [true]
[0:2015/06/09 11:27:45:INFO]  21:  cut-value [1.0e-10]
[0:2015/06/09 11:27:45:INFO]  22:  block-size [1024000]
[0:2015/06/09 11:27:45:INFO]  23:  charge-extrapolate-number [1]
[0:2015/06/09 11:27:45:INFO]  24:  orbital-overlap-correspondence [off]
[0:2015/06/09 11:27:45:INFO]  25:  orbital-overlap-correspondence-first [off]
[0:2015/06/09 11:27:45:INFO]  26:  orbital-overlap-correspondence-method [mo-overlap]
[0:2015/06/09 11:27:45:INFO]  27:  orbital-overlap-correspondence-number [3]
[0:2015/06/09 11:27:45:INFO]  28:  summary [none]
[0:2015/06/09 11:27:45:INFO]  29:  analyze_population [none]
[0:2015/06/09 11:27:45:INFO]  30:  max_iteration [100]
[0:2015/06/09 11:27:45:INFO]  31:  method [rks]
[0:2015/06/09 11:27:45:INFO]  32:  method/rks/occlevel [ 1 - 7 ]
[0:2015/06/09 11:27:45:INFO]  33:  method/rks/electrons [14]
[0:2015/06/09 11:27:45:INFO]  34:  method/uks/alpha_occlevel []
[0:2015/06/09 11:27:45:INFO]  35:  method/uks/alpha_electrons []
[0:2015/06/09 11:27:45:INFO]  36:  method/uks/beta_occlevel []
[0:2015/06/09 11:27:45:INFO]  37:  method/uks/beta_electrons []
[0:2015/06/09 11:27:45:INFO]  38:  method/roks/closed_occlevel []
[0:2015/06/09 11:27:45:INFO]  39:  method/roks/closed_electrons []
[0:2015/06/09 11:27:45:INFO]  40:  method/roks/open_occlevel []
[0:2015/06/09 11:27:45:INFO]  41:  method/roks/open_electrons []
[0:2015/06/09 11:27:45:INFO]  42:  save_diff_density_matrix [yes]
[0:2015/06/09 11:27:45:INFO]  43:  use_matrix_cache [yes]
[0:2015/06/09 11:27:45:INFO]  44:  force_loading_from_disk [yes]
[0:2015/06/09 11:27:45:INFO]  45:  show_cache_report [no]
[0:2015/06/09 11:27:45:INFO]  46:  disk-utilization [no]
[0:2015/06/09 11:27:45:INFO]  47:  update_method [yes]
[0:2015/06/09 11:27:45:INFO]  48:  orbital_independence_threshold [0.007]
[0:2015/06/09 11:27:45:INFO]  49:  orbital_independence_threshold/canonical [0.007]
[0:2015/06/09 11:27:45:INFO]  50:  orbital_independence_threshold/lowdin [0.007]
[0:2015/06/09 11:27:45:INFO]  51:  XMatrix/save_eigval [true]
[0:2015/06/09 11:27:45:INFO]  52:  convergence/type [density]
[0:2015/06/09 11:27:45:INFO]  53:  convergence/threshold [1e-4]
[0:2015/06/09 11:27:45:INFO]  54:  convergence/threshold-energy []
[0:2015/06/09 11:27:45:INFO]  55:  scf_acceleration [damping]
[0:2015/06/09 11:27:45:INFO]  56:  scf_acceleration/damping/damping_factor [0.67]
[0:2015/06/09 11:27:45:INFO]  57:  scf_acceleration/daming/start_number [0]
[0:2015/06/09 11:27:45:INFO]  58:  scf_acceleration/damping/damping_type [density_matrix]
[0:2015/06/09 11:27:45:INFO]  59:  scf_acceleration/anderson/damping_factor [0.50]
[0:2015/06/09 11:27:45:INFO]  60:  scf_acceleration/anderson/start_number [3]
[0:2015/06/09 11:27:45:INFO]  61:  level_shift [no]
[0:2015/06/09 11:27:45:INFO]  62:  level_shift/start_iteration [1]
[0:2015/06/09 11:27:45:INFO]  63:  level_shift/closed_mo [0.00]
[0:2015/06/09 11:27:45:INFO]  64:  level_shift/open_mo [0.00]
[0:2015/06/09 11:27:45:INFO]  65:  level_shift/virtual_mo [0.00]
[0:2015/06/09 11:27:45:INFO]  66:  scf_acceleration/diis/number_of_diis [3]
[0:2015/06/09 11:27:45:INFO]  67:  scf_acceleration/diis/start_number [3]
[0:2015/06/09 11:27:45:INFO]  68:  scf_acceleration/diis/start_extrapolation [6]
[0:2015/06/09 11:27:45:INFO]  69:  xc_functional [HF]
[0:2015/06/09 11:27:45:INFO]  70:  grid_free [false]
[0:2015/06/09 11:27:45:INFO]  71:  xc-potential/grid-type [sg-1]
[0:2015/06/09 11:27:45:INFO]  72:  xc-update [yes]
[0:2015/06/09 11:27:45:INFO]  73:  xc-density-threshold [1.0E-16]
[0:2015/06/09 11:27:45:INFO]  74:  TEI-integral-driven [yes]
[0:2015/06/09 11:27:45:INFO]  75:  J_engine [CD]
[0:2015/06/09 11:27:45:INFO]  76:  K_engine [CD]
[0:2015/06/09 11:27:45:INFO]  77:  XC_engine [gridfree_CD]
[0:2015/06/09 11:27:45:INFO]  78:  CDAM_tau [1.0E-16]
[0:2015/06/09 11:27:45:INFO]  79:  CD_epsilon [1.0E-10]
[0:2015/06/09 11:27:45:INFO]  80:  gridfree/orthogonalize_method [canonical]
[0:2015/06/09 11:27:45:INFO]  81:  gridfree/dedicated_basis [no]
[0:2015/06/09 11:27:45:INFO]  82:  gridfree/save_v_eigval [true]
[0:2015/06/09 11:27:45:INFO]  83:  scf-memory-saving [yes]
[0:2015/06/09 11:27:45:INFO]  84:  geometry/cartesian/input []
[0:2015/06/09 11:27:45:INFO]  85:  geometry/cartesian/unit [angstrom]
[0:2015/06/09 11:27:45:INFO]  86:  basis-set/orbital []
[0:2015/06/09 11:27:45:INFO]  87:  basis-set/density-auxiliary [s]
[0:2015/06/09 11:27:45:INFO]  88:  basis-set/exchange-auxiliary []
[0:2015/06/09 11:27:45:INFO]  89:  basis-set/gridfree []
[0:2015/06/09 11:27:45:INFO]  90:  xc_density_threshold [1.0E-16]
[0:2015/06/09 11:27:45:INFO]  91:  geometry [cartesian]
[0:2015/06/09 11:27:45:INFO]  92:  coordinates []
[0:2015/06/09 11:27:45:INFO]  93:  basis_set []
[0:2015/06/09 11:27:45:INFO]  94:  basis_set_j []
[0:2015/06/09 11:27:45:INFO]  95:  basis_set_xc []
[0:2015/06/09 11:27:45:INFO]  96:  basis_set_gridfree []
[0:2015/06/09 11:27:45:INFO]  97:  independent-orbital-number [0]
[0:2015/06/09 11:27:45:INFO]  98:  xc-potential/gxalpha/alpha-value [0.7]
[0:2015/06/09 11:27:45:INFO]  99:  myu-nyu-zero [no]
[0:2015/06/09 11:27:45:INFO]  100:  guess/nsp-ppq [nil]
[0:2015/06/09 11:27:45:INFO]  101:  guess/sp-ppq [nil]
[0:2015/06/09 11:27:45:INFO]  102:  guess/trans-angle-threshold [1.0 1.5 20 30]
[0:2015/06/09 11:27:45:INFO]  103:  guess/make-myu-nyu [meth0]
[0:2015/06/09 11:27:45:INFO]  104:  guess/vct-normalize [ON OFF OFF]
[0:2015/06/09 11:27:45:INFO]  105:  guess/part-normalize [nil]
[0:2015/06/09 11:27:45:INFO]  106:  guess/user-vector [nil]
[0:2015/06/09 11:27:45:INFO]  107:  num_of_atoms [2]
[0:2015/06/09 11:27:45:INFO]  108:  num_of_dummy_atoms [0]
[0:2015/06/09 11:27:45:INFO]  109:  num_of_AOs [10]
[0:2015/06/09 11:27:45:INFO]  110:  num_of_MOs [0]
[0:2015/06/09 11:27:45:INFO]  111:  num_of_auxCDs [24]
[0:2015/06/09 11:27:45:INFO]  112:  num_of_auxXCs [24]
[0:2015/06/09 11:27:45:INFO]  113:  TE []
[0:2015/06/09 11:27:45:INFO]  114:  debug/file_warning [yes]
[0:2015/06/09 11:27:45:INFO]  115:  debug/save_J [no]
[0:2015/06/09 11:27:45:INFO]  116:  debug/save_K [no]
[0:2015/06/09 11:27:45:INFO]  117:  debug/save_Fxc_pure [no]
[0:2015/06/09 11:27:45:INFO]  118:  debug/save_forces [no]
[0:2015/06/09 11:27:45:INFO]  119:  cutoff_distribution []
[0:2015/06/09 11:27:45:INFO]  120:  length_scale_parameter [1]
[0:2015/06/09 11:27:45:INFO]  121:  control []
[0:2015/06/09 11:27:45:INFO]  122:  debug/eri/exact_J []
[0:2015/06/09 11:27:45:INFO]  123:  cutoff_density []
[0:2015/06/09 11:27:45:INFO]  124:  cutoff_epsilon3 []
[0:2015/06/09 11:27:45:INFO]  125:  debug/eri/exact_K []
[0:2015/06/09 11:27:45:INFO]  126:  new_engine [true]
[0:2015/06/09 11:27:45:INFO]  127:  debug/eri/output_K []
[0:2015/06/09 11:27:45:INFO]  128:  debug/eri/output_J []
[0:2015/06/09 11:27:45:INFO]  129:  num_of_iterations [0]
[0:2015/06/09 11:27:45:INFO]  130:  stat []
```

---

### ProteinDF ツール

* C++で作成されたツール
  * 計算効率が要求される解析ツール
  * Pythonのツール群はpytoolsへ
* ツールの名前はpdf-*で統一
  * pdf [sub-command] が使えるように
    * cf.) git

--

### ProteinDF ツール一覧(1)

|ツール|内容|
|:-----|:---|
|pdf-pop-mulliken|Mulliken Populationを計算|
|pdf-mkfld-mo|分子軌道を計算、ボリュームデータを出力|
|pdf-mkfld-dens|電子密度を計算、ボリュームデータを出力|
|pdf-mkfld-esp|静電ポテンシャルを計算、ボリュームデータを出力|

--

### ProteinDF ツール一覧(2)

|ツール|内容|
|:-----|:---|
|pdf-localize|局在化軌道を計算|
|pdf-component|分子軌道に寄与するを原子軌道を出力|
|pdf-rotate-lcao|LCAO行列を回転操作|
|pdf-trans-densmat|密度行列の基底を変換|

--

### ProteinDF ツール一覧(3)

|ツール|内容|
|:-----|:---|
|pdf-mat-show|行列を標準出力に整形して表示|
|pdf-vtr-show|ベクトルを標準出力に整形して表示|
|pdf-mat-diff|行列の差分を標準出力に整形して表示|
|pdf-vtr-diff|ベクトルの差分を標準出力に整形して表示|


---

## ProteinDF マニュアル

* [manual](http://proteindf.github.io/ProteinDF_userman/en/index.html)
  * 製作中です

---

# ProteinDF Bridge クラスの紹介

2015.06.15
平野 敏行

---

## ProteinDF Bridge クラスの概要

- 様々なProteinDF Systemアプリケーションの  
  データの橋渡しをスムーズに行うクラスライブラリ
  - C/C++, Pythonなどで連携可能
    - もちろんRuby, Perl などもOK
- コンテナ + アルゴリズム
  - STLのような設計思想

--

## STL

* コンテナとアルゴリズムが互いに独立している
  * 主語と述語のような関係
* コンテナクラス
  * vector, map, set, list, queueなど
* アルゴリズムクラス
  * copy, sort, lower_bound, upper_bound, min, max, find, transform, replace, remove など

---

## 開発の動機

--

### ProteinDF Bridge クラスの開発の動機(1)

* 分子構造のファイル形式の種類が多すぎる
* read/writeをそれぞれのソフトで  
  書く・メンテナンスするのは面倒
  * 意外と仕様(ファイル形式)の変更が多い

--

### ファイル形式

  * PDB
  * CIF, mmCIF
  * MOL/SDF (MDL MOL)
  * CML (Chemical Markup Language)
  * xyz
  * SMILES
  * Gaussian, GAMESS inputfile
  * Amber, GROMACS, NAMD trajectory

--

### ProteinDF Bridge クラスの開発の動機(2)

* モデリング・QM・MDソフトで共通したアルゴリズムが多い
  * super impose(重ねあわせ), RMSD計算
  * 末端(NME, ACE)処理
  * 2次構造判定
  * 塩橋判定
  * SS結合処理

  など他にもたくさんある

---

## ProteinDF Bridge クラスの設計思想

* 初学者でも安全なクラスライブラリ
  * 取り扱いが簡単
    * **おまじない**は不要
  * 実行時エラーを起こさない
    * メモリリークを起こさない
      * 但し、実行性能は良くない

---

## Bridge クラス データ形式

--

### 代数幾何情報
* Position
  * カーテシアン座標、演算
* vector
  * ベクトルファイルのI/O, 線形演算
* Matrix
  * 行列ファイルのI/O, 線形演算

--

### 化学情報(1)

* PeriodicTable
  * 原子情報データベース

* Atom
  * 原子情報(原子種、座標、電荷など)を保持するコンテナ

--

### 化学情報(2)

* AtomGroup
  * 原子団を保持するコンテナ
  * Atom, AtomGroupを要素に持つ
  * パスによる位置指定のサポート
    * パスと名前は異なる

* bond
  * 結合情報を保持するコンテナ

---

## Bridgeクラス アルゴリズム

--

### ファイルI/O

* BioPdb
  * PDBファイルの読み書き

* xyz
  * xyzファイルの読み書き

--

### 原子団操作

* Selector
  * 原子・原子団の選択

* Superposer
  * 原子団の重ねあわせ
  * RMSD, 変換行列

* modeling
  * 原子の付加など

--

### タンパク質情報

* ionpair
  * イオン対の判定

--

## データベース

* DbManager
  * データベース処理のラッパー
    * SQL記述の必要なし

--
### その他

* utils
  * 文字列処理など

* mail
  * メール送信の処理

---

## タンパク質構造とBridgeクラス

--

### タンパク質構造の階層

モデル > 鎖 > アミノ酸残基 > 原子

* これらを順にAtomGroupでグループ化

--

#### PDB

```text
ATOM      1  N   GLY     1      -7.506   8.839   2.137  1.00  0.00           N
ATOM      2  H1  GLY     1      -8.205   8.976   2.850  1.00  0.00           H
ATOM      3  H2  GLY     1      -6.748   9.502   2.342  1.00  0.00           H
ATOM      4  H3  GLY     1      -7.898   9.160   1.255  1.00  0.00           H
ATOM      5  CA  GLY     1      -7.025   7.426   2.076  1.00  0.00           C
ATOM      6  HA2 GLY     1      -6.699   7.122   3.071  1.00  0.00           H
ATOM      7  HA3 GLY     1      -7.855   6.782   1.785  1.00  0.00           H
ATOM      8  C   GLY     1      -5.848   7.174   1.108  1.00  0.00           C
ATOM      9  O   GLY     1      -5.122   8.105   0.763  1.00  0.00           O
```

--

#### bridge クラス

```text
/model_1/_/1/1_N   N(name="N")  (  -7.506,    8.839,    2.137) Z= 0.00
/model_1/_/1/2_H1  H(name="H1") (  -8.205,    8.976,    2.850) Z= 0.00
/model_1/_/1/3_H2  H(name="H2") (  -6.748,    9.502,    2.342) Z= 0.00
/model_1/_/1/4_H3  H(name="H3") (  -7.898,    9.160,    1.255) Z= 0.00
/model_1/_/1/5_CA  C(name="CA") (  -7.025,    7.426,    2.076) Z= 0.00
/model_1/_/1/6_HA2 H(name="HA2")(  -6.699,    7.122,    3.071) Z= 0.00
/model_1/_/1/7_HA3 H(name="HA3")(  -7.855,    6.782,    1.785) Z= 0.00
/model_1/_/1/8_C   C(name="C")  (  -5.848,    7.174,    1.108) Z= 0.00
/model_1/_/1/9_O   O(name="O")  (  -5.122,    8.105,    0.763) Z= 0.00
```

* パスは"/ (スラッシュ)"で区切る
* モデル番号が無い場合は1
* 鎖情報が無い場合は"_ (アンダースコア)"
* アミノ酸残基名は該当グループの名前に登録
* 原子のパスの先頭にはindex(数字)

---

## Bridge クラススクリプト

--

### 変換系(1)

|ツール|内容|
|:-----|:---|
|mpac2yml|MessagePack形式のファイルをYAML形式に変換する|
|yml2mpac|YAMLファイルをMessagePack形式に変換する|
|pdb2brd|PDBファイルをBridge形式に変換する|
|xyz2brd|XYZ形式をBridge形式に変換する|

--

### 変換系(2)

|ツール|内容|
|:-----|:---|
|brd2pdb|Bridge形式をPDB形式に変換する|
|brd2xyz|Bridge形式をXYZ形式に変換する|
|brd2txt|Bridge形式を標準出力に出力する|

--

### 構造緩和

|ツール|内容|
|:-----|:---|
|relax _ protein|構造緩和を行う|
|remove_wat|水分子を除去する|

--

### タンパク質情報

|ツール|内容|
|:-----|:---|
|superposer.py|superimposeを行い、RMSDを出力する|
|brd-setup-bond.py|ボンド情報を正規化する|

--

### デバッグ支援

|ツール|内容|
|:-----|:---|
|brd-show-bonds.py|Bridge形式ファイル内の結合情報を出力する|
|db2txt.py|SQLite形式のデータベースを出力する|
|doctest _ runner.py|ライブラリのテストを実行する|
|module_inspect.py|実行環境における登録済みモジュールを表示する|

---

## Bridgeクラスデータ形式

Bridgeクラスで使われているオープンなデータ形式

--

### [MessagePack](http://msgpack.org)

* 機種依存の無いバイナリ形式
  * Endianの問題を気にしなくて良い
* コンパクト
* プログラミング言語に依存しない
* フォーマット定義(IDL)が不要
  * cf.) google protocol buffers
  * リスト型・辞書型コンテナを有する
  * データ型の仕様変更に柔軟に対応できる

--

### MessagePackの文字列問題

* [Issue121](https://github.com/msgpack/msgpack/issues/121)
  * 文字列はバイナリの配列? 専用の型?
    * フォーマットの対応? アプリケーションの対応? 
  * 新しい拡張仕様が導入された

--

### [YAML](http://yaml.org)

* Human-Readableなテキスト形式
  * XMLより分かりやすい
  * データサイズはどうしても大きくなる(XMLよりは小さい)
* データ構造としてリスト・辞書を持つ
* [詳しい解説](http://magazine.rubyist.net/?0009-YAML)

--

### [SQLite](https://www.sqlite.org)

* public-domainなRDBMS
* 非常に軽量
* Cランタイム以外のライブラリを必要としない
* バイトオーダーに依存しない
* DBは単一ファイル
  * 最大128TiBまで
* 多くの言語で使用可能

---

# ProteinDF_pytool の使い方

2015.06.15
平野 敏行

---

## ProteinDF_pytool 概要

* プリ・ポスト処理用プログラムを用意
  * 出力結果(fl_Out_Stdなど)の解析で消耗したくない
  * (重要な)結果はDB(SQLite)に格納
    * エンディアンの心配をしたくない
    * HDF5の方が良い?
* ほぼPythonスクリプト
  * 改変が用意
* いずれはProteinDFパッケージに融合したい

---

## ProteinDF python スクリプト

|ツール|内容|
|:-----|:---|
|pdf-archive| 計算結果をDB(SQLite形式)に登録する <br /> DBをcopyすれば他の計算機でも解析可能|
|pdf-report|結果解析レポートを出力する <br /> 全エネルギーやエネルギー準位のヒストリなど作成|

---

# QCLObotの紹介

2015.06.15
平野 敏行

---

## QCLObot概要

--

### QCLObotとは

* 分子シミュレーションを行う自動化プログラム(bot)
  * QMだけでなくMDも視野に
* 大規模分子のQM計算に必要な初期値をQCLO法により作成

--

## QCLO法

--

### QCLOとは

* 擬カノニカル局在化軌道(Quasi-Canonical Localized Orbital; QCLO)
  * 領域内ではカノニカル分子軌道の性質を持った、局在化軌道

* 局在化軌道(Localized Orbital; LO)
  * 分子軌道のユニタリ変換で得られる

* QCLO法
  * 小さなサブセットから段階的にQCLO計算領域を領域拡大することで良質な初期分子軌道を得る方法

--

### 計算方法

$
F\_{LO} = {C ^{\dagger}}^{AO}\_{LO} F\_{AO} C^{AO}\_{LO}
$

$
F\_{LO} C\_{LO} = \epsilon\_{LO} C\_{LO}
$

$
C^{AO}\_{LO} = C^{AO}\_{LO} C\_{LO}
$

|シンボル|意味|
|:-|:-|
|$F$|Fock行列|
|$C$|係数行列|
|$C\_{LO}$|QCLO|

--

### QCLO法の用語

* フラグメント
  * QCLOを求める最小の分子領域単位

* フレーム分子
  * QM計算を行う分子単位
  * 1つ以上のフラグメントから構成される

* 計算シナリオ
  * QCLO法を進めていく計算手順

---

## QCLObot 設計思想

--

### QCLObot 設計思想(1)

* Pythonで開発
  * 開発コストの削減
  * 基本的に何処でも動く

--

### QCLObot 設計思想(2)

* 自動化
  * 面倒なことはしたくない
  * 人間は計算シナリオに専念したい
    * これも自動化したい

--

### QCLObot 設計思想(3)

* 冪等性
  * 何度同じことをやっても同じ結果を返す

---

## QCLObotクラス

--

### フレーム・フラグメント管理

* QcAtom
  * bridge.Atomを継承
  * 基底関数情報を追加

* QcOrbitaldata
  * 基底関数情報

* QcFragment
  * QcAtomオブジェクトを追加することでフラグメントを構成
  * QcFragmentオブジェクトを子要素として持つことができる
    * 新たなフラグメントとして合成される
  * フラグメントに属する密度行列・QCLOを保存

* QcFrame
  * QcFragmentを追加することでフレーム分子を構成
  * 入力ファイルの作成・実行環境の作成・計算実行・post処理

--
### その他

* QcControl
  * (YAML形式で指示された場合)計算制御
   
---

## YAMLファイルを使った計算シナリオ

--

### 開発動機

* いちいちpythonスクリプトを書くのは面倒
* フラグメントの関係性に専念したい
  * 処理の順番(依存関係)を気にしたくない・自動的にやって欲しい

### 計算シナリオとYAML

* 構造の一致
  * QCLO計算シナリオ
  * YAMLのツリー構造
* YAMLの柔軟性
  * [Ansible](https://github.com/ansible/ansible)での採用

---

## 計算シナリオのプログラミング

--

### 構造緩和スクリプト

```
#!/bin/bash

if [ x${1} = x ]; then
    echo "please input PDB ID. stop."
    exit 1
fi

PDBID=${1}
MODELID=1

export AMBERHOME=${HOME}/local/amber14
export PATH=${AMBERHOME}/bin:${PATH}

# model select --------------------------------------------------------
run_reduce()
{
    echo "run reduce for protonation..."
    PDBID=${1}
    if [ x${PDBID} = x ]; then
        echo "please input PDBID. stop."
        exit 1
    fi

    PDBFILE=${PDBID}.pdb
    PDBFILE_ORIG=${PDBID}.orig.pdb

    cp ${PDBFILE} ${PDBFILE_ORIG}
    echo "original PDB file is saved as ${PDBFILE_ORIG}"

    reduce ${PDBFILE_ORIG} > ${PDBFILE}
    echo "protonated PDB file is saved as ${PDBFILE}"
}

echo "protonate..."
run_reduce ${PDBID}
echo "done."
echo

echo "save brd file..."
${PDF_HOME}/bin/pdb2brd.py --model 1 ${PDBID}.pdb ${PDBID}.brd
# ${PDF_HOME}/bin/brd2pdb.py ${PDBID}.brd > select.pdb
echo "done."
echo

echo "remove WAT..."
${PDF_HOME}/bin/remove_wat.py -o ${PDBID}.noWAT.brd ${PDBID}.brd

#./pdb_model_selecter.py -m ${MODELID} -o ${PDBID}.model_1.brd ${PDBID}.brd
#echo "model selected ${MODELID} is saved as ${PDBID}.brd"

#exit

# ----------------------------------------------------------------------
run_leap()
{
    STEP=$1
    tleap -s -f leap_md${STEP}.in
}


run_sander()
{
    STEP=$1

    DO_PARALLEL="${HOME}/local/gnu/openmpi/bin/mpiexec -n 4 "
    SANDER="${HOME}/local/amber14/bin/sander.MPI"
    ${DO_PARALLEL} ${SANDER} -O \
        -i md${STEP}.in \
        -o md${STEP}.out \
        -c md${STEP}.inpcrd \
        -p md${STEP}.prmtop \
        -r md${STEP}.restrt \
        -x md${STEP}.mdcrd \
        -v md${STEP}.mdvel \
        -e md${STEP}.mden
}

make_pdb()
{
    ambpdb -p md${STEP}.prmtop < md${STEP}.restrt > md${STEP}_after.pdb
}

step1()
{
echo ">>>> step1"
${PDF_HOME}/bin/relax_protein.py ${PDBID}.noWAT.brd 1
echo "do sander..."
run_sander 1
make_pdb 1
${PDF_HOME}/bin/pdb2brd.py md1_after.pdb md1_after.brd
echo "<<<< step1 done."
echo
}

step2()
{
echo ">>>> step2"
${PDF_HOME}/bin/relax_protein.py md1_after.brd 2
echo "do sander..."
run_sander 2
make_pdb 2
${PDF_HOME}/bin/pdb2brd.py md2_after.pdb md2_after.brd
echo "<<<< step2 done."
echo
}

step3()
{
echo ">>>> step3"
${PDF_HOME}/bin/relax_protein.py md2_after.brd 3
echo "do sander..."
run_sander 3
make_pdb 3
${PDF_HOME}/bin/pdb2brd.py md3_after.pdb md3_after.brd
echo "<<<< step3 done."
echo
}

# main
step1
step2
step3
```

--

## QCLObot script

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import argparse
import logging
import logging.config
import pprint

try:
    import msgpack
except:
    import msgpack_pure as msgpack

import pdfbridge as bridge
import pdfpytools as pdf
import qclobot as qclo

def main():
    parser = argparse.ArgumentParser(description='QCLO program')
    parser.add_argument('brdfile',
                        nargs=1,
                        help='Bridge file')
    parser.add_argument('-l', '--logconfig',
                        nargs=1,
                        action='store',
                        help='logconfig file')
    parser.add_argument('-v', '--verbose',
                        action='store_true',
                        default=False)
    parser.add_argument('-d', '--debug',
                        action='store_true',
                        default=False)
    args = parser.parse_args()

    # setting
    verbose = args.verbose
    if args.debug:
        logging.basicConfig(level=logging.DEBUG)
    brdfile_path = args.brdfile[0]
    logconfig_path = args.logconfig[0]
    if logconfig_path:
        logging.config.fileConfig(logconfig_path)

    # load
    if verbose:
        print("reading: {}".format(brdfile_path))
    brdfile = open(brdfile_path, 'rb')
    brddata = msgpack.unpackb(brdfile.read())
    brdfile.close()

    # all models
    models = bridge.AtomGroup(brddata)

    # model
    model = models["model_1"]

    frames = {}
    #
    #N_TERM = 0 # N-termがNMEなら1
    #C_TERM = 0 # C-termがACEなら1
    modeling = bridge.Modeling()
    for chain_name, chain in model.groups():
        max_resid = chain.get_number_of_groups()
        logging.info("chain {}: max_resid={}".format(chain_name, max_resid))

        step1(frames, chain, has_ACE=True, has_NME=True, dry_run = False)
        step2(frames, chain, has_ACE=True, has_NME=True, dry_run = False)
        step3(frames, chain, has_ACE=True, has_NME=True, dry_run = False)
            

def step1(frames, chain, start = 1, end = -1,
          has_ACE = False, has_NME = False,
          dry_run = False):
    '''
    has_ACE: specify True if the N-term is ACE
    has_NME: specify True if the C-term is NME
    '''
    logging.info("==== start of STEP 1 ====")

    if end == -1:
        end = chain.get_number_of_groups()
    if (start == 1) and (has_ACE == True):
        start = 2
        logging.info('pass calculation of ACE frame: start 1 -> {}'.format(start))
    if (end == chain.groups()) and (has_NME == True):
        end = end -1
        logging.info('pass calculation of NME frame: end {} -> {}'.format(end+1, end))
        
    modeling = bridge.Modeling()
    num_of_residues = chain.get_number_of_groups()
    for resid in range(start, end +1):
        res = chain[resid]
        name = 'res_{}-{}'.format(resid, resid)
        logging.info(">>>> STEP 1(resid={})".format(resid))

        # create base fragment
        res_model = bridge.AtomGroup(res)
        fragment_res = qclo.QcFragment(res_model)
	fragment_res.margin = False
        frame = qclo.QcFrame(name = name)
        frame[name] = fragment_res

        # ACE fragment
        if resid >= 2:
            ACE = qclo.QcFragment()

            prev = chain[resid -1]
            if (resid == 2) and (has_ACE == True):
                ACE = qclo.QcFragment(prev)
            else:
                ag_ACE = modeling.get_ACE_simple(prev)
                ACE = qclo.QcFragment(ag_ACE)

            ACE.margin = True
            frame['ACE'] = ACE
            
        # NME fragment
        if resid <= num_of_residues -1:
            NME = qclo.QcFragment()
            ahead = chain[resid +1]
            if (resid == num_of_residues -1) and (has_NME == True):
                NME = qclo.QcFragment(ahead)
            else:
                ag_NME = modeling.get_NME_simple(ahead)
                NME = qclo.QcFragment(ag_NME)

            NME.margin = True
            frame['NME'] = NME

        # calc
        try:
            setup_calc_conf(frame.pdfparam)
            frame.calc_sp(dry_run = dry_run)
            frame.pickup_density_matrix()
            frame.calc_lo()
            frame.pickup_lo()
        except:
            raise

        # regist
        frames[frame.name] = frame

    logging.info("==== end of STEP 1 ====")

        
def step2(frames, chain, start = 1, end = -1,
          has_ACE = False, has_NME = False,
          dry_run = False):
    '''
    has_ACE: specify True if the N-term is ACE
    has_NME: specify True if the C-term is NME
    '''
    logging.info("==== start of STEP 2 ====")
    
    if end == -1:
        end = chain.get_number_of_groups()
    if (start == 1) and (has_ACE == True):
        start = 2
        logging.info('pass calculation of ACE frame: start 1 -> {}'.format(start))
    if (end == chain.groups()) and (has_NME == True):
        end = end -1
        logging.info('pass calculation of NME frame: end {} -> {}'.format(end+1, end))
        
    for resid in range(start, end -3 +1):
        res1 = resid
        res2 = res1 +1
        res3 = res1 +2

        frame = qclo.QcFrame(name = 'res_{}-{}'.format(res1, res3))

        res1str = 'res_{res1}-{res1}'.format(res1=res1)
        res2str = 'res_{res2}-{res2}'.format(res2=res2)
        res3str = 'res_{res3}-{res3}'.format(res3=res3)
        frame[res1str] = frames[res1str][res1str]
        frame[res2str] = frames[res2str][res2str]
        frame[res3str] = frames[res3str][res3str]
        
        frame['ACE'] = frames[res1str]['ACE']
        frame['NME'] = frames[res3str]['NME']

        frames[frame.name] = frame

        try:
            setup_calc_conf(frame.pdfparam)
            # frame.guess_density()
            frame.calc_preSCF(dry_run = dry_run) # QCLOの前にpreSCFが必要
            frame.guess_QCLO()
            frame.calc_sp(dry_run = dry_run)
            frame.calc_lo()
            frame.pickup_lo()
        except:
            raise

    logging.info("==== end of STEP 2 ====")
    
def step3(frames, chain, start = 1, end = -1,
          has_ACE = False, has_NME = False,
          dry_run = False):
    '''
    has_ACE: specify True if the N-term is ACE
    has_NME: specify True if the C-term is NME
    '''
    logging.info("==== start of STEP 3 ====")

    name = 'res_{}-{}'.format(2, 6)
    frame = qclo.QcFrame(name = name)
    frame[name] = qclo.QcFragment()
    frame[name].set_group('res_2-2', frames['res_2-4']['res_2-2'])
    frame[name].set_group('res_3-3', frames['res_2-4']['res_3-3'])
    frame[name].set_group('res_4-4', frames['res_3-5']['res_4-4'])
    frame[name].set_group('res_5-5', frames['res_4-6']['res_5-5'])
    frame[name].set_group('res_6-6', frames['res_4-6']['res_6-6'])
    frame['ACE'] = frames['res_2-4']['ACE']
    frame['NME'] = frames['res_4-6']['NME']

    frames[name] = frame

    try:
        setup_calc_conf(frame.pdfparam)
        frame.calc_preSCF(dry_run = dry_run)
        frame.guess_QCLO()
        frame.calc_sp(dry_run = dry_run)
        frame.calc_lo()
        frame.pickup_lo()
    except:
        raise

    logging.info("==== end of STEP 3 ====")
    
            
def setup_calc_conf(pdfparam):
    pdfparam.j_engine = 'CD'
    pdfparam.k_engine = 'CD'
    pdfparam.xc_engine = 'gridfree_CD'
    pdfparam.xc_functional = 'b3lyp'
        
if __name__ == '__main__':
    import cProfile
    cProfile.run('main()', 'qclo_prof')

    import pstats
    ps = pstats.Stats('qclo_prof')
    ps.sort_stats('cumulative').print_stats()
    ps.sort_stats('time').print_stats()

```


--

## YAMLファイルでの例

```
---
vars:
  step1_residues: [ 2, 3, 5, 8, 9, 10, 12, 13, 14, 15, 16, 18, 19, 20,
                   23, 24, 25, 26, 27, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39,
                   41, 42, 43, 44, 45, 46, 47, 48, 49, 50 ]
  step2_residues: [ ]
tasks:
  - name: default
    brd_file: 2HIU.model.brd
    basis_set: DZVP2
    guess: Harris
    XC_functional: B3LYP
    J_engine: CD
    K_engine: CD
    XC_engine: grid

  # ion-pair
  - name: res_1_res_4
    sp: true
    fragments:
      - name: res_1-1
        brd_select: /model_1/_/1/
      - name: NME_1
        add_NME: true
        brd_select: /model_1/_/2/
      - name: ACE_4
        add_ACE: true
        brd_select: /model_1/_/3/
      - name: res_4-4
        brd_select: /model_1/_/4/
      - name: NME_4
        add_NME: true
        brd_select: /model_1/_/5/

  # ion-pair
  - name: res_17_res_43
    sp: true
    fragments:
      - name: ACE_17
        add_NME: true
        brd_select: /model_1/_/16/
      - name: res_17-17
        brd_select: /model_1/_/17/
      - name: NME_17
        add_NME: true
        brd_select: /model_1/_/18/
      - name: ACE_43
        add_NME: true
        brd_select: /model_1/_/42/
      - name: res_43-43
        brd_select: /model_1/_/43/
      - name: NME_43
        add_NME: true
        brd_select: /model_1/_/44/

  # SS
  - name: res_6_res_11
    sp: true
    fragments:
      - name: ACE_6
        add_ACE: true
        brd_select: /model_1/_/5/
      - name: res_6-6
        brd_select: /model_1/_/6/
      - name: NME_6
        add_NME: true
        brd_select: /model_1/_/7/
      - name: ACE_11
        add_ACE: true
        brd_select: /model_1/_/10/
      - name: res_11-11
        brd_select: /model_1/_/11/
      - name: NME_11
        add_NME: true
        brd_select: /model_1/_/12/

  # SS
  - name: res_7_res_28
    sp: true
    fragments:
      - name: ACE_7
        add_ACE: true
        brd_select: /model_1/_/6/
      - name: res_7-7
        brd_select: /model_1/_/7/
      - name: NME_7
        add_NME: true
        brd_select: /model_1/_/8/
      - name: ACE_28
        add_ACE: true
        brd_select: /model_1/_/27/
      - name: res_28-28
        brd_select: /model_1/_/28/
      - name: NME_28
        add_NME: true
        brd_select: /model_1/_/29/

  # SS
  - name: res_20_res_40
    sp: true
    fragments:
      - name: ACE_20
        add_ACE: true
        brd_select: /model_1/_/19/
      - name: res_20-20
        brd_select: /model_1/_/20/
      - name: NME_20
        add_NME: true
        brd_select: /model_1/_/21/
      - name: ACE_40
        add_ACE: true
        brd_select: /model_1/_/39/
      - name: res_40-40
        brd_select: /model_1/_/40/
      - name: NME_40
        add_NME: true
        brd_select: /model_1/_/41/

  - name: res_21-21
    sp: true
    fragments:
      - add_ACE: true
        name: ACE
        brd_select: /model_1/_/20/
      - name: res_21-21
        brd_select: /model_1/_/21/

  - name: res_22-22
    sp: true
    fragments:
      - name: res_22-22
        brd_select: /model_1/_/22/
      - add_NME: true
        name: NME
        brd_select: /model_1/_/23/

  - name: res_51-51
    sp: true
    fragments:
      - add_ACE: true
        name: ACE
        brd_select: /model_1/_/50/
      - name: res_21-21
        brd_select: /model_1/_/51/

  - name: res_{{ item }}-{{ item }}
    sp: true
    fragments:
      - add_ACE: true
        name: ACE
        brd_select: /model_1/_/{{ item -1 }}/
      - name: res_{{ item }}-{{ item }}
        brd_select: /model_1/_/{{ item }}/
      - add_NME: true
        name: NME
        brd_select: /model_1/_/{{ item +1 }}/
    with_items: step1_residues

# step2
  - name: res_1-11
    guess: QCLO
    sp: true
    fragments:
      - name: res_1-10
        fragments:
          - name: res_1-1
            reference:
              frame: res_1_res_4
              fragment: res_1-1
          - name: res_2-2
            reference:
              frame: res_2-2
              fragment: res_2-2
          - name: res_3-3
            reference:
              frame: res_3-3
              fragment: res_3-3
          - name: res_4-4
            reference:
              frame: res_1_res_4
              fragment: res_4-4
          - name: res_5-5
            reference:
              frame: res_5-5
              fragment: res_5-5
          - name: res_6-6
            reference:
              frame: res_6_res_11
              fragment: res_6-6
          - name: res_7-7
            reference:
              frame: res_7_res_28
              fragment: res_7-7
          - name: res_8-8
            reference:
              frame: res_8-8
              fragment: res_8-8
          - name: res_9-9
            reference:
              frame: res_9-9
              fragment: res_9-9
          - name: res_10-10
            reference:
              frame: res_10-10
              fragment: res_10-10
      - name: res_11
        fragments:
          - name: res_11-11
            reference:
              frame: res_6_res_11
              fragment: res_11-11
          - name: NME_11
            reference:
              frame: res_6_res_11
              fragment: NME_11
      - name: res_28 # for res_7
        fragments:
          - name: ACE_28
            reference:
              frame: res_7_res_28
              fragment: ACE_28
          - name: res_28-28
            reference:
              frame: res_7_res_28
              fragment: res_28-28
          - name: NME_28
            reference:
              frame: res_7_res_28
              fragment: NME_28

  - name: res_10-21
    guess: QCLO
    sp: true
    fragments:
      - name: res_10-10
        fragments:
          - name: ACE_10
            reference:
              frame: res_10-10
              fragment: ACE
          - name: res_10-10
            reference:
              frame: res_10-10
              fragment: res_10-10
      - name: res_11-21
        fragments:
          - name: res_11-11
            reference:
              frame: res_6_res_11
              fragment: res_11-11
          - name: res_12-12
            reference:
              frame: res_12-12
              fragment: res_12-12
          - name: res_13-13
            reference:
              frame: res_13-13
              fragment: res_13-13
          - name: res_14-14
            reference:
              frame: res_14-14
              fragment: res_14-14
          - name: res_15-15
            reference:
              frame: res_15-15
              fragment: res_15-15
          - name: res_16-16
            reference:
              frame: res_16-16
              fragment: res_16-16
          - name: res_17-17
            reference:
              frame: res_17_res_43
              fragment: res_17-17
          - name: res_18-18
            reference:
              frame: res_18-18
              fragment: res_18-18
          - name: res_19-19
            reference:
              frame: res_19-19
              fragment: res_19-19
          - name: res_20-20
            reference:
              frame: res_20_res_40
              fragment: res_20-20
          - name: res_21-21
            reference:
              frame: res_21-21
              fragment: res_21-21
      - name: res_6 # for res_11
        fragments:
          - name: ACE_6
            reference:
              frame: res_6_res_11
              fragment: ACE_6
          - name: res_6
            reference:
              frame: res_6_res_11
              fragment: res_6-6
          - name: NME_6
            reference:
              frame: res_6_res_11
              fragment: NME_6
      - name: res_43 # for res_17
        fragments:
          - name: ACE_43
            reference:
              frame: res_17_res_43
              fragment: ACE_43
          - name: res_43
            reference:
              frame: res_17_res_43
              fragment: res_43-43
          - name: NME_43
            reference:
              frame: res_17_res_43
              fragment: NME_43
      - name: res_40 # for res_20
        fragments:
          - name: ACE_40
            reference:
              frame: res_20_res_40
              fragment: ACE_40
          - name: res_40
            reference:
              frame: res_20_res_40
              fragment: res_40-40
          - name: NME_40
            reference:
              frame: res_20_res_40
              fragment: NME_40


  - name: res_{{ item }}-{{ item +11 }}
    guess: QCLO
    sp: true
    fragments:
      - name: ACE_{{ item }}
        reference:
          frame: res_{{ item }}-{ item }}
          fragment: ACE
      - name: res_{{ item }}-{{ item }}
        reference:
          frame: res_{{ item }}-{{ item }}
          fragment: res_{{ item }}-{{ item }}
      - name: res_{{ item +1 }}-{{ item +10 }}
        fragments:
          - name: res_{{ item +1 }}-{{ item +1 }}
            reference:
              frame: res_{{ item +1 }}-{{ item +1 }}
              fragment: res_{{ item +1 }}-{{ item +1 }}
          - name: res_{{ item +2 }}-{{ item +2 }}
            reference:
              frame: res_{{ item +2 }}-{{ item +2 }}
              fragment: res_{{ item +2 }}-{{ item +2 }}
          - name: res_{{ item +3 }}-{{ item +3 }}
            reference:
              frame: res_{{ item +3 }}-{{ item +3 }}
              fragment: res_{{ item +3 }}-{{ item +3 }}
          - name: res_{{ item +4 }}-{{ item +4 }}
            reference:
              frame: res_{{ item +4 }}-{{ item +4 }}
              fragment: res_{{ item +4 }}-{{ item +4 }}
          - name: res_{{ item +5 }}-{{ item +5 }}
            reference:
              frame: res_{{ item +5 }}-{{ item +5 }}
              fragment: res_{{ item +5 }}-{{ item +5 }}
          - name: res_{{ item +6 }}-{{ item +6 }}
            reference:
              frame: res_{{ item +6 }}-{{ item +6 }}
              fragment: res_{{ item +6 }}-{{ item +6 }}
          - name: res_{{ item +7 }}-{{ item +7 }}
            reference:
              frame: res_{{ item +7 }}-{{ item +7 }}
              fragment: res_{{ item +7 }}-{{ item +7 }}
          - name: res_{{ item +8 }}-{{ item +8 }}
            reference:
              frame: res_{{ item +8 }}-{{ item +8 }}
              fragment: res_{{ item +8 }}-{{ item +8 }}
          - name: res_{{ item +9 }}-{{ item +9 }}
            reference:
              frame: res_{{ item +9 }}-{{ item +9 }}
              fragment: res_{{ item+9  }}-{{ item +9 }}
          - name: res_{{ item +10 }}-{{ item +10 }}
            reference:
              frame: res_{{ item +10 }}-{{ item +10 }}
              fragment: res_{{ item +10 }}-{{ item +10 }}
      - name: res_{{ item +11 }}-{{ item +11 }}
        reference:
          frame: res_{{ item +11 }}-{{ item +11 }}
          fragment: res_{{ item +11 }}-{{ item +11 }}
      - name: NME_{{ item +11 }}
        reference:
          frame: res_{{ item +11 }}-{{ item +11 }}
          fragment: NME
    with_items: step2_residues


```

---

## Tips (ユーザー編)

--

### Linux(1)

* 使い方が分からない場合はヘルプが用意されているかどうか調べる

```
command -h
```

```
command --help
```

* プログラムをビルドする際、configureが用意されている場合は、configureを実行する
  * prefixはインストール場所を指定する
  * CC, CFLAGS, CXX, CXXFLAGS, F77, F90, FC, FCFLAGS, LDFLAGS, LIBSなどの環境変数に注意すること

--

### Linux(2)

* 必要なパッケージがインストールされていない
  * root権限がないとき

→ [linuxbrew](https://github.com/Homebrew/linuxbrew)を使う

* ホームディレクトリ以下にパッケージを管理

--

### Python

* Pythonプログラムのインストール
  * setup.pyを用意されている場合は、これを実行する
```
./setup.py build
./setup.py install --prefix=ANYWHERE
```

* PYTHONライブラリの場所を指定
環境変数PYTHONPATHの場所にあるライブラリが検索・使用される。

---

## Tips (デベロッパー編)

--

### Linux CUIプログラム作成

* [UNIXという考え方](http://www.amazon.co.jp/UNIXという考え方―その設計思想と哲学-Mike-Gancarz/dp/4274064069)
  * プログラムはシンプル・単機能であること
  * コマンド名は動詞が好ましい
  * 引数を与える場合は、英文法(第4文型 SVOO, 第5文型 SVOC)に従うこと
  * e.g.)

 ```
  cp [source_file] [dest_file]
 ```

--

### C++

* Style Guide
  * [Google Style Guide](https://google-styleguide.googlecode.com/svn/trunk/cppguide.html)

--

## Python

* システム以外のPythonをインストール
  * [pyenv](https://github.com/yyuu/pyenv)
  * [pyenv-virtualenv](https://github.com/yyuu/pyenv-virtualenv)
  * ref.) rbenv, plenv, ...

* Style Guide
  * [PEP8](https://www.python.org/dev/peps/pep-0008/)

---

### C++/Python のススメ

* Cの場合

```C
a[3] = 1.0; // OK
phoneNumber["satolab"] = "56670"; // NG!
```

* Pythonの場合

```python
a[3] = 1.0 # OK
phoneNumber["satolab"] = "56670" # OK
```

* C++の場合

```C++
std::map<std::string, std::string> phoneNumber;
phoneNumber["satolab"] = "56670"; // OK
```

--

* Pythonの場合

```python
phoneNumber["IIS"]["satolab"] = "56670" # OK
player["acmilian"][11] = "Honda" # OK
```

* C++の場合

```C++
std::map<std::string, std::map<std::string, std::string> > phoneNumber;
phoneNumber["IIS"]["satolab"] = "56670"; // OK

std::map<std::string, std::map<int, std::string> > player;
player["acmilian"][11] = "Honda"; // OK

#include "TlSerializeData.h"
TlSerializeData sd_player;
sd_playyer["acmilian"][11] = "Honda"; // OK
```


---
