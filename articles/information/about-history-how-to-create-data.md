---
title: Dynamics 365 Finance and Operations の本番環境のデータの作成経緯に関して
date: 2023-12-07
tags:
  - Information
  - D365FO
disableDisclaimer: false
---

こんにちは、日本マイクロソフト Dynamics ERP サポート チームの永吉です。  
この記事では、テクニカル サポート チームがサポート リクエストにてご依頼いただく「データの作成経緯」の必要な情報について紹介します。

<!-- more -->
# 目次

1. [はじめに](#overview)
1. [過去事例の調査](#past-case)
1. [再現手順の確認](#repro-steps)
1. [データが作成された日時の確認](#create-datatime)
1. [作成経緯が判明しなかった場合](#after-follow)
1. [データ修正に向けて](#data-fix)
1. [おわりに](#last)

<a id='overview'></a>

# はじめに
Dynamics 365 Finance and Operations のサポート リクエストにて、以下のようなご依頼を頂戴することがございます。  
> 本番環境で作成されたデータについて、どのように作成されたのかを知りたい  

実際に作成経緯が不明なデータや、意図していないデータが本番環境に存在した場合、そのデータの存在が今後の運用にどのような影響を及ぼすのか測りかねるという観点や、再発防止の観点よりご依頼いただくものと認識しております。  
また、SaaS 製品の性質上サーバー サイドを全てクラウド ベンダーが管理しているため、パートナー様やエンドユーザー様にてオンプレミス製品と同様の粒度で調査する手立てがなく、サポート リクエストにてご依頼いただく、という背景もあるものと認識しております。  

上記を踏まえたうえで、Microsoft にて調査する際に必要な情報についてご紹介します。  

<a id='past-case'></a>

# 過去事例の調査
過去に別のお客様から同一事象の発生報告があったかどうかを調査いたします。その事例においてどのように対応することで事象を解消したのかも併せて調査することで、事象の解消および発生起因の特定に繋がる可能性がございます。  
データが作成された経緯が同一事象かの判断に必要となりますため、対象データに関してご認識いただいている限りの情報をご提供ください。  
例: データを作成した操作の見当、カスタマイズの有無  

<a id='repro-steps'></a>

# 再現手順の確認
作成経緯を依頼しているのに再現手順が分かればそもそも質問しない、というご意見は十分に理解しております。  
一方で、**「当時の状況と全く同じ状態の環境を用意して、全く同じ操作を実施した場合に、同じ結果になるのかどうか」** という事実が明らかにすることで、事象の発生起因を切り分けることが可能です。  
この情報の提供に際して、弊テクニカル サポートからお客様へご依頼したい手順は以下となります。  
1. 対象のデータが作成される直前の時間の本番環境のデータベースを Sandbox 環境に PITR にてリストアする  
[サンドボックス環境への運用データベースのポイントインタイム復元 - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/database/database-pitr-prod-sandbox)  
1. Sandbox 環境のデータベースをエクスポートして、LCS の資産ライブラリに格納する  
[データベースのエクスポート - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/database/export-database#self-service-export-database)  
1. Sandbox 環境にて、対象データが作成される可能性がある操作を実施する  
1. 手順が確立された場合、手順 2 で資産ライブラリに格納したデータベースのバックアップを Sandbox 環境にリストアする
1. 弊テクニカル サポートにご連絡いただき、シャドウ コピー環境の許可と再現手順をご提供ください  
[Dynamics 365 Finance and Operations の調査に用いるシャドウ コピー環境について | Japan Dynamics ERP Support Blog (jpdynamicserp.github.io)](https://jpdynamicserp.github.io/blog/FinOps-Platform/what-shadow-copy-environment/)  
1. 弊テクニカル サポートにて、シャドウ コピー環境と再現手順にて再現を確認し、調査いたします

上記手順にて再現可否をご確認いただき、その旨をご連絡ください。  

<a id='create-datetime'></a>

# データが作成された日時の確認
対象のデータがいつ作成されたのか、可能な限り正確な日時をご提供ください。  
ご提供いただいた日時の付近にて、**「エラーの発生有無を起点とした」** テレメトリーを調査いたします。  
お客様より、「Microsoft が管理している SaaS 製品なので、全てのログを確認することができるのではないか」とご質問いただくことがございます。  
こちらはいわゆるデータベース ログに該当する情報となるため、パフォーマンスの観点よりすべてのテーブルやデータに対してログを収集しないものとなっております。  
[データベース ログの構成 - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log#database-logging-and-performance)  

一方で、エラーが発生した際の情報をテレメトリーとして収集・管理しているため、その観点から調査することで事象の発生起因を切り分けることが可能です。  
上記より、テレメトリーの調査のきっかけとなるデータの作成日時をご確認いただき、その情報をご提供ください。  

<a id='after-follow'></a>

# 作成経緯が判明しなかった場合
上述の調査にて作成経緯が判明しなかった場合、そのデータの作成経緯を特定できないものとご認識ください。  
一方で、対象テーブルに対してデータベース ログを設定いただくことで、今後同様の事象が発生した際に調査で有用な情報が得られるため、ご検討ください。  
[データベース ログの構成 - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log)  

<a id='data-fix'></a>

# データ修正に向けて
データを正しい状態に修正するにあたり、以下の順番で修正方法をご検討ください。  
1. 画面上の操作にてデータを修正する
1. カスタム X++ スクリプトの実行にてデータを修正する  
[ダウンタイムなしでカスタム X++ スクリプトの実行 - Finance & Operations | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/deployment/run-custom-scripts)  
[D365FOでダウンタイムなしでカスタム X++ スクリプトを実行する方法 | Japan Dynamics ERP Support Blog (jpdynamicserp.github.io)](https://jpdynamicserp.github.io/blog/FinOps-Platform/how-to-run-custom-script-d365fo/)  

> [!NOTE]  
> Microsoft は **「標準機能に起因して作成され、カスタム X++ スクリプトにて修正できないデータ」** 以外のデータに対して、SQL スクリプトを実行してデータを修正することはありません。  

<a id='last'></a>

# おわりに  
作成経緯が不明なデータや、意図していないデータに対する調査方法や提供いただきたい情報についてご紹介しました。  
全ての作成経緯を確実に解明するための方法ではございませんが、Microsoft の収集・管理しているデータや調査に必要な情報をご認識いただけますと幸いです。