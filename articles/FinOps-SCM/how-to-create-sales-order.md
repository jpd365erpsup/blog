---
title: 販売注文作成の一連の流れ
date: 2022-09-22
tags:
  - FinOps-SCM
  - Sales order
disableDisclaimer: false
---


こんにちは、Dynamics ERP サポートチームの道浦です。  
この記事では、 Dynamics 365 Finance and Operations にて、 販売注文作成の一連の流れについて紹介します。


<!-- more -->
## 検証に用いた製品・バージョン
Dynamics 365 Finance and Operations      
Application version : 10.0.33    
Platform version : PU 57  
Legal entity : USMF  

## 販売注文作成前の一連の流れ
1. [売掛金管理] > [注文] > [すべての販売注文] の順にクリックする  
    ![](./how-to-create-sales-order/step1.png)

1. [新規] をクリックし、[顧客 ID] を入力する
    設定が完了した後、[OK] ボタンをクリックする  
    ※ 顧客 ID を入力すると、"名前" 以降は自動で入力されます
    ![](./how-to-create-sales-order/step2.png)

1. "購買注文明細行" に必要な項目を入力する  
    ※ [品目番号] を入力すると、製品マスタに登録している内容は自動入力されます。
    ![](./how-to-create-sales-order/step3.png)

1. [保存] ボタンをクリックする  
    販売注文のステータスが "オープン注文" と表示されれば販売注文が作成されたことになります。  

## 販売注文作成後の一連の流れ
1. [販売] > [生成] > [販売注文の確認] の順にクリックし、販売注文の入力内容を確認し、[OK] をクリックする
    ![](./how-to-create-sales-order/step5.png) 
    
    ![](./how-to-create-sales-order/step5-1.png) 

    ※ピッキング リストを作成する必要がない場合は、以下 3 つの手順はスキップします
1. [ピッキングと梱包] > [生成] > [ピッキング リストの生成] の順にクリックする  
    ![](./how-to-create-sales-order/step6.png) 

1. 入力内容を確認し、[OK] をクリックする
    ![](./how-to-create-sales-order/step7.png) 

1. [ピッキングと梱包] > [生成] > [ピッキング リスト登録] の順にクリックする
    ![](./hou-to-create-sales-order/step7-2.png)

1. [更新] > [すべて更新] の順にクリックする
    ![](./hou-to-create-sales-order/step7-3.png)

1. [明細行] に表示されている全ての明細行の [処理ステータス] が "完了" になっていることを確認し、販売注文に戻る
    ![](./hou-to-create-sales-order/step7-4.png)

1. [ピッキングと梱包] > [生成] > [梱包明細の転記] の順にクリックする
    ![](./how-to-create-sales-order/step8.png) 

1. "パラメーター" の "数量" の箇所について、 ピッキング リスト作成の手順を実施した場合は [ピッキング済] とし、手順をスキップした場合は [すべて] に変更し、[OK] をクリックする  

    <ピッキング リスト作成した場合>  
    ![](./how-to-create-sales-order/step9-1.png)  
    <ピッキング リストの作成をスキップした場合>  
    ![](./how-to-create-sales-order/step9-2.png)  

1. [請求書] > [生成] > [請求書] の順にクリックする
    ![](./how-to-create-sales-order/step10.png)

1. 請求の転記内容を確認して、[OK] をクリックする
    ![](./how-to-create-sales-order/step11.png)

## 販売注文の一連の流れが完了した後
販売注文のステータスが "請求済" と表示されます  
![](./how-to-create-sales-order/step12.png)   

---
## おわりに  

以上、 Dynamics 365 Finance and Operations にて、販売注文作成の一連の流れについてご紹介しました。
