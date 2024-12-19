---
title: D365FO のブラウザーセッション ID の取得方法
date: 2022-11-16
tags:
  - FinOps-Platform
  - 情報採取
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームです。  
この記事では、 Dynamics 365 Finance and Operations のブラウザーセッション ID の取得方法をご紹介します。
D365FO の UI 上にてエラー等が発生した際に、ブラウザーセッション ID を取得し、弊社に提供して頂けますと、その ID を基にしてサーバーに残っておりますログを弊社にて調査できる場合がございますので、トラブルシューティングをより効果的に行うことができます。もし、お問い合わせの中で弊社サポートエンジニアより、ブラウザーセッション ID の取得を依頼されましたら、こちらの手順により取得して頂けますと幸いです。

<!-- more -->
> [!NOTE]
> 注意点としまして、Web ブラウザーのページを更新しますと、ブラウザーセッション ID は変わってしまいますので、事象の再現時および、ブラウザーセッション ID の取得時には Web ブラウザーのページを更新しないようにお願いします。
> Trace Parser によりトレースを取得 ([Trace Parserを使用したトレースの実行方法](https://jpdynamicserp.github.io/blog/FinOps-Platform/how-to-get-trace-parser/))  する際にも、トレースの取得前または取得後にて、ブラウザーを更新せずに、ブラウザーセッション ID の取得をお願いします。


## 検証に用いた製品・バージョン
Dynamics 365 Finance and Operations      
Application version: 10.0.31
Platform version: PU55


## Dynamics 365 Finance and Operations のブラウザーセッション ID の取得方法

1. D365FO の右上の ? ボタン > フィードバック をクリックします。

    <img src="./image1.png" style="border: 1px black solid;">

2. フィードバック画面が開きますので、下部のセッション情報をコピーし、弊社にご提供して頂けますと幸いです。

    <img src="./image2.png" style="border: 1px black solid;">


---
## おわりに  
以上、 Dynamics 365 Finance and Operations のブラウザーセッション ID の取得方法についてご紹介しました。
