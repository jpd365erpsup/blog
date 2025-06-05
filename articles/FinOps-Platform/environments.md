---
title: Dynamics 365 Finance and Operations の環境ごとの違い
date: 2024-07-01
tags:
  - FinOps-Platform
  - Tips
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの福原です。
この記事では、 Dynamics 365 Finance and Operations (D365FO) の環境ごとの違いについてご案内します。
クラウドホスト環境、サンドボックス環境、Tier2環境、本番環境等、様々な呼び方の環境があり、また、それぞれの環境で使える機能も異なるので、分かりづらいというお声をいただくことがありますので、そのような場合には本記事をご参考ください。

<!-- more -->


## 更新履歴
2023 年 9 月 8 日 : ブログ公開しました。
2024 年 7 月 1 日 : UDE (Unified developer environment) の GA に合わせ UDE を追加しました。 UDE の詳細は https://devblogs.microsoft.com/powerplatform/the-unified-development-environment-is-ga/ をご確認ください。





<br>
<br>
<br>
<br>


| 環境名                         | 本番環境                 | サンドボックス環境                       | クラウドホスト環境                               | UDE | 
| :----------------------------- | :----------------------- | :--------------------------------------- | :----------------------------------------------- | :----------- | 
| 配置可能なLCSプロジェクト                 | 実装プロジェクト         | 実装プロジェクト                         | 実装プロジェクト<br>  or パートナー試用版プロジェクト | LCS プロジェクト上には作成されないので該当なし        | 
| 呼ばれ方例                   | Production 環境 <br> 運用環境 <br> Microsoft-managed 環境 <br> セルフサービス環境  | Sandbox環境 <br> Tier2 ~ Tier5 環境 <br> 非運用環境  <br> Microsoft-managed 環境 <br> セルフサービス環境  | Cloud-hosted環境、<br> 開発環境            | Unified developer environment         | 
| 配置場所                       | Azure                    | Azure                                    | Azure                                            | Azure         | 
| Azure Subscription (*1)             | Microsoft                | Microsoft                                | 顧客                                             | Microsoft       | 
| データベース                   | Azure SQL                | Azure SQL                                | Azure VM 内のオンプレミスSQL Server              | Azure SQL         | 
| SSMSによる<br> データベースへの接続 | 不可                     | 可 (*2)                                       | 可                                               | 可 (*3)         | 
| RDP接続                        | 不可                     | 不可                                     | 可                                               | 不可         | 
| フライト有効化方法 (*4)            | Microsoft                | Microsoft                                | 顧客                                             | Microsoft       |



(*1): 本番環境、サンドボックス環境は、Microsoft 内の Azure Subscription に紐づいて管理されているので、顧客は Azure portal にて環境の情報を見ることができません。クラウドホスト環境は顧客の Azure Subscirption 内で構築されますので、Azure portal にて環境や請求の情報を見ることができます。

> [!NOTE]
> クラウドホスト環境は弊社からアクセスおよびログの取得ができないため、弊社によるトラブルシューティングが制限されております。
> クラウドホスト環境内の事象が解消しない場合には、クラウドホスト環境の再作成をお願いしていますので、再作成可能という前提でクラウドホスト環境の運用をお願い致します。
> 以下の弊社公開資料の注意事項もご参考にしていただきますようお願い致します。
> 
> [開発環境の配置とアクセス](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/dev-tools/access-instances)
>---抜粋---
>注意
> ・Microsoft サポートでは、レベル 1 の開発環境でのトラブルシューティングが制限される場合があります。
> ・特定の状況では、問題を解決するために、Microsoft サポートからレベル 1 環境の新規展開が要求される場合があります。
> ・開発環境にはビジネス クリティカルなデータを含めるべきではなく、破棄可能と見なされます。
> ・120 の環境だけがテナントごとのサポートです。 特定のテナント下のクラウド ホスト環境数を制限して、サンドボックスおよび運用環境を配置できる十分なキャパシティを許可することをお勧めします。

(*2): https://jpdynamicserp.github.io/blog/FinOps-Platform/database-just-in-time-jit-access/ の手順となります。
(*3): https://learn.microsoft.com/ja-jp/power-platform/developer/unified-experience/finance-operations-product-db-access の手順となります。
(*4): 本番環境、サンドボックス環境、クラウドホスト環境のフライトの管理方法の違いは https://jpdynamicserp.github.io/blog/FinOps-Platform/what-is-flight/ にてご案内しております。


(*): 本記事は2024 年 7 月 1 日時点での情報です。


---
## おわりに  

以上、 Dynamics 365 Finance and Operations (D365FO) の環境ごとの違いについてご紹介しました。
