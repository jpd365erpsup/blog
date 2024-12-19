---
title: 購買要求から作成された発注書が自動的に "ドラフト" になる場合
date: 2023-1-30
tags:
  - FinOps-SCM
  - Draft

disableDisclaimer: false
---

こんにちは、日本マイクロソフト Dynamics ERP サポートチームの木村です。  
この記事では、 Dynamics 365 Finance and Operations における [購買要求] 画面から作成された発注書のステータスを "ドラフト" にする手順を紹介します。

<!-- more -->
## 目次

1. [検証に用いた製品・バージョン](#anchor-version)
2. [[購買要求] 画面から作成された発注書のステータスを "ドラフト" にする手順について](#how-to-update-postatus)
3. [おわりに](#anchor-finish)

<a id='anchor-version'></a>

## 検証に用いた製品・バージョン
Dynamics 365 Finance and Operations      
Application version: 10.0.31   
Platform version: PU55  

<a id='how-to-update-postatus'></a>
## [購買要求] 画面から作成された発注書のステータスを **"ドラフト"** にする手順
### 手順
1. [調達] > [設定] > [調達パラメーター] を順にクリックする
2. "購買要求経由で作成された発注書経由のドラフト承認状態を指定する" を 「はい」に設定する
![](./how-to-change-purchase-order-status/step1.png)

3. 購買要求を作成し、承認まで実施する  
※本ブログでは購買要求の手順については割愛いたします。
![](./how-to-change-purchase-order-status/step2.png)

### **作成された発注書**  
ステータスが **"ドラフト"** になっていることを確認する
![](./how-to-change-purchase-order-status/step4.png)

 ※上記設定を行っていない場合は、[購買要求] 画面から作成された発注書のステータスは "承認済" となります  
 ※前提として [調達パラメーター] 画面の "変更管理の有効化" が「はい」になっていること (= [発注書] 画面にてワークフローの処理を有効にすること)　　
![](./how-to-change-purchase-order-status/step3.png)

<a id='anchor-finish'></a>
---
## おわりに  

以上、 Dynamics 365 Finance and Operations における [購買要求] 画面から作成された発注書のステータスを "ドラフト" にする手順について紹介いたしました。
