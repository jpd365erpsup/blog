---
title: Dynamics 365 Finance and Operations をご利用いただく際の留意事項、ご協力いただきたい事項
date: 2023-2-10
tags:
  - FinOps-Platform
  - Tips
disableDisclaimer: false
---


こんにちは、Dynamics 365 ERP サポートチームです。
今回は、Dynamics 365 Finance and Operations をご利用いただく際の留意事項、ご協力いただきたい事項についてご紹介します。

<!-- more -->
---
Dynamics 365 Finance and Operations では、稼働中一時的に接続が失われることがございます。
これらは障害の発生を未然に防ぐためのものとなり、自動で復旧する際に発生いたします。クラウド製品の特性上、データセンターやネットワーク インフラに問題が検知されたときの自動復旧動作となりますため、一時的に接続が失われた場合は少し時間をおいてから操作を再試行していただきますようお願いいたします。
少し時間をおいてから操作を再試行していただくことで、高い確率で正常に実行されます。

例としまして、以下の要因により、Dynamics 365 Finance and Operations にて一時的に接続が失われ、サーバー上での処理が止まる可能性がございますので、その際には再試行を実施して頂きますようお願いします。
- Dynamics 365 Finance and Operations にて使用している Azure SQL Database 上での計画外メンテンナンス、または、Dynamics 365 Finance and Operations のサーバーと Azure SQL Database の一時的なネットワークの接続の問題。
- Dynamics 365 Finance and Operations のバッチサーバー、AOS サーバーが稼働している基盤の切り替え。何らかの異常を検知した際に、長時間のダウンタイムを防ぐために、Azure 基盤を切り替え、正常な基盤で稼働するような計画外のメンテナンスが発生する場合がございます。こちらが発生した際には、バッチサーバー、AOS サーバーが再起動される場合がございます。
- Dynamics 365 Finance and Operations の AOS サーバー の自動再起動。 Dynamics 365 Finance and Operations の AOS サーバー の負荷が高いことを検知した場合、サーバーの使用率が低い時間帯に限って、負荷を下げるために、サーバーの再起動をする場合がございます。

再試行処理の例としましては、以下の公開資料にてバッチジョブの再試行処理をご案内していますのでご参考にしていただけますと幸いでございます。
https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/sysadmin/retryable-batch



以下の公開資料にてバッチジョブの再起動例をご案内していますのでご参考にしていただけますと幸いでございます。
https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/sysadmin/batch-server-overview#understanding-batch-server-restarts


また、セキュリティ、可用性、信頼性を確保するため計画メンテナンスも実施致しております。メンテナンスが実施される日時につきましては以下の公開資料をご確認お願いします。
https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/deployment/plannedmaintenance-selfservice#windows


---
## おわりに  

以上、 Dynamics 365 Finance and Operations をご利用いただく際の留意事項、ご協力いただきたい事項についてご紹介しました。
