---
title: LCSにてDynamics 365 Finance and Operationsに関するサポートリクエストを起票する方法
date: 2024-03-04
tags:
  - FinOps-Platform
  - LCS
  - Support Request
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームです。
この記事では、LCS にて Dynamics 365 Finance and Operations に関するサポートリクエストを起票する方法を紹介します。

<!-- more -->
> [!NOTE]
> 今後、サポートリクエストは LCS からではなく Power Platform 管理センターから起票いただくよう変更されます。当初、2023 年 11 月中には移行される予定でしたが予定は変更されました。移行に関しましては以下の公開資料をご確認いただきますようお願いいたします。
> [Migration of the Lifecycle Services Support experience to Power Platform admin center - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/support-migration-to-ppac)
> また、以下の Yammer でもご案内しておりますのでご参考にしていただけますと幸いでございます。
> https://www.yammer.com/dynamicsaxfeedbackprograms/threads/2690219038474240


## 更新履歴
2022 年 10 月 13 日 (木) : Advanced Diagnostic Information 箇所を追記しました。
2023 年 11 月 2 日 (木) : LCS から Power Platform 管理センターへの移行について追加しました。
2023 年 11 月 10 日 (金) : LCS から Power Platform 管理センターへの移行の予定の変更について追加しました。
2024 年 3 月 4 日 (月) : LCS から Power Platform 管理センターへの移行の予定に関する公開資料のリンクを追加しました。


## 手順
1.  LCSにログインする
2.  サポートリクエストを起票したい環境の含まれているプロジェクトを選択する  
    ![](./submit-an-incident-in-lcs/step2.png)

3.  画面上部の三本線より、「サポート」を選択する  
    ![](./submit-an-incident-in-lcs/step3.png)

4.  画面左部より、「サポート案件」 > 「Microsoftに送信済み」 > 「インシデントの送信」を選択する  
    ![](./submit-an-incident-in-lcs/step4.png)

5.  画面右部に「新しいサポート要求」画面が表示されるので、各項目を入力・選択し、「ソリューションを見る」を選択する  
    ![](./submit-an-incident-in-lcs/step5.png)

6.  表示された詳細情報にて解決できない場合、「次へ」を選択する  
    ![](./submit-an-incident-in-lcs/step6.png)

7.  「サポートプラン情報」画面が表示されるので、サポートプランを選択する  
※ 主要アクセスIDおよび契約IDを持っていない場合、サポートプランにて ”Dynamics AX - Subscription” を選択いただくことで、サポートサービスを受けることができます。  
※ ”Dynamics AX - Subscription” を選択した場合、貴社サポート契約に紐づかない形でのサポートリクエストとなり、貴社にて有償サポート契約を持っていた場合でも、その契約に応じたサポートサービスを適切に受けられない可能性がございます。予めご了承ください。  
    ![](./submit-an-incident-in-lcs/step7.png)

8.  サポートプランを選択する  
※ 20 MB以上のファイルを添付したい場合、サポートリクエストでのやり取りにて、弊社よりファイルアップロードリンクを提供いたします。  
    ![](./submit-an-incident-in-lcs/step8.png)

9.  Advanced Diagnostic Information を一読し、 「Allow Access to Diagnostix Information」 を選択する  
※ 本項目は Microsoft にて管理している環境情報等を、本件の調査にて確認することに関する同意となりますため、 Allow をご選択いただけますと幸いです。
    ![](./submit-an-incident-in-lcs/step8a.png)

10.  「この要求に関する連絡先の情報」画面が表示されるので、国/地域、メールアドレス (TO, CC) 、電話番号、希望の連絡方法を選択し、「送信」を選択する  
    ![](./submit-an-incident-in-lcs/step9.png)


（関連情報）  
https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/cloud-powered-support-lcs#open-a-new-incident  
  
  
---
## おわりに  
