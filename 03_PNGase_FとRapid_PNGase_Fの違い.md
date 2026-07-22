# 3. PNGase FとRapid PNGase Fの違い

## 3製品の比較

| 項目 | 通常型PNGase F P0709 | Rapid PNGase F P0710 | Rapid PNGase F Non-Reducing P0711 |
|---|---|---|---|
| 主用途 | 汎用N型糖鎖除去 | 高速N糖鎖遊離・プロファイリング | 非還元intact抗体の高速脱糖鎖 |
| 酵素 | 組換えPNGase F | 組換えPNGase F | 組換えPNGase F |
| 切断対象 | 高マンノース、ハイブリッド、複合型 | 基本的に同じ | 基本的に同じ |
| 切断できない代表例 | core α1-3 Fuc | 同左 | 同左 |
| 標準反応 | 37℃・1～24時間 | 50℃・10分 | 75℃・5分前処理→50℃・10分 |
| Fab糖鎖 | Native条件では切れにくい場合がある | 80℃・2分前処理で改善 | Cetuximabで検証済み |
| ジスルフィド保持 | 条件依存 | 保持を目的とした製品ではない | 保持を目的に再製剤化 |
| バッファー | 50 mM sodium phosphate、pH 7.5 | 専用5×Buffer、組成非公開 | 専用非還元5×Buffer、組成非公開 |
| 活性表示 | 500 U/µL | 1 reaction/µL | 1 reaction/µL |
| MS適合性 | Glycerol-free製品を推奨 | 反応成分はMS対応、反応後buffer exchange推奨 | 同左 |

## 触媒反応そのものは基本的に同じ

いずれもN型糖鎖の最内側GlcNAcとAsnの間を切断し、糖鎖全体を遊離する。反応後はAsnがAspとなり、タンパク質側に1サイト当たり約+0.984 Daの変化が残る。

Rapid型は、通常型では切れない糖鎖を新しく切れる酵素ではない。主な違いは、反応時間、バッファー、酵素量、加熱による基質の露出、抗体での製品検証である。

## 「改良された組換え酵素」とは何か

NEBはRapid PNGase Fを“improved recombinant reagent”と表現しているが、以下は公開していない。

- 通常型P0709とのアミノ酸配列差
- 具体的な変異部位
- 耐熱化変異の有無
- 通常型との比活性比較
- 37～50℃での失活速度
- `kcat`、`Km`、`kcat/Km`
- タンパク質濃度

したがって、「特定のアミノ酸変異によって耐熱性と触媒速度を上げた酵素」とは断定できない。

また、通常型P0709自体もElizabethkingia miricola由来遺伝子を大腸菌で発現した組換え酵素である。通常型対Rapid型は、天然酵素対組換え酵素という比較ではない。

## 高速化に寄与していると考えられる要素

NEBの関連特許では、短時間反応を実現する要素として次が示されている。

- 45～50℃の加熱
- DTTまたはTCEPによる還元
- ラウロイルサルコシンなどのカルボキシル化アニオン界面活性剤
- デオキシコール酸などの胆汁酸塩
- 高濃度の組換えPNGase F
- 必要に応じた70～80℃の基質前処理

特許例では、界面活性成分を加えることで、完全脱糖鎖に必要なPNGase F量が20～90倍以上減少した。また、実験には8,000 U/µLの組換えPNGase Fが用いられた。

ただし、これは関連特許の実施例であり、現在のRapid Buffer B0718の組成が同一であることを意味しない。現在のBuffer組成は非公開である。

このことから、Rapid化の中心は次の組み合わせである可能性が高い。

1. 抗体の部分変性によって糖鎖を露出させる
2. PNGase Fが働ける範囲で温度を上げる
3. 十分な酵素量を使用する
4. 専用Bufferで基質アクセス性と酵素活性を両立する

## 通常型PNGase Fを加熱すればよいのか

試す価値は十分にある。

通常型PNGase Fを用いた報告では、45℃・1時間で得られた糖鎖プロファイルは37℃・16時間とほぼ同等だった。一方、55℃では50℃より糖鎖遊離量が低く、加熱しすぎると酵素失活が優位になることが示されている。

| 条件 | 予想される結果 |
|---|---|
| 37℃・overnight | 確実だが遅い |
| 45℃・30～60分 | 通常型でも高速化が期待できる |
| 50℃・10～60分 | 基質によって有効。酵素失活との競合あり |
| 55℃以上 | 失活リスクが増える |
| 75～80℃で酵素と同時加熱 | PNGase Fが失活するため不適切 |

80℃前処理を行う場合は、抗体とバッファーだけを加熱し、冷却してから酵素を添加する。

ただし、「通常型＋50℃」だけでRapid型と同じ結果になるとは限らない。酵素濃度、専用Buffer、抗体糖鎖へのアクセス性、製品ごとの熱安定性が異なる可能性がある。

## 酵素とバッファーの寄与を切り分ける実験

| 条件 | 酵素 | バッファー | 温度・時間 | 分かること |
|---|---|---|---|---|
| A | P0709 | GlycoBuffer 2 | 37℃・16時間 | 通常型基準 |
| B | P0709 | GlycoBuffer 2 | 45℃・1時間 | 加熱だけの効果 |
| C | P0709 | GlycoBuffer 2 | 50℃・10、30分 | Rapid相当温度の効果 |
| D | P0709 | Rapid Buffer | 50℃・10分 | Bufferの寄与 |
| E | Rapid P0710 | GlycoBuffer 2 | 50℃・10分 | Rapid酵素製剤側の寄与 |
| F | Rapid P0710 | Rapid Buffer | 50℃・10分 | Rapid標準条件 |

DとEはメーカー推奨外だが、機構を切り分ける研究目的では意味がある。Rapid型は活性単位が非公開なので、通常型との厳密な等活性比較はできない。通常型側を125、250、500 Uなどで用量系列にする。

## 80℃・2分前処理による抗体への影響

80℃・2分は、抗体にとって「影響がない温度」ではない。少なくとも一部ドメインの立体構造を崩し、Fab糖鎖をPNGase Fへ露出させるための処理である。

抗体は複数ドメインからなり、一般にはCH2、Fab、CH3が異なる温度で変性する。CH2は最も不安定で、80℃では複数ドメインが変性領域に入る抗体が多い。

| 影響 | 可能性 | intact MSへの影響 |
|---|---|---|
| 二次・三次構造の変性 | 高い | Denaturing MSでは問題になりにくい |
| 抗原結合活性低下 | あり得る | 質量測定だけなら通常は不問 |
| 可溶性凝集体 | 抗体、濃度、Buffer依存 | 回収率低下、ピーク減少 |
| 沈殿 | 条件依存 | 特定分子種が失われ結果が偏る |
| ジスルフィド切断・交換 | 還元剤依存 | H鎖・L鎖構成に影響 |
| 酸化、脱アミド、異性化 | 2分では比較的小さいがゼロではない | 微小質量差、charge variant |
| ペプチド結合切断 | 中性付近・2分では一般に限定的 | 新規低分子fragment |

### 測定目的による許容度

#### 還元intact MS

その後TCEPで還元する場合、80℃によるNative立体構造の喪失は大きな問題になりにくい。確認すべきなのは、沈殿、回収率低下、共有結合性凝集、H/L鎖fragment、余分な化学修飾である。

#### 非還元intact MS

ジスルフィドが残ってもNative構造が保たれたとは限らない。通常の逆相LC-MSでは測定時に変性するため、熱処理による立体構造変化をスペクトルだけでは検出できない。

#### Native MSまたは機能評価

80℃処理は原則として避ける。さらに、N糖鎖を除去すること自体がCH2ドメインの安定性やFc機能を変えるため、加熱を避けても未処理抗体と同じ機能状態ではない。

## 80℃処理の影響を確認する最小実験

| 条件 | 加熱 | 酵素 | 評価目的 |
|---|---|---|---|
| A | なし | なし | 未処理基準 |
| B | 80℃・2分＋50℃・10分 | なし | 熱＋Bufferの影響 |
| C | 50℃・10分 | Rapid PNGase F | 80℃なしで切れるか |
| D | 80℃・2分＋50℃・10分 | Rapid PNGase F | 完全脱糖鎖条件 |

CでFab糖鎖まで完全に切れるなら80℃処理は不要である。Dでのみ完全に切れる場合は、AとBを比較して加熱による回収率低下や異常分子種を確認する。

完全脱糖鎖できる最低温度を探すため、次の系列も有効である。

- 前処理なし、50℃・10、30、60分
- 60℃・5分前処理
- 65℃・5分前処理
- 70℃・2または5分前処理
- 75℃・2分前処理
- 80℃・2分前処理

## 構造影響の確認法

- 非還元CE-SDS：H鎖・L鎖接続、fragment、共有結合性凝集体
- SEC-UVまたはSEC-MALS：可溶性凝集体、モノマー回収率
- nanoDSF/DSC：立体構造、熱安定性
- DLS：粒径、凝集
- BLI/SPR/ELISA：抗原結合能
- ペプチドマッピング：酸化、脱アミド、ジスルフィド交換

2 µgスケールでこれらが難しい場合、初期評価だけ20～100 µg程度でまとめて処理し、構造評価用試料を確保する。

## 実務上の推奨

1. 通常のFc糖鎖のみの抗体は、まずRapid P0710の50℃・10分だけを試す。
2. Fab糖鎖残存が確認された抗体だけ、前処理温度系列を行う。
3. 完全脱糖鎖できる最低の前処理温度を採用する。
4. 非還元intact massではP0711を候補にするが、Native構造保持とはみなさない。
5. Native性を優先し、Fc糖鎖だけでよければEndoS2を使用する。ただしFab糖鎖は残り、GlcNAc±Fucも残る。
6. 還元intact MSでは、立体構造より回収率、fragment、共有結合性凝集、化学修飾を重視する。

---

# 参考資料

## NEB

- [PNGase F (Glycerol-free), Recombinant P0709](https://www.neb.com/en/products/p0709-pngase-f-glycerol-free-recombinant)
- [PNGase F protocol](https://www.neb.com/en-us/protocols/pngase-f-protocol)
- [Rapid PNGase F P0710](https://www.neb.com/en-us/products/p0710-rapid-pngase-f)
- [Rapid PNGase F P0710 protocol](https://www.neb.com/en/protocols/rapid-phgase-f-protocols-f-p0710)
- [Rapid PNGase F Non-Reducing P0711](https://www.neb.com/en-gb/products/p0711-rapid-pngase-f-non-reducing-format)
- [Rapid PNGase F P0711 protocol](https://www.neb.com/en-us/protocols/rapid-pngase-f-non-reducing-format-p0711-reaction-protocol)
- [Endo H](https://www.neb.com/en-ca/products/p0702-endo-h)
- [PNGase A](https://www.neb.com/en-us/products/p0707-pngase-a)
- [O-Glycosidase P0733](https://www.neb.com/en-us/products/p0733-o-glycosidase)
- [O-Glycoprotease IMPa](https://www.neb.com/en-ca/products/p0761-o-glycoprotease)
- [Endoglycosidase selection chart](https://www.neb.com/en-us/tools-and-resources/selection-charts/endoglycosidase-selection-chart)

## Genovis

- [OglyZOR](https://www.genovis.com/product/oglyzor-lyophilized-2000-units/)
- [SialEXO](https://www.genovis.com/product/sialexo-lyophilized/)
- [OpeRATOR](https://www.genovis.com/smartenzymes/glycan-profiling/operator/)
- [GlycINATOR / EndoS2](https://www.genovis.com/products/glycinator/)

## 特許・文献

- [NEB Deglycosylation Reagents and Methods, US20150346194A1](https://patents.google.com/patent/US20150346194A1/en)
- [Rapid deglycosylation of glycoproteins, US8198063B1](https://patents.google.com/patent/US8198063B1/en)
- [Heat denaturation of the antibody, a multi-domain protein](https://pmc.ncbi.nlm.nih.gov/articles/PMC5899721/)
- [Site-Specific Structural Changes in Long-Term-Stressed Monoclonal Antibody](https://pmc.ncbi.nlm.nih.gov/articles/PMC10609731/)
- [Evaluation of different PNGase F enzymes in IgG and plasma N-glycan analysis](https://academic.oup.com/glycob/article-abstract/31/1/2/5848263)
