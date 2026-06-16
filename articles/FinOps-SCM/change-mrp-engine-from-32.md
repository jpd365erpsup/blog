---
title: 10.0.32 以降の MRP エンジン (計画最適化) について
date: 2026-06-15
tags:
  - FinOps-SCM

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
1. [環境による実行可否（組み込み MRP と計画最適化の比較）](#anchor-env)
1. [リソース](#anchor-resource)
1. [おわりに](#anchor-finish)

## 更新履歴
2023 年 3 月 1 日 : ブログ公開  
2023 年 3 月 24 日 : 既存 MRP エンジンのロードマップの適用日時を追記  
2026 年 6 月 15 日 : 最新バージョンの状況に合わせて全体を更新し、「環境による実行可否（組み込み MRP と計画最適化の比較）」のセクションを追加しました。

<a id='anchor-mrp'></a>

# 既存 MRP エンジンについて
<a id='anchor-mrp-roadmap'></a>

## ロードマップ
既存 MRP エンジン (組み込み MRP エンジン、deprecated master planning engine) は Dynamics 365 Finance and Operations において非推奨となり、計画最適化 (Planning Optimization) に置き換えられています。以下の提供方針が適用されます。  
- 既存 MRP エンジンに対して新しい機能の実装は予定しておりません
- 既存 MRP エンジンに対するサポートは、ブロッカー (計画オーダーが一切作成されない、または継続的に失敗する) およびリグレッションに限定されます (2023 年 3 月以降の方針)
- バージョン 10.0.32 以降、法人で計画機能を初めて有効化する際に、計画最適化のインストールおよび有効化が必須となります
- バージョン 10.0.41 以降、新規に配置した環境では既存 MRP エンジンが完全にブロックされ、お客様がご自身で有効化する方法はありません
- 既存 MRP エンジンの削除時期は現時点で未定です (削除する場合は 12 か月前に告知されます)


<a id='anchor-mrp-support'></a>

## テクニカル サポートの対応について
既存 MRP エンジンは非推奨となるため、お問い合わせを起票いただく際には以下の内容をご確認・ご理解ください。
- 計画最適化にて事象が再現する場合のみ、再現検証および想定挙動を調査します  
  ※ 計画最適化における事象の再現可否はお客様にて検証いただきますようお願いいたします。  
  ※ 以下[*](#anchor-po-migration) でもご紹介しますが、同一環境の法人ごとに計画最適化を有効化できるため、再現検証用に法人をコピーしていただき、そこで検証した結果を基にお問い合わせいただくことを推奨いたします。
- マイクロソフトにて調査した結果、想定挙動ではないと判断した場合、計画最適化に対してのみ修正を提供します
- お問い合わせの事象が既存 MRP エンジンにおけるクリティカルな問題の場合には、事前にビジネス インパクトも併せてご提供ください  
  関連ブログ: [お客様のビジネスインパクトをお伺いする目的や算出について](https://jpd365erpsup.github.io/blog/information/what-is-business-impact/)

<a id='anchor-po'></a>

# 計画最適化 (Planning Optimization) について

<a id='anchor-po-roadmap'></a>

## ロードマップ
計画最適化では以下の提供方針が 10.0.32 以降適用されます。
- 既存 MRP エンジンとの差分機能や設定については、新規お問い合わせにて計画最適化への追加希望をご依頼いただくことで実装可否を検討するリストへ追加されます
- 計画最適化の内部処理へのカスタマイズは基本的に実装できないため、お客様の運用を計画最適化に合わせていただくことを検討ください
- 内部処理のカスタマイズを希望する箇所がある際には、Ideas に投稿ください  
  関連ブログ: [Dynamics 365 製品のフィードバックサイト Ideas について](https://jpd365erpsup.github.io/blog/information/how-to-post-ideas/)

<a id='anchor-po-migration'></a>

## 移行について
既存 MRP エンジンから計画最適化への移行は、同一環境の法人 (Legal entity) ごとに実施することが可能です。移行前には、計画の最適化フィット分析 (fit analysis) を用いて、ご利用中の機能が計画最適化でサポートされているかを評価することを推奨します。  
計画最適化の検証時に法人をコピーして使用する際には、"法人へのコピー" 機能をご利用ください。  
関連公開資料 : [法人へのコピー](https://learn.microsoft.com/ja-jp/dynamics365/fin-ops-core/dev-itpro/data-entities/copy-configuration#copy-into-a-legal-entity)

<a id='anchor-po-exception'></a>

## 例外申請
Tier 2 以上の環境では既存 MRP エンジンは基本的にブロックされています。業務要件上、やむを得ず既存 MRP エンジンの継続利用が必要な場合には、Microsoft による環境ごとの例外対応が必要となり、これらはすべてサポート リクエストにて承ります。  

例外を申請いただくにあたっては、事前に以下の準備をお願いいたします。

1. **公開資料の確認**  
   まず、計画最適化の[計画の最適化フィット分析](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-fit-analysis) と、[計画の最適化と、非推奨のマスター プラン エンジンの相違点](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-differences-with-built-in)に関する公開資料をご確認ください。
1. **業務要件に基づく検証**  
   次に、お客様の業務要件から作成したテスト データを用いて、組み込み MRP エンジンと計画最適化の挙動の違いをご確認ください。

そのうえで、確認・検証の結果に応じて、例外申請の取り扱いは以下のように異なります。

- **計画の最適化フィット分析に記載があり、予想される可用性が "将来のサイクル" 等となっている機能の場合**  
  当該機能が計画最適化で未提供であることが公開資料上で確認できるため、その記載と検証結果を添えて申請いただくことで、例外申請が承認される場合があります。
- **相違点に関する公開資料に記載がある挙動の場合**  
  それらは意図された差異となるため、例外申請は却下される場合があります。この場合は、カスタマイズの実装、または業務要件の変更をご検討ください。
- **計画の最適化フィット分析にも相違点の資料にも記載がなく、業務要件と実際の挙動に差異があり、それが業務上許容できない場合**  
  サポート リクエストにて計画最適化の修正をリクエストしてください。修正が予定された場合には、その修正がリリースされるまでの間、例外申請が承認される場合があります。
- **既に組み込み MRP エンジンを利用していて、組み込み MRP エンジン内に実装したカスタマイズを計画最適化用に再実装する必要がある場合**  
  サポート リクエストにて再実装のタイムラインを含め例外申請を提出してください。タイムライン期間中は例外申請が承認される場合があります。

<a id='anchor-env'></a>

# 環境による実行可否（既存 MRP エンジンと計画最適化の比較）

計画最適化と既存 MRP エンジンは、実行できる環境が異なる点にご注意ください。

| エンジン | 実行可能な環境 |
| ---- | ---- |
| 計画最適化 (Planning Optimization) | Tier 2 以上の Microsoft managed 環境 (高可用性) のほか、UDE (Unified developer environment) でも実行可能です。一方、Tier 1 環境や OneBox 環境では実行できません。 |
| 既存 (組み込み) MRP エンジン | Tier 1 (クラウドホスト / OneBox) 環境などでは実行可能です。一方で、現行バージョンの Microsoft managed 環境では基本的にブロックされ、実行できません。 |

このため、既存 MRP エンジンの挙動を実際に実行してご確認いただきたい場合 (例 : 計画最適化との結果差分の比較・調査) には、既存 MRP エンジンが実行可能な **Tier 1 環境**などをご利用いただく必要があります。  
なお、計画最適化自体は Tier 1 環境では実行できないため、両エンジンの結果を比較する際は、既存 MRP エンジンを Tier 1 環境で、計画最適化を Tier 2 以上の環境などで実行し、それぞれの結果を突き合わせていただく形となります。  

※ 計画最適化を有効化すると、既存 MRP エンジンは自動的に無効化されます。そのため、同一環境で両エンジンを同時に実行することはできません。

環境の種類 (Tier 1 / Tier 2 以上 / クラウドホスト / サンドボックス / 本番 など) の違いについては、以下の記事もあわせてご参照ください。  
- 関連ブログ : [Dynamics 365 Finance and Operations の環境ごとの違い](https://jpd365erpsup.github.io/blog/FinOps-Platform/environments/)

<a id='anchor-resource'></a>

# リソース
既存 (組み込み) MRP エンジンから計画最適化への移行に際して、以下の公開資料を必要に応じてご確認ください。  
- [計画最適化の使用を開始する - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/get-started)
- [非推奨のマスター プランの概要 - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/deprecated-master-planning-overview)
- [既存の法人で非推奨のマスター プランを継続して使用する - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/continue-using-deprecated-planning)
- [計画最適化と既存 MRP エンジンの相違点 - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-differences-with-built-in)
- [計画最適化にて考慮されないパラメーター - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/not-used-parameters)
- [計画最適化の機能リリース予定および履歴 - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/release-process)
- [計画最適化の適合分析 (fit analysis) - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-fit-analysis)
- [既存 MRP エンジンから計画最適化への移行 - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/new-master-planning-engine)
- [計画最適化のトラブルシューティング - Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-trouble-shooting)
- 関連ブログ : [各モジュールの Viva Engage のリスト](https://jpd365erpsup.github.io/blog/information/viva-engage-list/)


<a id='anchor-finish'></a>
---

# おわりに  

以上、 Dynamics 365 Finance and Operations における MRP エンジンの変更のロードマップや注意点を紹介いたしました。
