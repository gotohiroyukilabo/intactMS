# 4. 抗体・抗原糖鎖の基礎：Fab糖鎖とO型糖鎖をintact MSでどう考えるか

## この資料の目的

この資料は、IgG試料に脱糖鎖酵素を加えてintact MS解析を行う人を対象に、次の問いに答えるための学習ノートである。

- 抗体のどこに、どのような糖鎖が結合するのか
- Fc N型糖鎖、Fab N型糖鎖、O型糖鎖をどう区別するか
- PNGase F処理後にも不均一性が残るとき、何を疑うべきか
- Fab糖鎖を取り切る条件と、O型糖鎖を処理する条件をどう最適化するか
- intact MSで測定する抗原タンパク質自身のN型・O型糖鎖をどう評価するか
- intact MSだけで言えることと、ペプチドマッピングが必要なことの境界はどこか

中心となる文献は、KrištićとLaucによる2024年の総説「The importance of IgG glycosylation—What did we learn after analyzing over 100,000 individuals」である。この総説が主に扱うのはヒト血漿IgGであり、以下の実験設計部分では、組換え抗体や治療用抗体の解析へ適用するために酵素特異性とMS上の注意を補足した。

> **最初に覚える要点**
>
> 1. IgG1、IgG2、IgG4は通常、FcのAsn297に2本のN型糖鎖を持つ。
> 2. ヒト血漿IgGの15～25%は、さらにFab可変領域にもN型糖鎖部位を持つ。
> 3. IgG3はFc N型糖鎖に加え、ヒンジにO型糖鎖を持ち得る。
> 4. PNGase FはアクセスできるN型糖鎖をFc/Fabの区別なく外すが、O型糖鎖は外さない。
> 5. 「PNGase F後にピークが残る」だけでは、O型糖鎖、Fab N型糖鎖の未消化、非糖鎖修飾を区別できない。
> 6. 抗原側の糖鎖は、抗体結合を妨げる場合、促進する場合、エピトープの一部になる場合がある。

---

## 1. N型糖鎖とO型糖鎖の違い

| 項目 | N型糖鎖 | O型糖鎖 |
|---|---|---|
| 結合するアミノ酸 | Asn | SerまたはThr |
| 結合原子 | Asn側鎖の窒素 | Ser/Thr側鎖の酸素 |
| 代表的な配列規則 | Asn-X-Ser/Thr（Xは通常Pro以外） | 単純な共通配列はない |
| IgGでの主な場所 | Fc Asn297、Fab可変領域、IgG3の一部アロタイプのAsn392 | IgG3ヒンジ |
| 代表的な除去酵素 | PNGase F、EndoS/EndoS2 | O-Glycosidase。シアル化時は通常Sialidaseも必要 |
| 処理後のタンパク質 | PNGase FではAsn→Asp、1サイト当たり約+0.984 Da | 糖鎖が外れればSer/Thr側鎖のOHに戻る |

N型糖鎖は共通の五糖コアを持つ。その上にGlcNAc、Gal、Fuc、Neu5Acなどが付加され、高マンノース型、ハイブリッド型、複合型に分かれる。IgG FcのAsn297では複合型の二本鎖糖鎖が主体である。

O型糖鎖はN型糖鎖のような共通コアを持たず、構造の種類が多い。IgG3ヒンジで報告されている主成分はmucin型のcore 1で、構造は次のとおりである。

`Galβ1-3GalNAc-Ser/Thr`

このcore 1には、シアル酸が0、1、または2残基付加し得る。

---

## 2. Fc Asn297 N型糖鎖：intact MSの基準となる糖鎖

IgG1、IgG2、IgG4では、各重鎖のCH2ドメインに保存されたAsn297があり、通常は抗体1分子当たり2本のN型糖鎖が結合する。総説では、Fc Asn297に30種類を超える糖鎖構造が存在すると整理されている。

ヒト血漿IgGの代表的な傾向は次のとおりである。

- Fc糖鎖のほとんどは複合型で、高マンノース型とハイブリッド型は合計1%未満
- 約35%がアガラクトシル化糖鎖
- 約65%が少なくともGalを持つ
- core Fucを持つ糖鎖が90%超
- bisecting GlcNAcを持つ糖鎖が約10～15%
- 同一IgGの2本の重鎖に、同じ糖鎖が付く場合と異なる糖鎖が付く場合がある

最後の点はintact MSで特に重要である。intact抗体の1本のピークは、2本のFc糖鎖の組合せを反映する。たとえばG0F/G1FとG1F/G0Fは質量だけでは同一であり、位置や左右の重鎖を区別できない。

### 糖鎖が抗体構造に必要な理由

Fc糖鎖は単なる質量付加ではない。総説では、Fc糖鎖がCH2ドメインの構造を安定化し、Fcγ受容体やC1qと相互作用できる配置を支えることがまとめられている。糖鎖を完全に除くとCH2領域が柔軟になり、Fcγ受容体との結合が大きく低下する。

したがって、脱糖鎖後の試料は「糖鎖だけがなく、元の立体構造は完全に同じ抗体」ではない。通常の変性LC-intact MSでは問題にならなくても、native MSや機能評価では区別が必要である。

---

## 3. Fab N型糖鎖：Fc糖鎖とは性質も消化のしやすさも違う

### 3.1 どこから生じるか

ヒト血漿IgGの15～25%は、Fab可変領域にもN型糖鎖部位を持つ。Fc Asn297のように全IgGで保存された部位ではなく、多くはB細胞の体細胞超変異によって新たな`Asn-X-Ser/Thr`配列が生じることで獲得される。

部位の位置と占有率は抗体ごとに異なる。したがって「Fab糖鎖あり」という情報だけでは、軽鎖か重鎖か、片腕か両腕か、何%が占有されるかは分からない。

### 3.2 Fc糖鎖との組成差

総説が整理したヒト血漿IgGでは、Fab N型糖鎖はFc N型糖鎖と比べて次の傾向を示す。

- bisecting GlcNAcが多い
- シアル酸が多く、二シアル化糖鎖も多い
- core Fucが少ない
- Galを少なくとも1残基持つものが大半
- 高マンノース型が約4%で、Fcより多い

したがって、シアル酸に由来する約291 Da間隔や、Galに由来する約162 Da間隔が目立つ不均一性は、Fab糖鎖を疑う手掛かりになる。ただし、質量差だけでFab由来と断定してはいけない。

### 3.3 生物学的な意味

Fab糖鎖は、位置と抗体によって抗原結合を増強、低下、または変化させない場合がある。抗原特異性、交差反応性、抗体安定性にも影響し得る。またFab糖鎖はFcRnとの結合を立体的に妨げ、胎盤輸送に影響する可能性が示されている。

つまり、Fab糖鎖は「Fc糖鎖の取り残し」ではなく、抗体の性質を変え得る独立した品質特性である。

### 3.4 Fab糖鎖がPNGase Fで切れにくい理由

PNGase Fは原理上、FcとFabのN型糖鎖を区別しない。しかしnative抗体では、糖鎖部位の立体的な露出度が反応速度を左右する。Fab糖鎖が可変領域の内側やドメイン境界に近い場合、Fc糖鎖が消えてもFab糖鎖が残ることがある。

Fab糖鎖の完全除去を確認するときは、次を段階的に検討する。

1. 反応時間を延ばす
2. 酵素/基質比を上げる
3. 前処理温度を上げて糖鎖部位を露出させる
4. 還元または変性条件を用いる
5. 還元intact MSで重鎖と軽鎖を分け、どちらに糖鎖があるか確認する
6. 最終的にはペプチドマッピングで部位と占有率を確認する

Native PNGase F条件で残ったピークを、ただちにO型糖鎖と判断しないことが重要である。

---

## 4. IgG3のO型糖鎖

### 4.1 どこに結合するか

IgG3のヒンジは他のIgGサブクラスより約4倍長い。総説では、Thr122、Thr137、Thr152の3部位にO型糖鎖が報告され、各部位の占有率は約10%とされている。番号は配列・アロタイプ・番号付け規則で確認する。

IgG3ヒンジの主なO型糖鎖はcore 1である。

| 構造 | 残基組成 | 参考質量差 |
|---|---:|---:|
| core 1 | Hex1HexNAc1 | 約365.13 Da |
| シアル化core 1 | Hex1HexNAc1Neu5Ac1 | 約656.23 Da |
| 二シアル化core 1 | Hex1HexNAc1Neu5Ac2 | 約947.32 Da |

質量は単糖の残基質量を用いた組成上の目安であり、装置のデコンボリューション、平均質量/モノアイソトピック質量の設定、付加イオンによって見え方が変わる。

### 4.2 何が分かっていて、何が未解明か

IgG3 O型糖鎖の機能は、Fc Asn297糖鎖に比べてほとんど分かっていない。総説では、次が仮説として挙げられている。

- ヒンジをプロテアーゼ切断から保護する
- 長いヒンジを伸びた構造に保つ
- IgG3のFab間距離と柔軟性に寄与する

これらは確立した機能としてではなく、限られたデータに基づく可能性として理解する。

### 4.3 O-Glycosidaseだけでは取れない場合がある

一般的なO-Glycosidaseは、非修飾のcore 1を基質にする。末端にシアル酸が付いていると反応しにくいため、通常は先にSialidase/Neuraminidaseでシアル酸を外す。

推奨する考え方は次の順序である。

`シアル酸除去 → core 1露出 → O-Glycosidaseでcore 1除去`

ただし、O型糖鎖は構造多様性が高い。O-Glycosidaseで質量シフトが出なくても、次の可能性が残る。

- core 1以外の構造
- シアル酸除去が不完全
- 酵素が届きにくい
- 単独GalNAc（Tn抗原）など、使用酵素の基質外
- 実際にはO型糖鎖ではなく、酸化、糖化、C末端Lys、クリッピングなど別の修飾

したがって、陰性結果は「O型糖鎖なし」ではなく「この条件と酵素では除去を検出できなかった」と解釈する。

---

## 5. intact MSで役立つ質量差

| 残基・反応 | 参考質量差 | 主な解釈 |
|---|---:|---|
| Hex | 162.0528 Da | GalまたはManの増減 |
| HexNAc | 203.0794 Da | GlcNAcまたはGalNAcの増減 |
| Fuc | 146.0579 Da | Fucの増減 |
| Neu5Ac | 291.0954 Da | シアル酸の増減 |
| core 1（Hex+HexNAc） | 365.1322 Da | O型core 1候補 |
| PNGase F後のAsn→Asp | +0.9840 Da/site | N型糖鎖除去のタンパク質側変化 |

質量差は構造の候補を絞るための情報であり、結合位置や異性体を確定する情報ではない。たとえばHex1HexNAc1の差が見えても、intact MS単独では、それがIgG3ヒンジのcore 1か、別の組成差の組合せかを完全には証明できない。

---

## 6. Fab N型糖鎖とO型糖鎖を切り分ける並列実験

同じ試料から分注した並列反応を使う。酵素を順番に足し続ける方法は、先の反応で残った糖残基が次の酵素の基質にならない場合があるため、原因切り分けには不向きである。

| 条件 | 処理 | 主に分かること |
|---|---|---|
| A | 未処理 | 全不均一性の基準 |
| B | Bufferのみ、酵素なし | 加熱、pH、Bufferによる変化 |
| C | EndoS2 | Fc N型糖鎖を単純化した後に残るFab N型糖鎖＋O型糖鎖＋非糖鎖修飾 |
| D | PNGase F、十分な変性/露出条件 | FcとFabを含むN型糖鎖を除いた後の不均一性 |
| E | Sialidaseのみ | N型とO型を合わせたシアル酸寄与 |
| F | Sialidase＋O-Glycosidase | 除去可能なO型core 1の寄与。ただしN型糖鎖は残る |
| G | PNGase F＋Sialidase＋O-Glycosidase | N型糖鎖と除去可能なO型core 1を除いたバックボーン |

### 比較の読み方

- **Cで残り、Dで消える成分**：Fab N型糖鎖の可能性が高い
- **Dで残り、Gで消える成分**：除去可能なO型糖鎖の可能性が高い
- **Eで約291 Da単位に収束する成分**：シアル酸を含む糖鎖の可能性が高い
- **Gでも残る成分**：酵素耐性糖鎖、未消化、または非糖鎖修飾を検討

EndoS2はIgG Fcを認識してN型糖鎖のchitobiose core内部を切り、タンパク質側にGlcNAc±core Fucを残す。PNGase Fのように糖鎖全体をAsnから外す反応ではないため、EndoS2処理物とPNGase F処理物の絶対質量は一致しない。

### 位置をさらに絞る方法

- **還元intact MS**：Fab糖鎖が重鎖か軽鎖かを絞る
- **IdeSなどによるsubunit解析**：Fc/2とF(ab')2側を分ける
- **ペプチドマッピング**：結合部位、糖鎖組成、site occupancyを決定する
- **O-glycoproteaseを用いた解析**：O型糖鎖部位のマッピングに使う。ただしタンパク質を切断するので、完全長intact質量の単純化用途とは分ける

---

## 7. 酵素最適化の進め方

### 7.1 最適化前に固定するもの

反応条件を振る前に、次を固定する。

- 抗体濃度と反応液量
- 酵素量の表し方（U/µg、µL/µg、またはメーカー定義のreaction/µg）
- 反応後の停止・buffer exchange法
- LC-MS注入量
- デコンボリューション範囲、質量幅、S/N閾値
- 未処理対照、Buffer対照、酵素ブランク

反応収率とMS応答を混同しないため、全条件を同じ後処理と注入量で比較する。

### 7.2 PNGase F：Fab糖鎖を取り切る最小検討

まずFc糖鎖が容易に外れる条件を基準にし、Fab糖鎖が残る試料だけ条件を強くする。

| 因子 | 低 | 中 | 高 |
|---|---|---|---|
| 酵素/基質比 | 0.5× | 1× | 2× |
| 反応時間 | 10～30分 | 1～2時間 | overnight |
| 前処理 | なし | 穏やかな加熱 | 製品推奨の高温前処理または変性 |

一度に全組合せを試すより、次の順に進める。

1. 標準条件でFc除去とFab残存を確認
2. 時間延長と酵素増量を比較
3. それでも残る場合だけ前処理温度または変性を追加
4. 完全消化を達成した中で、回収率が高く、凝集・fragmentが少ない最も穏やかな条件を採用

Native構造を維持したい目的と、完全N脱糖鎖バックボーンを得たい目的は分ける。Fab糖鎖を完全に外すための加熱・変性条件は、native性を損なう可能性がある。

### 7.3 O型糖鎖：二段階反応として最適化する

O型糖鎖は、Sialidase工程とO-Glycosidase工程を分けて評価する。

1. **Sialidase量と時間を最適化**

   約291 Da単位のシアル酸由来ピークが収束するかを見る。
2. **O-Glycosidase量と時間を最適化**

   desialylated core 1に相当する約365 Da単位の差が消えるかを見る。
3. **同時添加と逐次添加を比較**

   Buffer互換性がある場合でも、逐次添加の方が律速工程を見つけやすい。
4. **PNGase F併用条件を確認**

   N型糖鎖由来の複雑さを先に除くと、O型糖鎖の反応評価が容易になる。

### 7.4 合否判定の例

最適条件は「最小ピーク数」だけで決めない。事前に合否基準を置く。

- 目的の未消化glycoformが総ピーク面積の5%未満
- 主成分の質量誤差が装置・メソッドの許容範囲内
- 回収率が未処理対照の80%以上
- 新規fragment、共有結合性aggregate、沈殿が許容範囲内
- 反復間の未消化率と主ピーク面積が再現する

5%と80%は開始時の例であり、分析目的と装置性能に合わせて設定する。

---

## 8. よくある誤読と対処

### PNGase F後にも162 Daまたは291 Da間隔が残る

Fab N型糖鎖の未消化、O型糖鎖、糖化などを候補にする。EndoS2と十分に変性したPNGase Fの並列比較、Sialidase処理で切り分ける。

### O-Glycosidaseを加えたのに変化がない

シアル酸除去不足、core 1以外、酵素アクセス不足、そもそも非糖鎖修飾、の順で確認する。O-Glycosidase陰性だけでO型糖鎖を否定しない。

### EndoS2後に糖鎖らしいピークが残る

想定内である。Fab N型糖鎖とO型糖鎖は残り、FcにもGlcNAc±Fucが残る。EndoS2は完全なN脱糖鎖酵素ではない。

### intact MSで糖鎖結合部位を決めたい

intact MSは組成差と全体分布には強いが、位置決定には限界がある。還元intact、subunit、ペプチドマッピングへ段階的に分解する。

### IgG1試料でO型糖鎖を疑っている

この総説では、通常のIgG1、IgG2、IgG4にO型糖鎖は報告されず、IgG3ヒンジが主対象である。まずサブクラス、配列、発現系、融合パートナー、非標準配列を確認し、Fab N型糖鎖の未消化と非糖鎖修飾を優先して除外する。

---

## 9. 実務用チェックリスト

### 試料情報

- [ ] IgGサブクラスとアロタイプを確認した
- [ ] 重鎖・軽鎖配列からN型糖鎖sequonを検索した
- [ ] IgG3ヒンジ、融合パートナー、非標準配列のSer/Thr-rich領域を確認した
- [ ] 発現宿主を確認した

### 反応対照

- [ ] 未処理対照がある
- [ ] Bufferのみ対照がある
- [ ] 酵素ブランクがある
- [ ] EndoS2とPNGase Fを別アリコートで比較した
- [ ] O型糖鎖評価ではSialidase単独条件を置いた

### MS評価

- [ ] 糖残基の質量差だけで部位を断定していない
- [ ] 未消化率だけでなく回収率も見た
- [ ] aggregate、fragment、沈殿を確認した
- [ ] 必要に応じて還元intactまたはsubunit解析を行った
- [ ] 最終確認が必要な場合はペプチドマッピングを計画した

---

## 10. 抗原タンパク質自身に結合するN型・O型糖鎖

ここでいう「抗原糖鎖」は、抗体に結合する遊離糖鎖ではなく、intact MSの測定対象となる抗原タンパク質に共有結合した糖鎖を指す。抗体側のFab糖鎖とは別の変数として扱う。

### 10.1 抗原糖鎖が抗体結合へ与える3種類の影響

抗原上の糖鎖と抗体結合の関係は、次の3つに分けて考える。

1. **糖鎖がエピトープを覆う**

   糖鎖がペプチド表面への接近を妨げる。この場合、脱糖鎖によって抗体結合が増える可能性がある。
2. **糖鎖がエピトープの一部になる**

   抗体が糖鎖そのもの、または糖鎖とペプチドを合わせたglycopeptide epitopeを認識する。この場合、脱糖鎖すると結合が低下または消失する。
3. **糖鎖が抗原の立体構造を間接的に支える**

   抗体が糖鎖へ直接接触しなくても、糖鎖除去によって抗原が変性または局所的に構造変化し、結合が変わることがある。

したがって、脱糖鎖前後の結合差だけから「抗体が糖鎖を直接認識する」とは断定できない。直接認識、steric masking、構造変化を切り分ける必要がある。

HIV Envでは、N型糖鎖がprotein epitopeを覆うglycan shieldを形成する一方、一部の広域中和抗体はN型糖鎖を含むエピトープを認識する。MUC1では、O型糖鎖が抗体との直接接触に加え、ペプチド部分の構造平衡を変えることで結合性に影響する例が報告されている。

### 10.2 抗原のN型糖鎖

抗原タンパク質でも、基本的なN型糖鎖付加規則は`Asn-X-Ser/Thr`（Xは通常Pro以外）である。ただし、配列中にsequonがあっても必ず占有されるとは限らない。

N型糖鎖の解析では、次の3段階を分けて考える。

- **macroheterogeneity**：部位が占有される分子と、占有されない分子が混在する
- **microheterogeneity**：同じ部位に異なる糖鎖構造が付く
- **site combination**：複数部位の占有状態と糖鎖構造が組み合わさる

N型糖鎖部位が多い抗原では、intact質量だけから個々のglycoformを一意に割り当てることが急速に難しくなる。たとえばSARS-CoV-2 spikeには1 protomer当たり22個のN型糖鎖sequonがあり、HIV Env trimerには約90本のN型糖鎖が存在する。このような抗原では、intact MSは全体分布、脱糖鎖前後の質量差、主要集団の比較には使えるが、部位別構造の決定にはglycopeptide解析が必要である。

### 10.3 抗原のO型糖鎖

抗原のO型糖鎖は、IgG3に限定されない。分泌タンパク質、膜タンパク質、mucin、ウイルス表面タンパク質、linkerを含む融合タンパク質など、多様な抗原に存在し得る。

O-GalNAc型糖鎖はSer/Thrに結合し、N型糖鎖のような単純な共通sequonを持たない。次の特徴を持つ領域では候補として優先する。

- Ser/Thrが集中する領域
- Proが多い、構造的に柔軟な領域
- mucin-like領域
- signal peptide通過後に細胞外へ分泌される領域
- 人工linker、特にSerを含むlinker
- プロテアーゼ切断部位の近傍

ただし、配列だけでsite occupancyや糖鎖構造を確定することはできない。

抗原O型糖鎖ではcore 1以外にも、core 2、core 3、Tn、sialyl-Tn、O-mannose、O-fucose、O-glucose、glycosaminoglycan結合型などを考える必要がある。一般的なO-Glycosidaseが除去できるのは主にdesialylated core 1/core 3であり、「O型糖鎖全般を外す酵素」ではない。

### 10.4 発現宿主から予想する

抗原糖鎖は、アミノ酸配列だけでなく、発現宿主、細胞株、培養条件、立体構造、精製工程に依存する。同じHEK293発現抗原でも製造条件や供給元によってsite-specific glycan profileが異なることが報告されている。

| 発現・由来 | 想定する糖鎖 | intact MSでの注意 |
|---|---|---|
| ヒト組織・血漿由来 | 複合型N糖鎖、mucin型O糖鎖など | ドナー、組織、疾患状態による不均一性 |
| CHO、HEKなど哺乳類細胞 | 複合型、ハイブリッド型、高マンノース型N糖鎖、O-GalNAc型 | 細胞株と培養条件で末端Gal、Sia、Fucが変わる |
| 昆虫細胞 | paucimannose、高マンノース、core Fucを含むN糖鎖など | core α1-3 FucがあるとPNGase F耐性になり得る |
| 植物 | core α1-3 Fuc、β1-2 Xylを含むN糖鎖など | PNGase Fで外れないN糖鎖を考える |
| 酵母 | 高マンノース/過マンノース型N糖鎖、O-mannose型 | 哺乳類O-Glycosidaseの適用範囲外になりやすい |
| 大腸菌 | 通常は真核生物型N/O糖鎖を付加しない | glycoengineered株、培地由来adduct、非酵素的糖化は別途確認 |

「同じ抗原配列だから同じ質量分布になる」とは限らない。ロット比較では発現宿主だけでなく、細胞株、培養条件、construct、精製法も記録する。

### 10.5 Fc-fusion抗原は糖鎖の由来を分けて考える

Fc-fusion抗原では、少なくとも次の3領域が糖鎖を持ち得る。

- IgG Fc Asn297のN型糖鎖
- 抗原ドメイン自身のN型/O型糖鎖
- hingeまたはlinkerのO型糖鎖

Serを含むGS linkerを使用したCHO産Fc-fusionで、予期しないO型糖鎖やglycosaminoglycan型修飾が検出された報告がある。PNGase F後にもlinker由来の不均一性が残る可能性がある。

Fc-fusionでは、別アリコートをEndoS2処理するとFc N型糖鎖を選択的に単純化できる。EndoS2後にも残る糖鎖様不均一性は、抗原ドメイン、linker、O型糖鎖、または非糖鎖修飾に由来する可能性が高くなる。

### 10.6 抗原糖鎖を切り分ける並列実験

抗原試料でも、同一試料から分けた並列反応を基本にする。

| 条件 | 処理 | 主に評価できること |
|---|---|---|
| A | 未処理 | 抗原全体の不均一性 |
| B | Bufferのみ | 加熱、pH、界面活性剤による変化 |
| C | PNGase F、native条件 | 表面に露出したN型糖鎖 |
| D | PNGase F、変性条件 | N型糖鎖の完全除去に近い陽性対照 |
| E | Endo H | 高マンノース型と一部ハイブリッド型N糖鎖の寄与 |
| F | Sialidase | N型/O型を合わせた末端シアル酸の寄与 |
| G | Sialidase＋O-Glycosidase | 除去可能なcore 1/core 3 O型糖鎖 |
| H | PNGase F＋Sialidase＋O-Glycosidase | N型糖鎖と除去可能な短いO型糖鎖を除いたバックボーン |
| I | EndoS2、Fc-fusionのみ | Fc N型糖鎖と抗原/linker糖鎖の切り分け |

#### 比較の読み方

- **Cで一部残り、Dで消える**：N型糖鎖への立体アクセスが不十分
- **Eで消える成分**：高マンノース型またはEndo H感受性hybrid型の可能性
- **Fで約291 Da単位に収束する**：Neu5Acを含む糖鎖の可能性
- **Dで残り、Hで消える**：除去可能なO型糖鎖の可能性
- **Gで変化せず、O型糖鎖が疑われる**：core 1/core 3以外、シアル酸除去不足、酵素アクセス不足を検討
- **IでFc由来分だけ単純化する**：残りを抗原ドメイン/linker側の候補として調べる
- **Hでも残る**：非対応糖鎖、未消化、糖化、酸化、リン酸化、硫酸化、切断、adductを検討

PNGase F処理後の約+0.984 Da/siteは、糖鎖除去時のAsn→Asp変換に由来する。複数サイトを持つ抗原では理論aglyco massへこの差を加える必要がある。

### 10.7 糖鎖と糖化を混同しない

約+162 Da差はHex残基の差を示唆するが、酵素的な糖鎖だけでなく、還元糖がLysやN末端へ非酵素的に付加する糖化でも生じる。

- PNGase Fで消える：N型糖鎖由来を支持
- O-Glycosidase系で消える：対応するO型糖鎖由来を支持
- どちらでも消えない+162 Da：糖化、酵素耐性糖鎖、別修飾を検討

糖残基の質量差だけでglycosylationと判定しない。

### 10.8 抗原結合評価とMS用脱糖鎖処理を分ける

完全脱糖鎖バックボーンを得るための変性処理は、抗原の立体構造や抗体結合能を破壊し得る。次の2目的を分ける。

1. **分析上の質量単純化**

   変性条件を含め、完全消化を優先する。
2. **糖鎖が抗体結合へ与える影響の評価**

   native性を保てる条件を使用し、未処理、Buffer対照、酵素処理を比較する。反応後は酵素とBufferを除去し、抗原濃度と回収率をそろえて結合測定する。

結合評価では少なくとも次を確認する。

- SECなどでaggregateとmonomer回収率を確認
- 同一濃度へ補正
- 抗体結合だけでなく、既知のconformation-sensitive抗体または受容体結合も確認
- PNGase F、Sialidase、O-Glycosidaseごとの単独条件を置く
- 糖鎖を戻せないため、可能ならglycoengineered抗原やsite mutantで直交検証する

### 10.9 intact MSで分かることと分からないこと

#### intact MSで比較的分かりやすいこと

- 糖鎖を含む総質量分布
- 酵素処理による全体の質量変化
- 主要glycoform間のHex、HexNAc、Fuc、Neu5Ac単位の差
- ロット間、発現宿主間、処理条件間の全体比較
- 完全脱糖鎖バックボーンの質量確認

#### intact MS単独では決めにくいこと

- どの部位にどの糖鎖が付いているか
- 同一組成の構造異性体と結合様式
- 複数部位間の糖鎖分布
- 糖鎖が抗体と直接接触しているか
- O型糖鎖の正確なsite occupancy

多部位抗原では、intact MSで全体像を把握した後、subunit解析、glycopeptide mapping、released glycan解析、必要に応じてETD/EThcDを用いたO-glycosite解析へ進む。

---

## 11. まとめ

- Fc Asn297 N型糖鎖はIgGの基本糖鎖で、抗体1分子に通常2本あり、組合せのためintact質量は複雑になる。
- Fab N型糖鎖はヒト血漿IgGの15～25%に存在し、Fcよりシアル化・bisectingが多い。抗体ごとに部位とアクセス性が異なる。
- IgG3ヒンジには低占有率のcore 1 O型糖鎖があり、0～2残基のシアル酸を持ち得る。
- EndoS2はFc N型糖鎖を選択的に単純化し、PNGase Fはアクセス可能なFc/Fab N型糖鎖を除去する。O型糖鎖は別処理が必要である。
- O型糖鎖の処理は、Sialidaseで末端シアル酸を外してからO-Glycosidaseを作用させる。
- 最適化では、未処理、Buffer、EndoS2、PNGase F、Sialidase、O-Glycosidaseの並列条件を置き、消化率、回収率、fragment/aggregateを同時に評価する。
- intact MSで構造候補を絞り、位置と占有率の確定にはsubunit解析またはペプチドマッピングを使う。
- 抗原側の糖鎖はエピトープを隠す場合、エピトープの一部になる場合、抗原構造を支える場合があり、脱糖鎖による結合変化の方向は一様ではない。
- 抗原糖鎖は配列だけでなく発現宿主、細胞株、construct、培養条件に依存する。Fc-fusionではFc、抗原ドメイン、linkerを分けて評価する。

---

## 関連するリポジトリ内資料

- [2. 脱糖鎖酵素のプロファイリング](./02_脱糖鎖酵素のプロファイリング.md)
- [3. PNGase FとRapid PNGase Fの違い](./03_PNGase_FとRapid_PNGase_Fの違い.md)

## 参考文献・資料

### 中心文献

- Krištić J, Lauc G. [The importance of IgG glycosylation—What did we learn after analyzing over 100,000 individuals](https://doi.org/10.1111/imr.13407). *Immunological Reviews*. 2024;328(1):143-170. PMID: 39364834; PMCID: PMC11659926.
- [PubMedレコード](https://pubmed.ncbi.nlm.nih.gov/39364834/)
- [PMC全文](https://pmc.ncbi.nlm.nih.gov/articles/PMC11659926/)

### 酵素処理と解析設計の補足

- New England Biolabs. [PNGase F Protocol](https://www.neb.com/en-sg/protocols/pngase-f-protocol). Native基質では長時間または酵素増量が必要になり得ること、変性条件を完全消化の陽性対照にすることが示されている。
- New England Biolabs. [O-Glycosidase](https://www.neb.com/en-us/products/p0733-o-glycosidase). Core 1/Core 3の基質特異性と、Neuraminidase併用の必要性が示されている。
- Albert H, Collin M, Dudziak D, Ravetch JV, Nimmerjahn F. [In vivo enzymatic modulation of IgG glycosylation inhibits autoimmune disease in an IgG subclass-dependent manner](https://doi.org/10.1073/pnas.0808248105). *PNAS*. 2008.
- Trastoy B, Du JJ, Cifuente JO, et al. [Mechanism of antibody-specific deglycosylation and immune evasion by Streptococcal IgG-specific endoglycosidases](https://doi.org/10.1038/s41467-023-37215-3). *Nature Communications*. 2023.
- Collin M, Olsén A. [EndoS, a novel secreted protein from Streptococcus pyogenes with endoglycosidase activity on human IgG](https://pubmed.ncbi.nlm.nih.gov/11406581/). *EMBO Journal*. 2001.

### 抗原糖鎖と抗体結合・intact MSの補足

- Watanabe Y, Allen JD, Wrapp D, McLellan JS, Crispin M. [Site-specific glycan analysis of the SARS-CoV-2 spike](https://doi.org/10.1126/science.abb9983). *Science*. 2020. Spike 1 protomer当たり22個のN型糖鎖sequonと、部位ごとの糖鎖processingが解析されている。
- Cao L, Diedrich JK, Kulp DW, et al. [Global site-specific N-glycosylation analysis of HIV envelope glycoprotein](https://doi.org/10.1038/ncomms14954). *Nature Communications*. 2017. 多数のN型糖鎖部位を持つ抗原で、Endo HとPNGase Fの反応痕跡を利用したsite-specific解析が示されている。
- Andrabi R, Su CY, Liang CH, et al. [Glycans function as anchors for antibodies and help drive HIV broadly neutralizing antibody development](https://doi.org/10.1016/j.immuni.2017.08.006). *Immunity*. 2017. 抗原N型糖鎖が抗体エピトープの一部として働く例。
- Movahedin M, Brooks TM, Supekar NT, et al. [Glycosylation of MUC1 influences the binding of a therapeutic antibody by altering the conformational equilibrium of the antigen](https://doi.org/10.1093/glycob/cww131). *Glycobiology*. 2017. 抗原O型糖鎖がglycopeptide構造と抗体結合へ影響する例。
- Spahr C, Shi SDH, Lu HS. [O-Glycosylation of glycine-serine linkers in recombinant Fc-fusion proteins](https://doi.org/10.4161/mabs.28763). *mAbs*. 2014. CHO産Fc-fusionのGS linkerに、予期しないO型糖鎖・glycosaminoglycan型修飾が生じた例。
- Goecker ZC, Burke Harris M, Remoroza C, et al. [Variation of site-specific glycosylation profiles of recombinant influenza glycoproteins](https://doi.org/10.1016/j.mcpro.2024.100827). *Molecular & Cellular Proteomics*. 2024. 同じHEK293発現でも、製造された組換えHA/neuraminidaseのsite-specific N型糖鎖が異なり得ることを示す。
