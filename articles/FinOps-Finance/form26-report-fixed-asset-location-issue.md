---
title: 保管場所を移動しても償却資産税申告書に反映されない事象について
date: 2023-03-20
tags:
  - FinOps-Finance
  - D365FO Fixed Assets issue

disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの尾崎です。  
この記事では固定資産の保管場所を移動した際に、償却資産税申告書に移動結果が反映されない事象についてご案内します。

<!-- more -->

## 更新履歴
2023 年 3 月 20 日 (月) : ブログ公開
2023 年 5 月 10 日 (水) : タイムライン更新

## 検証に用いた製品・バージョン
Dynamics 365 Finance and Operations  
Application version: 10.0.32  
Platform version: PU56  


## 事象の再現手順
弊社標準環境 JPMF を使用した事象の再現手順は以下のようになっております。
1. 固定資産パラメーターにて場所移動を許可します。

![](./form26-report-fixed-asset-location-issue/form26-report-fixed-asset-location-issue1.png)

2. 減価償却プロファイルにて電算処理方式の期間の頻度を年 1 回に変更します。

![](./form26-report-fixed-asset-location-issue/form26-report-fixed-asset-location-issue2.png)

3. 固定資産の作成を行います。帳簿には Form26 を含むようにします。
4. 作成した固定資産を取得し、減価償却を行います。
5. 固定資産の場所を移動します。転送先の場所を押下後、移動場所と転送日を入力し更新します。

![](./form26-report-fixed-asset-location-issue/form26-report-fixed-asset-location-issue3.png)

6. 固定資産の場所移動を確定後、申告 26 レポートを起動します。
　固定資産 > 照会およびレポート > 減価償却資産申告レポート > 申告 26: 償却資産税の元帳レポート

7. レポートを出力すると場所移動前の市区町村にて出力される事象が確認できます。
　また本事象は以下 2 つのレポートでも発生することを確認しております。
　申告 26 - 1: 全資産および増加資産のタイプごとの詳細レポート
　申告 26 - 2: 減少資産のタイプごとの詳細レポート
![](./form26-report-fixed-asset-location-issue/form26-report-fixed-asset-location-issue4.png)


## 修正方針
場所の移動結果が正しくレポートに反映されるよう修正を行う方針でございます。

## 今後のタイムライン
バージョン 10.0.38 にて修正プログラムがリリースされる予定でございます。
※リリース予定のバージョンは変更される場合がございます。予めご了承ください。

## おわりに  
以上、固定資産の保管場所を移動した際に、償却資産税申告書に移動結果が反映されない事象についてご案内いたしました。
