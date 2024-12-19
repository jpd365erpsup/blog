---
title: 適格請求書等保存方式 (インボイス制度) の対応状況について
date: 2023-03-23
tags:
  - FinOps-Finance
  - New Invoicing system requirements
  - Japan localization
disableDisclaimer: false
---

こんにちは、Dynamics ERP サポートチームの木村です。  
この記事では、 2023 年 10 月 1 日より開始される適格請求書等保存方式 (インボイス制度) について  
Dynamics 365 Finance における対応状況を随時更新して参ります。  

<!-- more -->
弊社では各チャネルでお客様への情報公開の準備を進めています。  
記事更新時点で公開が確認されているものおよび公開が予定されているものについて記載しています。  

なお制度の詳細については国税庁ホームページをご確認ください。  
[No.6498 適格請求書等保存方式（インボイス制度）](https://www.nta.go.jp/taxes/shiraberu/taxanswer/shohi/6498.htm)  

## 目次
1. [変更予定の内容](#update-contents)
1. [情報公開チャネル](#information-channel)
1. [既知の事象一覧](#bug-list)
1. [既知の制限一覧](#limit-list)
1. [公開済みの機能](#published-function)
1. [経過措置について](#transitional-measures)


<a id='update-contents'></a>

## 変更予定の内容
売掛金管理の請求書、買掛金管理の請求書、プロジェクト請求書および各種月次締め請求書にて  
適格請求書発行事業者としての登録番号が記載されるようになります。  
また、請求書の消費税欄には総額から算出した消費税額を表示するように変更が行われております。  
  
<a id='information-channel'></a>

## 情報公開チャネル
公開資料  
  [Registration IDs - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/europe/emea-registration-ids)  
  [Qualified Invoice System in Japan - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/japan/apac-jpn-qualified-invoice-system)


<a id='bug-list'></a>

## 既知の事象一覧
| No. | 事象 | 方針 | 関連情報 |
| ---- | ---- | :----: | ---- |
|  1 | 消費税の照会をすると「実際の消費税の合計金額」に関係ない値が表示される | 修正済み | [Issue 862723](https://fix.lcs.dynamics.com/Issue/Details?kb=0&bugId=862723&dbType=3&qc=123e2bb4dbd398f8806c38f8d9762c700bc4252c18701c7ff6a91d3c627b4c2d) |
|  2 | 10 %と 8 %の税調整金額の合計が 0 円のときに消費税金額に再計算された金額が<br>月次締め請求書に表示されていない | 修正予定 | [Issue 868315](https://fix.lcs.dynamics.com/Issue/Details?kb=0&bugId=868315&dbType=3&qc=1a5d7c73e01fb306a7b1ff69f066d6102465865a22547d5138f387bb5741489b) |
|  3 | 10 %と 8 %の税調整金額の合計が 0 円のときに作成される消費税調整の伝票トランザクションに<br>顧客 ID が設定されていない | 対応予定<br>(時期未定) | [Ideas](https://experience.dynamics.com/ideas/idea/?ideaid=fd1411fd-06b1-ee11-92bd-6045bdaf814b) |
|  4 | 消費税調整で作成された顧客トランザクションに支払期日が自動計算されておらず<br>転記日と同じ日付が設定されていて、支払条件や支払方法も設定されていない。 | 対応予定<br>(時期未定) | [Ideas](https://experience.dynamics.com/ideas/idea/?ideaid=d1f95876-f4b0-ee11-92bd-6045bdaf814b) |
|  5 | 税調整金額に対して入金消込を実行したが月次締め請求書の未払金額に税調整金額が表示される | 修正予定 | [Issue 864075](https://fix.lcs.dynamics.com/Issue/Details?kb=0&bugId=864075&dbType=3&qc=fea454aa599fdaa26937d12e9e8bc48b663a73704782eadd65aa1a55a3305034) |
|  6 | 税調整金額がマイナス金額の場合に入金処理を実行して全額消込したが<br>支払済金額には税調整分の金額しか表示されず、未払い金額に金額が表示される | 修正予定 | No.5 と同様 |
|  7 | プロジェクト請求書で適格請求書を出力できない | 対応予定<br>(時期未定) | [Ideas](https://experience.dynamics.com/ideas/idea/?ideaid=6abad8dc-3293-ee11-a81c-000d3a7e6e50) |
|  8 | 適格請求書 (黒伝票) と適格返還請求書 (赤伝票) が分けて計算されない | 対応予定<br>(時期未定) | - |
|  9 | 言語設定が "EN-US" 以外に設定されているとき、事業者番号が印字されない | 修正済み | [Issue 843227](https://fix.lcs.dynamics.com/Issue/Details?kb=0&bugId=843227&dbType=3&qc=44bf9b8ffa1fd15facbc5a2ea32f576af8603a069ac10338665f78e9c438941d) |
| 10 | 月次締め請求書の転記後、「一時売上税取引」画面で売上税の詳細等が表示されない | 対応予定<br>(時期未定) | [Issue 862481](https://fix.lcs.dynamics.com/Issue/Details?bugId=862481&dbType=3&qc=de4d0061c5cccd43e3c4657f3c11d4b95980649f039429917a75491d94a741c8) |
| 11 | 顧客ごとに税調整データを作成するかどうか設定できない | 対応予定<br>(時期未定) | - |

<a id='limit-list'></a>

## 既知の制限一覧  
本項目では、本機能のリリース時の検討 または リリース後にお客様から指摘いただいた際の再検討 にて製品実装上の制限と判断したものをご案内しております。  

| No. | 事象 | 関連情報 |
| ---- | ---- | ---- |
| 1 | 仕訳伝票に自由書式で説明を記載できる項目がない | [Issue 862451](https://fix.lcs.dynamics.com/Issue/Details?bugId=862451&dbType=3&qc=eded77cc7363325332285dd7347c41836bb866bd1dafb4e3f5b90abdea4c9ab8) <br> [自動転記の既定の説明の設定 - Finance \| Dynamics 365 \| Microsoft Learn](https://learn.microsoft.com/ja-jp/dynamics365/finance/general-ledger/set-up-default-descriptions-for-automatic-posting#set-up-default-descriptions) |
| 2 | 月次締め請求書の通貨として JPY 以外が設定できない[*](#note-limit-no2) | [Issue 861848](https://fix.lcs.dynamics.com/Issue/Details?bugId=861848&dbType=3&qc=a6d13a2c4fcf86ae5504e5e7c15794f152c266d9a04a30d8431af19e3c1a9e89) <br> [Consolidated invoices for Japan - Finance \| Dynamics 365 \| Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/japan/apac-jpn-consolidate-invoices#assumptions-and-limitations) |
| 3 | 「請求書売上レポート」出力時に「実際の消費税額」が合計金額に含まれない | - |

> [!NOTE]  
> 対応予定 (時期未定) の事象 および 既知の制限 につきましては、Ideas を新規で投稿または既存の投稿に賛成票 (Vote) を投じることで、日本における影響度を開発チームに伝えることが出来るため、積極的にご投稿・ご投票ください。

<a id='note-limit-no2'></a>
既知の制限 No.2 の機能につきましては、当初実装する方針で対応を進めておりましたが、技術的な複数の課題が潜在的に対して大規模かつ複雑な対応が必要となるため、現時点における制限となりました。

<a id='published-function'></a>

## 公開済みの機能
適格請求書発行事業者の登録番号を入力する機能がバージョン 10.0.34 にてリリースされております。  
登録方法は以下の記事にてご案内しております。  
[適格請求書等保存方式 (インボイス制度) における事業者番号の登録および請求書への印字について | Japan Dynamics ERP Support Blog](https://jpdynamicserp.github.io/blog/FinOps-Finance/new-invoicing-system-requirements-QIInumber-setting/)


<a id='transitional-measures'></a>

## 経過措置について
免税事業者などとの仕入取引に対する経過措置の対応方法を以下の記事で公開しております。  
[適格請求書等保存方式 (インボイス制度) における経過措置の対応方法について | Japan Dynamics ERP Support Blog](https://jpdynamicserp.github.io/blog/FinOps-Finance/new-invoicing-system-requirements-transitional-measures/)

## おわりに  
以上、適格請求書等保存方式 (インボイス制度) の対応状況についてご案内いたしました。  
