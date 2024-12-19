---
title: D365BCの画面上でテーブルデータを確認する方法
date: 2022-09-07
tags:
  - BusCen-Platform
  - tips

disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの永吉です。  
この記事では、 Dynamics 365 Business Central (D365BC) の画面上でデータベースのテーブルデータを確認する方法を紹介します。

<!-- more -->
## 検証に用いた製品・バージョン
Dynamics 365 Business Central  
Version: W1 20.4  

## 手順
1. D365BC にブラウザでアクセスする
    ![](./how-to-check-table-data-d365bc/step1.png)

2. URL を以下のとおり変更する  
    ``` https://<environmentURL>/?company=<ComapanyName>&table=<tableID> ```  
    以下例  
    ![](./how-to-check-table-data-d365bc/step2.png)

3. 画面上にリスト形式でテーブルデータが表示される
    ![](./how-to-check-table-data-d365bc/step3.png)

## テーブル番号の調べ方
1. 参照したいテーブルデータが表示されるページに遷移する  
   以下例
    ![](./how-to-check-table-data-d365bc/step4.png)

2. Ctrl + Alt + F1 をクリックして、Page Inspection を開く
    ![](./how-to-check-table-data-d365bc/step5.png)

3. Page Inspection の Table で括弧書きにされている番号がテーブル番号となる  
    ![](./how-to-check-table-data-d365bc/step6.png)

---
## おわりに  

以上、Dynamics 365 Business Central の画面上で、データベースのテーブルデータを確認する方法を紹介いたしました。  
