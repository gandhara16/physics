-   本稿は2022年の4月に行われた，「量子と古典の物理と幾何\@オンライン」(https://connpass.com/event/241136/)という研究会での発表をもとに書いた解説である。

-   このトピックに関する最新情報は<https://scrapbox.io/flagments/Wave_Equations>にポストしていく予定である。

-   間違いやわかりにくい説明も多々あると思うので，コメントなどお願いします。https://twitter.com/gandhara16，tadas＠fpu.ac.jp。些細なこと（誤字など）でも結構です。

Introduction
============

-   Klein-Gordon，Maxwell，Dirac 方程式は，それぞれ
    $\partial_\mu^2 \phi = m^2 \phi$，
    $\partial_t\mathbf{B} +\nabla\times\mathbf{E}=0, {\rm etc.}$，
    $\gamma^\mu\partial_\mu \psi_D + m \psi_D =0$
    などと書かれるが，同じ相対論的な場の方程式が，なぜこのように違う形をしているのだろうか？

-   実は，3つの方程式の微分演算子の部分は全く同じものであることを20世紀後半に
    Hestenes が幾何代数をつかって示している（参考文献参照）。

    -   しかし，幾何代数がとっつきにくいためか，これはあまり多くの物理学者には知られていないように感じられる。

    -   幾何代数，時空代数，クリフォード代数などの用語は微妙に意味するところが違うが，以下では気にせずに「幾何代数」で統一する。

-   ここでは，幾何代数をつかわずに，多くの物理学者になじみのある行列計算だけをつかって，同じ結果を導く。
    行列計算といっても，ここで必要なのは以下のガンマ行列の演算規則だけである。（$\eta$はメトリックテンソル，ハットマークは行列をあらわす。）
    $$\hat\gamma^\mu\hat\gamma^\nu         + \hat\gamma^\nu \hat\gamma^\mu        = 2\hat\eta^{\mu\nu}        \label{eq:gamma-rule}$$

-   以下では幾何代数の知識は一切使わないが，やってることは幾何代数の計算とまったくパラレルなので，この解説を読んだのちに教科書などを読むと，とっつきやすくなるのでは，と期待している。

3D Static Fields
================

-   まず，練習問題として3次元ユークリッド空間のベクトル場を考える。いきなり4次元からはじめることもできるが，4次元だと4行4列の複素行列を計算しなくてはならないので，手間がかかる。3次元だと2行2列ですみ，さらに多くの物理学者に馴染みのある
    Pauliの$\sigma$行列がつかえるので，直感的にわかりやすい（と思う）。

    -   3次元の計算を理解すると，必要な要素はだいたいそろっているので，それを4次元に拡張して適用するのは容易である。

-   物理的直感でイメージしやすいように，静電場と静磁場を例にとる。まず，以下の静電場の方程式を考える。
    $$\nabla\cdot\mathbf{E} = \rho\,,     ~~\nabla\times\mathbf{E} = 0\,,                     ~~\nabla\times\mathbf{B} = \mathbf{J}\,,                 ~~\nabla\cdot\mathbf{B} = 0\,.                \label{eq:3dEM}$$

-   幾何代数は，このようなベクトル場をDiracの$\gamma$行列であらわし，その代数演算で幾何学的構造をあきらかにする。
    3次元の場合は([\[eq:gamma-rule\]](#eq:gamma-rule){reference-type="ref"
    reference="eq:gamma-rule"})を満たす$\gamma$行列は以下のような
    Pauliの$\sigma$行列になる。
    ```math
    $$\hat\sigma_{1}=\left(\begin{array}{cc}    0 & 1\\    1 & 0    \end{array}\right)\,,\;\;    \hat\sigma_{2}=\left(\begin{array}{cc}    0 & -i\\    i & 0    \end{array}\right)\,,\;\;    \hat\sigma_{3}=\left(\begin{array}{cc}    1 & 0\\    0 & -1    \end{array}\right)\,. \nonumber
    $$
    上では行列の形を明示的に書いたが，実は以下で必要なのは
    ([\[eq:gamma-rule\]](#eq:gamma-rule){reference-type="ref"
    reference="eq:gamma-rule"})から導かれる以下の演算規則だけである。
    $$\hat\sigma_i \hat\sigma_j =         \begin{cases}        \hat 1 & {\rm if }~~i=j\\        -\hat\sigma_j \hat\sigma_i  &  {\rm if }~~i\ne j        \end{cases}\,. \label{eq:sigma-rule}$$

-   この演算法則（に$i$をかけたもの）は四元数の虚数部と等価である。四元数の虚数部分を使って3次元ベクトルをあらわすことができるので，上の3つの$\sigma$行列も3次元の単位ベクトルを表すことができると考えられる。

Static Electric Field
---------------------

-   Pauliの$\sigma$行列を各方向の単位ベクトルとみなし，電場は以下のように書く。
    $$\hat{\mathbf{E}} = \hat \sigma_1 E_x         + \hat \sigma_2  E_y + \hat \sigma_3  E_z\,.\label{eq:e-field}$$
    この$\hat{\mathbf{E}}$に作用する微分演算子を以下のようにあらわすと，次にみるようにベクトル解析と同じ結果が得られる。この演算子はDirac演算子と呼ばれる。
    $$\hat D = \hat \sigma_1  \partial_x + \hat \sigma_2         \partial_y + \hat \sigma_3 \partial_z\,$$

    -   本稿では「ベクトル解析」という言葉は，ベクトルに対する演算一般ではなく，Gibbs
        や Heaviside
        が始めた$\mathbf{div}$や$\mathbf{rot}$を使ったベクトル計算の手法を意味する。

-   上の2つの式の積に対して，$\sigma$行列の演算規則
    ([\[eq:sigma-rule\]](#eq:sigma-rule){reference-type="ref"
    reference="eq:sigma-rule"}) を使うと $$
    \hat D \hat{\mathbf{E}} =&(\hat{\sigma_1}  \partial_x + \hat \sigma_2 \partial_y + \hat \sigma_3 \partial_z)(\hat \sigma_1 E_x + \hat \sigma_2  E_y + \hat \sigma_3  E_z)\\= & \hat 1(\partial_x E_x + \partial_y E_y + \partial_z E_z)\\ &+ \hat\sigma_3 \hat\sigma_2(\partial_z E_y - \partial_y E_z) + \hat\sigma_3 \hat\sigma_1(\partial_z E_x - \partial_x E_z) + \hat\sigma_1 \hat\sigma_2(\partial_x E_y - \partial_y E_x)$$

    この結果をみると，$\hat 1$の項は$\nabla\cdot\mathbf{E}$を，のこりは$\nabla\times\mathbf{E}$をあらわしていることがわかる。
    Pauli行列$\sigma_i$と単位行列の4つは互いに線形独立なので，これで方程式をつくると，4本の式になる。ここで，$\rho$を電荷密度として，$\hat D \hat{\mathbf{E}}=\hat 1\rho$という式を立てると，これは
    ([\[eq:3dEM\]](#eq:3dEM){reference-type="ref" reference="eq:3dEM"})
    の式になる。
    $$\hat D \hat{\mathbf{E}} = \begin{cases}\nabla\cdot \mathbf{E} = \rho&{\rm for}~\hat 1\\\nabla\times \mathbf{E} = 0 &{\rm for}~\hat\sigma_i\hat\sigma_j\end{cases}$$

-   この2つめの式から，ポテンシャル$\phi$が存在して，$\mathbf{E} = \nabla \phi$と書けることかる。つまり，このアプローチでは先に電場を導入し，それが従うべき物理法則$\hat D \hat{\mathbf{E}}=\hat 1 \rho$から，ポテンシャルが導びかれることになる。　　

Multi Vectors
-------------

-   上の電場およびその空間微分の表現をみると，$\hat 1$，$\hat \sigma_i$，$\hat \sigma_i \hat \sigma_j$などの成分をもっている。これらの幾何学的意味を考えると，それぞれ，点，線，面に対応している。ベクトル解析ではこれらの区別はあいまいだが，外積代数や微分形式では，これらをゼロベクトル，１ベクトル，２ベクトルと呼んで区別する。さらに，のちに出てくる$\hat \sigma_i\hat\sigma_j\hat\sigma_k$は３ベクトルで体積に相当する。

-   ゼロベクトルは描きにくいが，１ベクトル以上は下のように図示するとわかりやすい。

    ![image](figs.eps){width="11cm"}

    $$\hat\sigma_i \Leftrightarrow \mathbf{e}_i    ~~~~~~\hat\sigma_i\hat\sigma_j \Leftrightarrow     \mathbf{e}_i \times \mathbf{e}_j    ~~~~~~\hat\sigma_i \hat\sigma_j \hat\sigma_k     \Leftrightarrow      \mathbf{e}_k\cdot(\mathbf{e}_i \times \mathbf{e}_j)$$

-   以下ではベクトルの次数を
    グレード（grade）と呼ぼう。上の計算をみると電場はグレード
    1，その$\mathbf{div}$，$\mathbf{rot}$はそれぞれ，グレート 0 と 2
    であることがわかる。

-   Dirac演算子$\hat D$
    を作用させると，グレードがひとつ下（$\mathbf{div}$）とひとつ上（$\mathbf{rot}$）の成分が結果になる。これはグレード1だけでなく，他のグレードでもなりたつ。
    グレードを下げる微分演算を余微分，上げるのを外微分といい，それぞれ$\hat \delta$，$\hat d$であらわす。

    $$\nabla\cdot\mathbf{E},~~\nabla\times\mathbf{E}         \rightarrow \hat{D}\hat{\mathbf{E}}=\hat{\delta}\hat{\mathbf{E}}+\hat{d}\hat{\mathbf{E}}$$

-   つぎに見る磁場も含めて，以上の結果を表にまとめると次のようになる。

         grade                            0                                                   1                                                    2                                                  3
      ------------ ----------------------------------------------- ------------------------------------------------------- -------------------------------------------------- -------------------------------------------------
          unit               $\rule{0pt}{3ex}{\hat{1}}$                               $\hat{\sigma_i}$                                 $\hat\sigma_i\hat\sigma_j$                  $\hat\sigma_i\hat\sigma_j\hat\sigma_k$
         object                         point                                               line                                                surface                                            volume
       components                         1                                                   3                                                    3                                                  1
         elec.      $\rule{0pt}{3ex} \hat{\delta}\hat{\mathbf{E}}                       $\mathbf{E}$                        $\hat{d}\hat{\mathbf{E}}=\nabla\times\mathbf{E}$  
                                     =\nabla\cdot\mathbf{E}$                                                                                                                  
          mag.                                                      $\hat{\delta}\hat{\mathbf{B}}=\nabla\times\mathbf{B}$                     $\mathbf{B}$                     $\hat{d}\hat{\mathbf{B}}=\nabla\cdot\mathbf{B}$

    \

Static Magnetic Field
---------------------

-   次に，磁場について考えてみよう。磁場と磁束密度の関係にはいろいろと議論があるようだが，ここではそれには立ち入らずに，磁束密度$\mathbf{B}$をあつかう。上の
    ([\[eq:3dEM\]](#eq:3dEM){reference-type="ref"
    reference="eq:3dEM"})にある 静的な磁束密度の方程式を考える。

-   磁束密度$\mathbf{B}$は面密度なので，その面の向きに対応する2ベクトルである。
    $$\hat{\mathbf{B}} = \hat \sigma_2 \hat \sigma_3 B_x     + \hat \sigma_3 \hat \sigma_1  B_y + \hat \sigma_1 \hat \sigma_2  B_z$$
    これにDirac演算子$\hat D$を作用させると，電場のときと同じように計算して
    $$\begin{aligned}
        \hat D \hat{\mathbf{B}} =&(    \hat{\sigma_1}  \partial_x + \hat \sigma_2 \partial_y + \hat \sigma_3 \partial_z)    (\hat \sigma_2 \hat \sigma_3 B_x     + \hat \sigma_3 \hat \sigma_1  B_y + \hat \sigma_1 \hat \sigma_2  B_z)\\%    = & \hat\sigma_1(\partial_z B_y - \partial_y B_z)     + \hat\sigma_2(\partial_z B_x - \partial_x B_z)    + \hat\sigma_3 (\partial_x B_y - \partial_y B_x)\\    & +\hat\sigma_1\hat\sigma_2\hat\sigma_3(\partial_x B_x + \partial_y B_y + \partial_z B_z)\\\end{align*}が得られる。
    結果の式の各項は，$\mathbf{rot}$と$\mathbf{div}$に対応するが，かかる行列が$\hat\sigma_i$と$\hat\sigma_1\hat\sigma_2\hat\sigma_3$なのが電場の場合と違っている。
    Dirac演算子をかけると，電場の場合と同じく，ベクトルの次数がひとつ下がった成分$\hat\delta \hat{\mathbf{B}}$と上がった成分$\hat d\hat{\mathbf{B}}$がでてくるが，電場と違い，もとが2ベクトルなので，それぞれ1ベクトルと3ベクトルになる（{\sf Table 1}参照）。
    \item 電場のときと同様に$\hat \delta$ からくる成分とソースタームを結びつけると，静的磁束密度の方程式になる。ソースタームは以下の電流密度であり，$\hat D \hat{\mathbf{B}}=\hat{\mathbf{J}}$が (\ref{eq:3dEM})の磁場の部分 になる。
            \begin{equation*}       \hat{\mathbf{J}}=\hat\sigma_y\hat\sigma_z J_x               +\hat\sigma_z\hat\sigma_x J_y+\hat\sigma_x\hat\sigma_y J_z      \end{equation*}
    \end{itemize}
    \section{4D Wave Fields}
    \begin{itemize}
    \item 上でみた三次元の計算で，1ベクトルにDirac演算子を適用すると電場の方程式が，2ベクトルに適用すると磁束密度の方程式が得られた。同様の計算を，Minkowski 計量の四次元空間に適用してやると，１ベクトルに対して，Klein-Gordon 方程式が，２ベクトルに対してMaxwell 方程式が得られる。
    \item 三次元空間は他の空間と違う特殊性があり，線形独立な１ベクトル（線的ベクトル）と２ベクトル（面的ベクトル）の数が${}_3C_1={}_3C_2$となって等しいことである。このことにより，三次元では線と面の両方が3成分のベクトルであらわされることになり，両者の区別が鮮明ではない。四次元になると，１ベクトルは${}_4C_1=4$成分，2ベクトルは${}_4C_2=6$成分もつ。
    \item Dirac演算子は
    \begin{equation}    \hat{D}= \hat\gamma^t \partial_t    + \hat\gamma^x \partial_x     +\hat\gamma^y \partial_y     +\hat\gamma^z \partial_z\label{eq:4DD}\end{equation}
    となる。
    \end{itemize}

    \subsection{Klein-Gordon Equation}
    \begin{itemize}
        \item 次の4次元の1ベクトルを考える。3次元のときと同じように$\gamma$行列は各方向の単位ベクトルだと解釈する。以下では四次元ベクトルはカリグラフィックフォントで表す。
           \begin{align*}    \hat{\mathcal{V}}     = \hat\gamma^t \hat{\mathcal{V}}_t    + \hat\gamma^x \hat{\mathcal{V}}_x     +\hat\gamma^y \hat{\mathcal{V}}_y     +\hat\gamma^z \hat{\mathcal{V}}_z     \end{aligned}$$

-   これにDirac演算子 ([\[eq:4DD\]](#eq:4DD){reference-type="ref"
    reference="eq:4DD"})
    をかけて，三次元のときと同様に交換関係を使って計算すると
    $$\begin{aligned}
    \hat{D}\hat{\mathcal{V}}=&\hat{1}(V_{t,t}+V_{x,x}+V_{y,y}+V_{z,z})\nonumber\\&+\hat\gamma^t\hat\gamma^x(V_{t,x}-V_{x,t}) + \hat\gamma^t\hat\gamma^y(V_{t,y}-V_{y,t}) \nonumber\\ &+ \hat\gamma^t\hat\gamma^z(V_{t,z}-V_{z,t})+\hat\gamma^x\hat\gamma^y(V_{x,y}-V_{y,x}) \label{eq:DV}\\ &+\hat\gamma^z\hat\gamma^x(V_{z,x}-V_{x,z})  + \hat\gamma^x\hat\gamma^y(V_{x,y}-V_{y,x})\nonumber\\            =& \hat\delta \hat{\mathcal V} + \hat d\hat{\mathcal V}         \nonumber\end{aligned}$$
    この式の2〜4行$\hat\delta \hat{\mathcal V}$は三次元での$\mathbf{rot}$に対応するもので，これがゼロの場合はスカラー（ゼロベクトル）$\phi$が存在して，
    $$\hat\gamma^\mu \partial_\mu  \phi = \hat\gamma^\mu V_\mu$$と書くことができる。三次元の場合の静電場と同様に，はじめに1ベクトルである$\hat{\mathcal{V}}$を導入して，それが従う方程式から微分の2ベクトル成分がゼロであることにより，ポテンシャル$\phi$が導かれるという手順である。

-   式 ([\[eq:DV\]](#eq:DV){reference-type="ref" reference="eq:DV"})
    の第一行$\hat d \hat{\mathcal V}$は三次元の$\mathbf{div}$に対応する。したがって，$\hat D\hat{\mathcal{V}}=\hat 1 m^2\phi$と式を立てると，ベクトル解析の記法で$\square \phi = m^2 \phi$という
    Klein-Gordon 方程式になる。

Maxwell Equations
-----------------

-   上で1ベクトルにDirac演算子をかけると Klein-Gordon
    方程式が得られることをみた。同様の操作を2ベクトルにほどこすと，Maxwell
    方程式が得られる。
    2ベクトルは面に対応するが，四次元空間では線形独立な面の数は${}_4C_2=6$ある。つまり2ベクトルは6成分をもつ。

-   この6成分は電磁気学では電場の3成分と磁場の3成分になる。これは前節の，三次元の静電磁場とは別のあるかいをしていることに注意。電磁場をあらわす2ベクトル$\hat{\mathcal{F}}$は電場，磁場の成分を使って
    $$\begin{aligned}
        \hat{\mathcal{F}}     = &\hat\gamma^t\hat\gamma^x E_x    +\hat\gamma^t\hat\gamma^y E_x           +\hat\gamma^t\hat\gamma^z E_z\nonumber\\              &+\hat\gamma^y\hat\gamma^z B_x              +\hat\gamma^z\hat\gamma^x B_y              +\hat\gamma^x\hat\gamma^y B_z                \label{eq:EM}     \end{aligned}$$
    と書ける。これにDirac演算子を作用させた結果が四次元電流と等しいとおくとMaxwell方程式になる。
    $$\hat{D} \hat{\mathcal{F}}= \hat{\delta}\hat{\mathcal{F}} + \hat{d}\hat{\mathcal{F}}= J_\mu \hat{\gamma^\mu} \equiv \hat{\mathcal{J}}$$

-   すべての項の計算を書くと長くなるので，代表的な項をいくつか書くと
    $$\begin{gathered}
    \hat\gamma^t \partial_t (\hat\gamma^t \hat\gamma^x E_x) = \hat\gamma^x \partial_t E_x\,,~~~\hat\gamma^x \partial_x (\hat\gamma^t \hat\gamma^x E_x) = \hat\gamma^t \partial _x E_x\,, \\~~~\hat\gamma_y \partial_y (\hat\gamma^t \hat\gamma^x E_x) = \hat\gamma^t \hat\gamma^x \partial_y E_x\,,\nonumber\\\hat\gamma^t \partial_t (\hat\gamma^y \hat\gamma^z B_x) = \hat\omega\hat\gamma^x \partial_x B_x\,,~~~\hat\gamma^x \partial_x (\hat\gamma^y \hat\gamma^z B_x) = \hat\omega\hat\gamma^t \partial _x B_x\,, \nonumber\\~~~\hat\gamma_y \partial_y (\hat\gamma^t \hat\gamma^x B_x) = \hat\omega\hat\gamma^x  \partial_y B_x\,.\end{gathered}$$
    このような計算をして式を整理し，ベクトル解析の記法であらわすと以下のMaxwell方程式が得られる。
    $$\begin{aligned}
    \hat{\delta}\hat{\mathcal{F}} = \hat{\mathcal{J}}&~~\rightarrow~~\nabla\cdot\mathbf{E}=\rho\,,~~\partial_t \mathbf{E} + \nabla\times\mathbf{B} = \mathbf{J}\\\hat{d}\hat{\mathcal{F}} = 0&~~\rightarrow~~\nabla\cdot\mathbf{B}=0\,,~~\partial_t \mathbf{B} + \nabla\times\mathbf{E} = 0\\\end{aligned}$$

-   この結果は一般的なものであるが，実際の計算は$\gamma$行列の Dirac
    表現をつかうとやりやすい。（2022/5/20 Appendix
    に準備中，しばらくしたら上記のサイトをチェックしてみてください）

-   四次元ベクトルに関する方程式は以下のようにまとめられる。

          grade                             0                                    1                             2                                         3                                                          4
      -------------- ----------------------------------------------- -------------------------- -------------------------------- -------------------------------------------------- ------------------------------------------------------------------
           unit                $\rule{0pt}{3ex}{\hat{1}}$                $\hat{\gamma}^\mu$      $\hat\gamma^\mu\hat\gamma^\nu$   $\hat\gamma^\mu\hat\gamma^\nu \hat\gamma^\alpha$   $\hat\gamma^\mu\hat\gamma^\nu \hat\gamma^\alpha\hat\gamma^\beta$
          object                          point                                 line                        surface                                   3-volume                                                   4-volume
        components                          1                                    4                             6                                         4                                                          1
       Klein-Gordon   $\rule{0pt}{3ex} \hat\delta\hat{\mathcal{V}}$     $\hat{\mathcal{V}}$        $\hat{d}\hat{\mathcal{V}}$                                                       
         Maxwell                                                      $\hat\delta \mathcal{F}$        $\hat{\mathcal{F}}$                    $\hat{d}\hat{\mathcal{F}}$             

    \

### Dirac Equation

-   上の議論で，普通はベクトル解析の表現になっている Maxwell 方程式が
    Dirac行列$\gamma^\mu$を使って書けることをみた。ここでは，逆に Dirac
    方程式がベクトル解析の表現で書けることを示そう。

-   まず，Maxwell 方程式は普通に書かれる Dirac
    方程式とほぼ同様の形に書けることを示そう。そして，それを示した操作の逆をたどれば
    Dirac 方程式をベクトル解析の表現で示すことができる。

-   電磁場の表示([\[eq:EM\]](#eq:EM){reference-type="ref"
    reference="eq:EM"}) は$\gamma$行列をDirac表現を使って書くと
    $$\hat{\mathcal{F}}=\begin{pmatrix}   B_z    &   B_x - i B_y& i E_z & i E_x + E_y\\  B_x + i B_y &  -  B_z &  i E_x - E_y  & - i E_z\\  i E_z &i E_x +  E_y & B_z &    B_x - i B_y\\   i E_x -  E_y  &-i E_z &   B_x +i B_y &  - B_z\end{pmatrix}\label{em-matrix}$$
    となる。

-   これを見ると，4つの線形独立な成分が4回繰り返しでてくることがわかる。ということは，$4\times 4=16$成分でなく，$1\times 4$の一列で必要な情報をあらわすことができる。これをDirac方程式の波動関数と同様な形で
    $$\hat{\psi}_{EM}=\begin{pmatrix}   B_z \\ B_x + i B_y \\  i E_z \\   i E_x - E_y \\\end{pmatrix}$$
    と書こう。

-   これに Dirac 演算子を作用させると，電磁場の方程式を Dirac
    方程式とほぼ同じ形に書ける。簡単のために電流項がゼロの場合を考えると以下のようになる。
    $$\hat D \hat{\psi}_{EM}    = \hat{\gamma}^\mu\partial_\mu \hat{\psi}_{EM}=0$$
    このベクトル表現$\rightarrow1\times 4$行列表現の逆の操作で Dirac
    方程式の$1\times 4$行のDirac
    波動関数を逆にベクトル解析の表現にできる。

-   ところが，電磁場の場合は電場＋磁場で6成分なのに対し，Dirac
    場は複素4成分，つまり実数にすると8成分なので，2つ足りない。2ベクトルは6成分しか持つことができないので，あと2成分をつけくわえなければならない。

-   電磁場の行列表示 ([\[em-matrix\]](#em-matrix){reference-type="ref"
    reference="em-matrix"})
    をみると，「空席」があるのは$E_z$と$B_z$の，項がひとつだけの場所なので，そこに2つの変数$\alpha_0$と$\alpha_\omega$を押し込めばよい。具体的には6成分ある$4\times 4$行列に.$\hat 1 i\alpha_0$と$\hat{\gamma^0}\hat{\gamma^1}\hat{\gamma^2}\hat{\gamma^3}\alpha_\omega$を加えてやる。
    その結果，Dirac 場は電磁場
    ([\[em-matrix\]](#em-matrix){reference-type="ref"
    reference="em-matrix"})と同じような以下の行列に書ける。電磁場を連想するとわかりやすいので，各成分の記号には$\mathbf{E}$と
    $\mathbf{B}$を連想させるようなギリシャ文字をつかったが，もちろん，電磁場には関係ない。
    $$\hat{\mathcal{\psi}}=    \begin{pmatrix}     i \alpha_0 + \beta_z    &   \beta_x - i \beta_y                & \alpha_\omega + i \varepsilon_z & i \varepsilon_x + \varepsilon_y\\    \beta_x + i \beta_y &  - i \alpha_0  - \beta_z &  i \varepsilon_x - \varepsilon_y                  & \alpha_\omega  - i \varepsilon_z\\    \alpha_\omega + i \varepsilon_z &i \varepsilon_x +  \varepsilon_y &                     i \alpha_0  + \beta_z &    \beta_x - i \beta_y\\   i \varepsilon_x -  \varepsilon_y  &\alpha_\omega  -i \varepsilon_z &                     \beta_x +i \beta_y & i \alpha_0  - \beta_z    \end{pmatrix}    \label{dirac-matrix}$$

-   これと，電磁場の行列
    ([\[em-matrix\]](#em-matrix){reference-type="ref"
    reference="em-matrix"}) の対比によって，以下のような Dirac
    方程式のベクトル解析表現が得られる。ただし，質量項のあつかいはやっかいなので，ここでは質量なしの場合に限定した。
    $$\begin{aligned}
    \partial_t \alpha_0+\nabla\cdot\boldsymbol{\varepsilon}=0,~~~~\nabla \alpha_0+\partial_t \boldsymbol{\varepsilon} - \nabla\times \boldsymbol{\beta} = 0\\\partial_t \alpha_\omega+\nabla\cdot\boldsymbol{\beta} =0,~~~~\nabla \alpha_\omega+\partial_t \boldsymbol{\beta}  + \nabla\times\boldsymbol{\varepsilon} = 0\end{aligned}$$
    ここで Dirac場
    ([\[dirac-matrix\]](#dirac-matrix){reference-type="ref"
    reference="dirac-matrix"})は，ベクトルではなく，別の数学的構造である。これについては次章で議論しよう。

Discussions
===========

-   本稿では Klein-Gordon，Maxwell，Dirac
    の各方程式の時空間微分が，すべて Dirac
    演算子$\hat D$であらわされる同一の微分操作から導かれることをみた。ということは各方程式の違いは微分演算子ではなく，微分される方の場の性質から来るものと考えられる。

-   まず，Klein-Gordon 方程式と Maxwell
    方程式の違いだが，これは本稿でみたように，ベクトルの次数の違いである。Klein-Gordon
    方程式は1ベクトル，Maxwell 方程式は2ベクトルに Dirac
    演算子を作用させて得られる。

-   では，Dirac
    方程式の場はなんであろうか？　これはベクトルとは別物で，スピノルと呼ばれる。平坦な空間には並進と回転の2つの対称性があるが，ベクトルは並進に，スピノルは回転に対応すると考えられる。

-   スピノルをベクトルと区別するのであれば，Dirac
    方程式のベクトル解析表現を導出するときに書いたように，
    Dirac場の成分が体積ベクトルなどのベクトル場であるというのは不正確である。そこで$\gamma^0$や$\gamma^2\gamma^3$など，いままでベクトルとごっちゃにしていたものを，幾何代数の言葉をかりて，「ブレード
    (blade)」と呼ぼう。この呼び方だと$\gamma^2\gamma^3$はグレード2のブレードである。

-   そうすると，Klein-Gordon場はグレード１のブレードからなる1ベクトル，電磁場はそれぞれグレード２のブレードからなる2ベクトル，ということができる。それに対して，Dirac
    場はグレードがゼロ，2，4の三種類のグレードからできているスピノルということになる。つまり，ブレードというのは機械を構成する部品のようなものであり，ベクトルやスピノルは，その部品を使って組み立てた，使用目的をもった機械にたとえることができる。

-   ベクトルが平行移動に対応するのは直感的にわかるが，スピノルがどういう幾何学的意味をもつのかは，本稿の議論ではあきらかではない。Hestenes
    による
    Dirac方程式の幾何代数化（参考文献参照）などをみると，回転演算（rotor）かける振幅というあつかいになっているが，これについては別の機会に。

-   筆者は，ベクトルに1ベクトルや2ベクトルがあるように，1スピノルや2スピノルも考えられるように感じているが，具体的にはアイデアがない。諸賢のご教示を乞いたい。

Maxwell Equations with Dirac Bases {#maxwell-equations-with-dirac-bases .unnumbered}
==================================

すみません，準備中です。

参考文献 {#参考文献 .unnumbered}
========

Hestenes による幾何代数を使った各方程式の導出は

-   David Hestenes. Journal of Mathematical Physics,8(4): 1967.

-   David Hestenes. Journal of Mathematical Physics, 16:556, 1975.

-   David Hestenes. American Journal of Physics, 71(7):691, 2003.

幾何代数に関しては，21世紀にはいってから多くの解説や教科書が出ている。以下は筆者が参考にしたもので，物理
oriented
な読者にとってわかりやすいと思う。また，「幾何代数」や「クリフォード代数」でwwwを検索すると，日本語で良質の解説がいくつかみつかる。

-   Chris Doran, et al., In Advances in imaging and electron physics,
    volume 95, pp 271. Elsevier, 1996

-   Chris Doran, et al., Geometric algebra for physicists. Cambridge
    University Press, 2003.

-   Miroslav Josipovic. Geometric Multiplication of Vectors.
    Birkhaeuser,2019.

ベクトル解析の歴史については以下の本は面白かった。

-   Michael J. Crowe. A History of Vector Analysis: The Evolution of
    theIdea of a Vectorial System. Dover Reprints, 2015.
