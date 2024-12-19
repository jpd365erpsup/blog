---
title: 月次締め請求書の作成手順
date: 2022-07-01
tags:
  - FinOps-Finance
  - Invoice
  - Japan localization
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの尾崎です。  
この記事では、Dynamics 365 Finance and Operations (D365FO) の日本向けローカライゼーション機能である月次締め請求書作成手順を紹介します。  
<!-- more -->
## 検証に用いた製品・バージョン
Dynamics 365 Finance and Operations      
Application version : 10.0.33
Platform version : PU 57
Legal entity : JPMF  
  
# 支払期日の設定
請求書に記載する毎月の支払予定日の情報を入力します。手順は以下のようになります。
1. [売掛金管理] > [支払の設定] > [支払期日] を開く
1. [新規] ボタンを押下し、"支払期日" の名称を入力
1. 支払期日明細行では [週/月] に "月" を入力、[月の日付] には毎月の期日を入力 (毎月の支払日に末日を設定する場合には 31 を入力)  
![](./create-consolidated-invoice/CreateConsolidatedInvoice1.png)


# 支払条件の設定
月次締め請求書における締日などの支払い条件を登録します。手順は以下のようになります。
1. [売掛金管理] > [支払の設定] > [支払条件] を開く
1. [新規] ボタンを押下し、[支払条件] の名称を入力、[支払方法] には "締日" を選択
1. 月数には当月、翌月、翌々月などの情報を数字で入力 (20 日締翌月末払いの場合、締日に "20"、月数に "1" を入力)  
![](./create-consolidated-invoice/CreateConsolidatedInvoice2.png)


# 月次締めグループの登録
月次締め請求書出力時に使用する顧客の月次締め日を登録します。手順は以下のようになります。
1. [売掛金管理] > [顧客] > [すべての顧客] を開く
1. 対象の顧客を選択し、[支払の既定値] > [月次締めグループ] > [月次締め日] に顧客の月次締め日を入力
1. [支払の既定値] > [支払] > [支払い条件] に作成したものを入力
![](./create-consolidated-invoice/CreateConsolidatedInvoice3.png)


# 販売注文の作成および請求
販売注文は通常の手順で作成したものを使用できます。月次締め日を登録した顧客について販売注文を作成し、請求書の転記まで行います。  
参考ブログ : [販売注文作成の一連の流れ](https://jpdynamicserp.github.io/blog/FinOps-SCM/how-to-create-sales-order/)  


# 月次締め請求書の出力  
月次締め請求書の出力は以下の手順になります。
1. [売掛金管理] > [定期処理のタスク] > [月次締め請求書] を開く
1. [新規] ボタンを押下し、パラメーターとレコードを選択して実行
   1. [パラメーター] > [実行日] はセッション日付
   1. 月次締め日を手動で設定したい場合、 [以下で指定する月次締め日の使用] を [Yes] に変更
   1. [対象に含めるレコード] > [フィルター] を押下し、条件を指定する
1. データの取得に成功すると一覧に表示されるので、データを選択した状態で [月次締め請求書] > [印刷] > [月次締め請求書] ボタンより印刷
1. 出力結果について確定する場合は[確認] ボタンを押下（確認済のものを変更する場合は [再オープン] を押下する）
![](./create-consolidated-invoice/CreateConsolidatedInvoice4.png)


参考資料    
[顧客月次締め請求書の作成および確認 - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/finance/localizations/tasks/create-confirm-customer-consolidated-invoice)  
[日本向け月次締め請求書 - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/finance/localizations/apac-jpn-consolidate-invoices)  

---  
# おわりに  
以上、月次締め請求書の事前設定と出力の手順についてご紹介しました。
