---
title: 10.0.32 以降の MRP エンジン (計画最適化) について
date: 2023-3-1
tags:
  - FinOps-SCM
  - Master Planning

disableDisclaimer: false
---

こんにちは、日本マイクロソフト Dynamics ERP サポート チームの永吉です。  
この記事では、 Dynamics 365 Finance and Operations における MRP エンジンの変更のロードマップや注意点をご案内します。

<!-- more -->
## 目次

1. [既存 MRP エンジンについて](#anchor-mrp)
    1. [ロードマップ](#anchor-mrp-roadmap)  
    1. [テクニカル サポートの対応について](#anchor-mrp-support)
1. [計画最適化 (Planning Optimization) について](#anchor-po)
    1. [ロードマップ](#anchor-po-roadmap)
    1. [移行について](#anchor-po-migration)
    1. [例外申請](#anchor-po-exception)
1. [リソース](#anchor-resource)
1. [おわりに](#anchor-finish)

## 更新履歴
2023 年 3 月 1 日 : ブログ公開  
2023 年 3 月 24 日 : 既存 MRP エンジンのロードマップの適用日時を追記

<a id='anchor-mrp'></a>

# 既存 MRP エンジンについて
<a id='anchor-mrp-roadmap'></a>

## ロードマップ
既存 MRP エンジンは Dynamics 365 Finance and Operations として非推奨となり、以下の提供方針が 10.0.32 以降および 2023 年 3 月 20 日より適用されます。  
- 既存 MRP エンジンに対して新しい機能の実装は予定しておりません
- 既存 MRP エンジンに対して基本的にはバグ修正は実施されません (ブロッカーおよびセキュリティ関連を除く)
- 既存 MRP エンジンを Dynamics 365 Finance and Operations からの排除は予定しておりません

<a id='anchor-mrp-support'></a>

## テクニカル サポートの対応について
既存 MRP エンジンは非推奨となるため、お問い合わせを起票いただく際には以下の内容をご確認・ご理解ください。
- 計画最適化 (Planning Optimization : 以下 計画最適化) にて事象が再現する場合のみ、再現検証および想定挙動を調査します  
  ※ 計画最適化における事象の再現可否はお客様にて検証いただきますようお願いいたします。  
  ※ 以下[*](#anchor-po-migration) でもご紹介しますが、同一環境の法人ごとに計画最適化を有効化できるため、再現検証用に法人をコピーしていただき、そこで検証した結果を基にお問い合わせいただくことを推奨いたします。
- マイクロソフトにて調査した結果、想定挙動ではないと判断した場合、計画最適化に対してのみ修正を提供します
- お問い合わせの事象が既存 MRP エンジンにおけるクリティカルな問題の場合には、事前にビジネス インパクトも併せてご提供ください  
  関連ブログ : [お客様のビジネスインパクトをお伺いする目的や算出について](https://jpdynamicserp.github.io/blog/information/what-is-business-impact/)

<a id='anchor-po'></a>

# 計画最適化 (Planning Optimization) について

<a id='anchor-po-roadmap'></a>

## ロードマップ
計画最適化では以下の提供方針が 10.0.32 以降適用されます。
- 既存 MRP エンジンとの差分機能や設定については、新規お問い合わせにて計画最適化への追加希望をご依頼いただくことで実装可否を検討するリストへ追加されます
- 計画最適化の内部処理へのカスタマイズは基本的に実装できないため、お客様の運用を計画最適化に合わせていただくことを検討ください
- 内部処理のカスタマイズを希望する箇所がある際には、Ideas に投稿ください  
  関連ブログ : [Dynamics 365 製品のフィードバックサイト Ideas について](https://jpdynamicserp.github.io/blog/information/how-to-post-ideas/)

<a id='anchor-po-migration'></a>

## 移行について
既存 MRP エンジンから計画最適化への移行に際して、同一環境の法人 (Legal entity) ごとに移行することが可能となります。  
計画最適化の検証時に法人をコピーして使用する際には、"法人へのコピー" 機能のご利用ください。  
関連公開資料 : [法人へのコピー](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/data-entities/copy-configuration#copy-into-a-legal-entity)

<a id='anchor-po-exception'></a>

## 例外申請
計画最適化の例外申請が 10.0.32 以降で以下の方法および内容へ変更となります。
- Microsoft Managed ではない環境では、計画最適化へ移行を促すメッセージが表示されません
- Microsoft Managed 環境にて既存 MRP エンジンを用いて手動で MRP を実行した際に、例外申請の案内が表示されるため、内容に沿って項目を選択し、申請ください  
  ※ バッチ ジョブにて実行した際には案内は表示されず、また実行結果に影響もありません
- 検証等で複数回手動で MRP を実行する際に都度案内が表示されることが煩わしい場合は、"Customizations" の項目を "Yes" と設定ください

<a id='anchor-resource'></a>

# リソース
既存 MRP エンジンから計画最適化への移行に際して、以下の公開資料を必要に応じてご確認ください。  
- [計画最適化の使用を開始する - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/get-started)
- [計画最適化と既存 MRP エンジンの相違点 - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-differences-with-built-in)
- [計画最適化にて考慮されないパラメーター - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/not-used-parameters)
- [計画最適化の機能リリース予定および履歴 - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/release-process)
- [計画最適化の適合分析 (fit analysis) - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-fit-analysis)
- [既存 MRP エンジンから計画最適化への移行 - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/new-master-planning-engine)
- [計画最適化のトラブルシューティング - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-trouble-shooting)
- [計画最適化に関する Yammer グループ](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=17348655)


<a id='anchor-finish'></a>
---

# おわりに  

以上、 Dynamics 365 Finance and Operations における MRP エンジンの変更のロードマップや注意点を紹介いたしました。
