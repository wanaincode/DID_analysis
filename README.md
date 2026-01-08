# 小売業におけるマークダウン施策の因果効果分析
## Difference-in-Differences（DiD）によるアプローチ

## 概要
本プロジェクトは、小売業におけるマークダウン（販促割引）施策が、
週次売上に与える因果効果を Difference-in-Differences（DiD）手法を用いて評価する
因果推論プロジェクトである。

実務においては、施策導入後の売上変化を単純に比較するだけでは、
季節性や景気変動、店舗特性などの影響を分離することが難しい。
本分析では、公開されている実データを用いて擬似的な実験構造を構築し、
施策の純粋な効果を定量的に推定することを目的とする。

---

## 分析目的・問い（Research Questions）

- マークダウン施策は週次売上を**因果的に**押し上げているか  
- その効果の大きさはどの程度か  
- 祝日週（Holiday）において、施策効果は増幅するか  

---

## データセット

本プロジェクトでは、Kaggle にて公開されている実世界データを使用している。

**Walmart Recruiting – Store Sales Forecasting**

本データセットは、小売店舗における週次売上データを  
Store × Department 単位で提供しており、売上高に加えて以下の外生変数を含んでいる。

- 気温（Temperature）
- 燃料価格（Fuel Price）
- 消費者物価指数（CPI）
- 失業率（Unemployment）
- 祝日フラグ（IsHoliday）
- マークダウン施策（MarkDown1–5）

- 分析単位：Store × Department × 週  
- 被説明変数：Weekly_Sales（週次売上）  
- 介入変数：マークダウン施策（MarkDown1–5）  
- 時系列構造：週次データ  

元データ自体は改変せず、`data/` ディレクトリにローカル保存し、
バージョン管理の対象外としている。  
因果効果を推定するため、前処理段階において施策有無を示す処置変数（treatment）や、
介入後期間を表すフラグ（post）などの分析用変数を新たに構築している。

データ出典：  
https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting

---

## 分析手法

- Difference-in-Differences（DiD）
- Store × Department 固定効果
- 時間固定効果（週次）
- 外生変数（経済指標・祝日要因）を含む回帰分析
- 並行トレンド仮定の検証およびロバストネスチェック

---

## 分析結果

※ 現在は分析途中であり、推定結果および図表は今後追加予定。

---

## 考察・示唆

※ 分析結果に基づき、マークダウン施策の有効性や実務上の示唆について考察を追加予定。

---

## フォルダ構成

```
DID_analysis/
├── README.md
├── data/               # 元データ（Git 管理対象外）
├── notebooks/          # 分析用ノートブック
├── src/                # 再利用可能な分析コード
└── results/            # 図表・推定結果
```
---

## English Version
## Overview
This repository contains a causal inference project that evaluates the causal impact of markdown (promotion) policies on weekly sales using the Difference-in-Differences (DiD) methodology.

The project is motivated by real-world business settings where randomized A/B testing is often infeasible.  
By constructing a quasi-experimental design from publicly available data, the analysis aims to isolate the causal effect of promotion interventions from seasonal trends, macroeconomic factors, and store-specific characteristics.

---

## Research Questions

- Do markdown promotions causally increase weekly sales?
- How large is the estimated treatment effect?
- Are promotion effects amplified during holiday weeks?

---

## Dataset

This project uses publicly available real-world data from Kaggle.

**Walmart Recruiting – Store Sales Forecasting**  
The dataset provides weekly sales data at the Store × Department level, along with external variables such as temperature, fuel price, CPI, unemployment rate, holiday indicators, and markdown (promotion) variables.

- Unit of analysis: Store × Department × Week  
- Outcome variable: Weekly_Sales  
- Treatment variable: Markdown promotions (MarkDown1–5)  
- Time dimension: Weekly time series  

The original raw datasets are stored locally under the `data/` directory and are excluded from version control.  
For causal inference purposes, additional variables such as treatment indicators and post-intervention flags are constructed during the data preprocessing stage.

Data source:  
https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting

---

## Methodology

- Difference-in-Differences (DiD)
- Store × Department fixed effects
- Weekly time fixed effects
- Regression with external control variables
- Validation of the parallel trends assumption
- Robustness checks under alternative specifications

---

## Results

Results and figures will be added as the analysis progresses.

---

## Implications

Based on the estimation results, business implications and decision-oriented insights regarding the effectiveness of markdown promotions will be discussed.