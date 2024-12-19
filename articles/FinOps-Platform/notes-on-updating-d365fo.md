---
title: D365FOのアップデートに関する注意事項
date: 2023-11-10
tags:
  - FinOps-Platform
  - Information
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームです。  
この記事では、Dynamics 365 Finance and Operations (D365FO) のアップデートに関する注意事項を紹介します。  
<!-- more -->

## 更新履歴
2023 年 11 月 10 日 (金) : バージョンアップデートの頻度の変更について更新しました。

# 2024 年 4 月からの変更点
バージョンアップデートの頻度が、年 7 回から年 4 回に変更されます。連続で最大 1 つまでの更新を一時停止することができ、年に少なくとも 2 回バージョンアップデートを実施して頂く必要があります。

詳細は以下のドキュメントをご確認お願い致します。

[What's changing with the new release cadence?](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/one-version#whats-changing-with-the-new-release-cadence)

# 「サービスアップデート自動適用の一時停止」の注意点
D365FO のサービスアップデートにつきまして、以下のドキュメントに記載されていますように、2024 年 4 月より連続で最大 1 つまでの更新を続けて一時停止することができます。  

[更新を遅らせることができますか、ポリシーとは何ですか。](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/one-version#can-the-updates-be-delayed-whats-the-policy)

連続で 2 回以上の一時停止は、**いかなる理由でも実施できません**のでご注意ください。  
本番環境は、サービス終了する前にアップデートして頂くことで、常にサポートされている環境を維持頂きますようお願い致します。

# 「サービス終了」の期日

各サービスアップデートの「サービス終了」期日は以下のドキュメントでご確認頂けます。  
[サービス更新の可用性](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases)

# サービス終了前にアップデートを適用するメリット

サービス終了前にアップデート頂くことで、常にサポートされている環境を維持でき、以下のようなメリットもございます。  
1. 問題発生時に調査及びトラブルシューティングを依頼可能です。  
2. Critical な問題が発見された場合、新しいサービスアップデートを適用することなく、Quality Update から修正を入手可能です。  
  
# 「サービス終了」した環境の制約
        
「サービス終了」した環境では多くの制約が発生しますのでご注意ください。  
1. Microsoft は、サービスの終了に達しているバージョンに対して、修正プログラムをリリースしません。  
2. 3 つのサービス更新より古いバージョンで発生した問題の調査とトラブルシューティングを行いません。  
3. 以下の LCS 機能が使用不可となる可能性がございます。  
    * メンテナンス モードの有効化  
    * 環境または環境間でデータベースを移動するために提供されるすべての機能を使用する  
    * SQL Server データベースへのファイアウォール アクセスの有効化  
    * RSAT 証明書のダウンロード  
    * RSAT 証明書を再生成する  
  
(参考URL)  
[サービスの終了にはどのような意味がありますか?](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/get-started/one-version#what-does-end-of-service-mean)  


# おわりに  
以上、 Dynamics 365 Finance and Operations (D365FO) のアップデートに関する注意事項を紹介いたしました。