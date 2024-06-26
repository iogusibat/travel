---
title: 実際原価計算と標準原価計算の差異分析 | インドネシアITなび
updated: 2017-04-30 07:39:12Z
created: 2017-04-30 07:39:12Z
source: https://www.indonesia-japan.com/standard-cost/
tags:
  - SI
---

# 実際原価計算と標準原価計算の差異分析

### 前期末に立てた計画を元に実績を比較する

工場では年度末に製造費用予算（材料費・労務費・製造間接費）、生産予定数、能率などの来期の計画を作成し、実際発生額、生産実績数、実績能率との比較を行います。
1. 生産予定数量
2. 能率（稼動予定時間÷生産予定数量）
3. 予算（直接材料費・直接労務費・製造間接費）

### 標準原価では直接労務費や製造間接費も変動費のように計算する

製造原価は大きく分けて直接材料費（モノ）、直接労務費（人）、製造間接費（機械）にカテゴリ分けされ、変動費の大半は直接材料費や外注加工費で占められますが、機械の光熱費や特定品の発送費用、仕入諸掛など製造間接費の一部として製造変動費（直接経費）が含まれます。

![cost](../_resources/fc6a64752a7146d2b8a33fc6cb29dc34.png)

そして変動費である直接材料費だけでなく、固定費である直接労務費や製造間接費も、標準原価を計算するために変動費のような式で表現されます。
1. 直接材料費＝単価ｘ数量
2. 直接労務費＝賃率ｘ時間
賃率は1分あたりの費用
3. 製造間接費＝配賦率ｘ稼動時間
配賦率は1時間あたりの費用

### 直接材料費（モノ）

生産管理システムは品目マスタ、BOM（部品構成表）、単価マスタなどのマスタ情報をベースとして機能しますが、日常の現場では必ずしもマスタの定義どおりには動いていません。

BOMに基づく材料の必要量より現場での材料の投入実績が多くなったり、スクラップが発生し計画どおりの生産実績が上がらなかったり、P/O（Purchase Order 発注書）発行時の購入価格がネゴのおかげで購買単価マスタベースの価格より安く済んだり、マスタ情報と現場の実績には差異が出ます。

![difference1](../_resources/ce6ce941fdebeb7f6a2229d8be5a2e7f.png)
この例は**数量差異**（Qty difference）と**価格差異**（Price difference）という直接材料費に関係する差異です。

- 価格差異＝（実際購入単価－標準購入単価）ｘ実際数量
- 数量差異＝（実際数量－標準数量）ｘ標準購入単価

実務上の帳票フォーマットはこんな感じになります。
![価格差異](../_resources/rm_differ.gif)

### 直接労務費（人）

直接労務費の場合は、作業日報で作業手順ごとの実績作業時間（activity）を収集し
実際直接労務費÷実績作業時間

で求められる実際賃率に対する標準賃率（配賦率）の差に起因する差異が**賃率差異**（Allocation rate difference）で、作業時間の差に起因する差異が**作業時間差異**（Activity difference）です。![difference2](../_resources/ca4c2255f788eaa7fc63e52da20eafa5.png)

- 賃率差異＝（実際賃率－標準賃率）ｘ実際作業時間

実際賃率＝実際直接労務費÷実績作業時間

- 作業時間差異＝（実際作業時間－標準作業時間）ｘ標準賃率

実務上の帳票フォーマットはこんな感じになります。
![労務費差異](../_resources/lc_differ2.gif)

実績作業時間（直接工数）は直接部門単位（コストセンター）単位に集計できますが、品目別の**直接工数**（1個あたり何分）を算出するためには、事前にマスタに設定した**標準工数**（Standard activity）と製造数量により按分します。

品目別直接工数合計＝部門別直接工数合計ｘ｛（標準工数ｘ製造実績数量）／SUM（標準工数ｘ製造実績数量）｝

[1個あたりの直接労務費を「工数ｘ賃率」で算出するという発想](https://www.indonesia-japan.com/wage-rate/)は、発注側が受注側に対して外注加工費の目安として提示するために使用されますが、製品あたりの労務費を算出する際にも使用されます。

### 製造間接費（機械）

製造原価の変動費の大半は直接材料費や外注加工費で占められますが、厳密に言うと機械を動かすための光熱費は変動費に分類すべきであり、製造間接費は製造変動費と製造固定費に分けられます。

![cost](../_resources/e8ca64e765830b4c882ab9669233e1b6.png)

基準操業時間（フル操業時間）と実績操業時間の差が操業度差異時間であり、標準固定費単価を掛けて金額換算したものが**操業度差異**になり、機械負荷（Load）が能力（Capacity）に満たない場合の損失を表します。

![操業度差異](../_resources/sougyoudo.gif)

一方、**能率差異**は機械の実際能力が標準能力に満たない場合の損失を表します。実績生産数量を標準能力（ph）で割った標準能力時間と、実績能力（ph）で割った実績能力時間との差が能率差異時間であり、標準固定費単価を掛けて金額換算したものが操業度差異金額になります。

![能率差異](../_resources/nouritsu.gif)

**予算差異**は材料費単価や賃率が上がったことにより、実績製造間接費（配賦率ｘ実際稼働時間）をオーバーした差異です。

## 実績原価計算と標準原価計算の差異

実績原価計算では直接材料費合計は「標準材料単価ｘ実績投入数量」、製造間接費合計は「標準単価（時間）ｘ実績作業時間」で計算され、この結果として製品と中間品の単価をリアルタイムで計算（速報原価）できるため、会計システム連動型ERPパッケージでは継続記録法で仕訳を起こし、在庫評価額を常に把握できるようになっています。

標準原価での材料費は「標準使用量＝子必要量（BOM）ｘ生産数量」としたとき
標準購入単価（購買単価マスタ）ｘ標準使用量
ですが、実績原価では
標準購入単価（購買単価マスタ）ｘ実際使用量
になります。例えば1製品あたり4個のボルトを使う製品を100個生産する場合、標準原価では
標準購入単価ｘ4個ｘ100個
ですが、実績原価の場合は
標準購入単価ｘ（4個ｘ100個＋NG分）
になります。つまり実績原価と標準原価の間には価格差異は発生しませんが、数量差異が標準購入単価ｘ差異分発生することになります。
また標準原価での労務費は
標準賃率ｘ標準作業時間
ですが、実績原価では
標準賃率ｘ実際作業時間（標準作業時間＋ロス時間）
になります。つまり同じように賃率差異は発生しませんが、作業時間差異が発生することになります。

## 予定配賦費用と実際配賦費用の差異

本来の実際原価計算では、月末に算出される総平均単価から直接材料費を算出し、直接労務費や間接費はG/L（General Ledger 一般会計）から集計した当月発生費用を、作業時間や出来高で配賦しますが、企業会計の現場における機動的なスピード会計が難しいという判断から、原価計算基準の実際原価計算の定義で[予定配賦](http://okwave.jp/qa/q2207338.html)が認められています。

受払の都度仕訳を発生させる継続記録法を前提としたパッケージシステムにおいて、材料費は移動平均法で入荷の都度アップデートされ、労務費と製造間接費はBOMまたは品目工程マスタ（作業項目マスタ）に[予定配賦率](http://okwave.jp/qa/q2207338.html)を設定し、実績消費量を元に予定配賦額を算出し、月末に実際発生額との差異の調整仕訳を起こします。

実際発生額と予定配賦額の差異は差異勘定に計上され、月末に売上原価（COGS）と月末製品在庫に按分されます。

### 投入実績

材料費と材料の払いは「移動平均単価ｘ実績消費量」で都度仕訳され、材料費を積上げるためオフセットで仕掛品に振替えます。
Dr. 材料費 80　　　　Cr. 材料 80
Dr. 仕掛品　80　　　Cr. 材料費Offset（マイナス費用） 80

### 生産実績時の予定配賦

労務費と製造間接費はオフセットに「予定配賦率ｘ実績出来高」で予定配賦額を都度仕訳されます。
Dr. 仕掛品 50　　　　Cr. 労務費Offset（予定配賦額　マイナス費用） 50
Dr. 仕掛品 30　　　　Cr. 製造間接費Offset（予定配賦額　マイナス費用） 30
製品完成時に仕掛品は製品製造原価（COGM）から製品に振替えられ、月末に仕掛品残の理論値が確定します。
Dr. COGM　60　　　　Cr. 仕掛品　60
Dr. 製品 60　　　　Cr. COGM-Offset 60

### 月末の差異仕訳

この時点で労務費と製造間接費は予定額として資産である製品に含まれています。
製造原価報告書上では予定配賦額を使って、労務費50と製造間接費30と記載して、COGMを暫定的に確定してしまいます（仕訳なし）。
そして実際発生額が集計できた時点で、
Dr. 労務費Payable 53　　　　AP 53
Dr. 製造間接費Payable 32　　　　AP 32
実際発生額と予定配賦額との差異をP/L上で原価差異勘定に計上しますが、この差異は本来はCOGMに含まれるべきものです。
Dr. 賃率差異（不利差異） 3　　　　Cr.労務費Offset 3
Dr. 製造間接費配賦差異（不利差異） 2　　　　Cr. 製造間接費Offset 2

### 月末のCOGSと製品在庫への振替仕訳

賃率差異、製造間接費配賦差異などCOGMに含みきれなかった原価差異は、最終的にP/L上では一括して原価差異として売上原価または製品に振替えます。
この場合、売れた製品（売上原価）と残った製品（月末在庫）に数量按分します。
Dr. COGS 2　　　　Cr.賃率差異（原価差異） 3
Dr. 製品 1Dr. COGS 1　　　　Cr. 製造間接費配賦差異（原価差異）2
Dr. 製品 1

![contra](../_resources/f9a6b67d0df49c5e7c83a8d0d3c32d64.jpg)