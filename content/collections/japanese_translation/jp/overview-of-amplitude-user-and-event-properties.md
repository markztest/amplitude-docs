---
id: e62bc81a-674c-498c-96ab-3cfc8c49e3e7
blueprint: japanese_translation
title: Amplitudeのユーザープロパティとイベントプロパティの概要
title_en: 'Overview of Amplitude User and Event Properties'
source: 'https://help.amplitude.com/hc/ja/articles/115002380567'
---
Amplitudeでは、**プロパティ**とはユーザーとユーザーがトリガーするイベントに関する追加のコンテキストを提供する属性のことです。Amplitudeには2種類のプロパティがあります:

1. **ユーザープロパティ:** ユーザープロパティは個々のユーザーの属性です。一般的なユーザープロパティには、デバイスの種類、場所、ユーザーID、ユーザーの有料と無償の区分などが含まれます。属性は、性質と更新頻度に基づいて、現在または過去の値を反映している場合があります。
2. **イベントプロパティ:** イベントプロパティは特定のイベントの属性です。イベントプロパティに含まれる値は、イベントがトリガーされた時点の値です。例えば、JoinCommunityというイベントは`Type`のイベントプロパティを持っている可能性があります。これはそのイベントの`発生時`に参加したコミュニティの種類を示します。

この記事では、ユーザープロパティとイベントプロパティの動作、これらのプロパティをAmplitudeがどのように更新して適用するか、Amplitudeプロジェクトでプロパティを非表示にする方法についてご説明します。

**注：**イベント、ユーザー、プロパティの詳細については[Amplitudeアカデミー](https://academy.amplitude.com/amplitude-getting-started-with-analytics/1092674/scorm/40m548g557cd)の当コースを受講してください。

## ユーザープロパティ

上記の通り、ユーザープロパティはそれが関連付けられているユーザーに関する有益な詳細情報を説明する属性です。Amplitudeはすべてのイベントでユーザープロパティを送信します。

AmplitudeのSDKはデフォルトで次のユーザープロパティをトラックします:

* プラットフォーム
* デバイスの種類
* デバイスファミリー
* 国
* 市区町村
* 地域
* 開始バージョン
* バージョン
* 通信事業者
* OS
* 言語
* ライブラリ
* IPアドレス

各プロパティの定義は[こちら](/docs/get-started/user-property-definitions)で確認いただけます。

**注意:** デフォルトのプロパティに対して[自動トラッキングを無効](https://developers.amplitude.com/docs/ios#disable-tracking)にしたい場合、[JavaScript](https://help.amplitude.com/hc/en-us/articles/115001361248-JavaScript-SDK-Installation#settings-configuration-options)、[Android](https://help.amplitude.com/hc/en-us/articles/115002935588-Android-SDK-Installation#disable-automatic-tracking-of-user-properties)または[iOS](https://help.amplitude.com/hc/en-us/articles/115002278527-iOS-SDK-Installation#disable-automatic-tracking-of-user-properties) SDKの構成から行うことができます。これにより、まだデータが送信されていない新規作成されたプロジェクトでAmplitudeがデフォルトのプロパティをトラックしないようにすることができます。

カスタムユーザープロパティをセットアップすることもできます。ユーザーとユーザーが使用するデバイスに固有の特徴や特性を選択するようにします。さもないと、ユーザープロパティから収集されるデータがそれほど役に立たないことがあります。カスタムユーザープロパティの良い例としては、ゲーム内のリフェラルソース、プランの種類、友人の数、現在のレベルなどがあります。

Amplitudeのロゴを探して、デフォルトのAmplitudeユーザープロパティとカスタムユーザープロパティを区別できます。ロゴが記載されているプロパティはデフォルトのユーザープロパティです。カスタムユーザープロパティの名前はそのロゴが前に付いていません。

Amplitudeの顧客は通常はデフォルトのプロパティ以外に最大20のカスタムユーザープロパティを実装します。

### Amplitudeによりユーザープロパティを更新する

ユーザーがAmplitudeにより取得されたイベントを発動するときに、各ユーザープロパティの現在値が含まれますが、これらの値は時間の経過とともに変化する可能性があります。例えば、ユーザーがニューヨークからダラスに転居する、または無料ユーザーから有料ユーザーに変更するな場合があります。これが起こる場合、Amplitudeはユーザープロパティを更新し、その時点からユーザーが送信するイベントに新しい値を適用します。ユーザープロパティの値の更新は過去に遡って**適用されません**。古くなった値は履歴データで管理されます。つまり、プロパティの値は常にイベント発生時の値を反映しています。

例えば、下の画像で、このユーザーは午前10時12分にコミュニティに参加しています。 `Communities_Joined` プロパティの値が448になりました。

![Screen_Shot_2019-10-04_at_17.24.52.png](/docs/output/img/jp/screen-shot-2019-10-04-at-17-24-52-png.png)

このユーザーは約1週間前の9月21日午後7時54分にもコミュニティに参加しています。そのイベントを選択すると、 `Communities_Joined` プロパティに447と表示されます。これは `Join Community` イベント発生時の値です。

![Screen_Shot_2019-10-04_at_17.24.41.png](/docs/output/img/jp/screen-shot-2019-10-04-at-17-24-41-png.png)

ユーザーの[個々のイベントストリーム](/docs/analytics/user-data-lookup)の各イベントに表示されているユーザープロパティは*イベント発生時*のユーザープロパティの値を取得します。 この情報はIdentify call経由で送信される最新のイベントに由来します。

**注意:** すべてのイベントでカスタムユーザープロパティを送信する必要はありません。ユーザープロパティが設定されると、その値は永続し、Amplitudeはその値が変更されるまで後続のすべてのイベントにこの値を適用します。ユーザープロパティは[Identify API](https://help.amplitude.com/hc/articles/205406617)から後で更新できるため、イベントにカスタムユーザープロパティを適用し忘れても心配ありません。ただし、後でAmplitudeでこのイベントをクエリした場合、更新後のユーザープロパティはこのイベントに表示されず、その時点以降のイベントにのみ適用されます。

#### 新旧のユーザープロパティの値が重複するとき

ユーザープロパティの値が変更されるとき、Amplitudeのチャートに新旧両方のユーザープロパティのカテゴリにユーザーを表示できます。この重複はプロパティ値が変更された特定の日付にのみ適用されます。

例えば次のように機能します。7月1日にユーザーがゲームアプリ（この時点でバージョン1.8）にログインし、いくつかゲームをプレイします。後日、ユーザーがアプリを最新のバージョン2.0にアップグレードし、さらにいくつかゲームをプレイしました。アクティブユーザーの日次チャートをバージョン別にセグメント化して、バージョン1.0と2.0を比較する場合、そのユーザーはその日の両方のセグメントに表示されます。一方、7月2日以降、このユーザーはユーザーがさらに新しいバージョンにアップグレードするまで、バージョン2.0のセグメントに表示されます。

ユーザーセグメントをチャートに適用した場合も同じことが起こります。イベント発生時にユーザープロパティに値がない場合、Amplitudeは `(none)` という値を表示します。最初の`PlaySong`イベントのユーザーの値が isPaying =  `(none)` で、次の`PlaySong`イベントの値が`isPaying`  =  `True`の場合、ユーザーは両方のバケツに表示されます。そのユーザーの[ユーザーアクティビティ](/docs/analytics/user-data-lookup)のページを見ると、そのプロパティの最新の値のみがユーザーのプロフィール上のセクションに表示されていることが確認できます。

### Amplitudeでユーザープロパティをイベントに適用する

ユーザープロパティは次の3つの方法でイベントに適用できます:

1. **イベントが送信される *前に*ユーザープロパティを更新する:** プロパティの値がユーザープロパティテーブルで更新され、Amplitudeに送信される次のイベントに適用されます。 更新したプロパティの値が正しくイベントに適用されるようにするため、これはユーザープロパティの更新に推奨および期待される方法です。
2. **イベントが送信された*後に*ユーザープロパティを更新する:** イベントがAmplitudeに送信された後、プロパティの値がユーザープロパティテーブルで更新されます。更新された値は別のイベントが送信されるまでUIに反映されません。
	* イベント後にIdentify callが送信された場合、更新された値はそのイベントに*反映されません*。更新後の値はユーザーのプロフィールの上に反映されますが、Identify callの後に別のイベントが送信されるまでチャート結果に表示されません。
3. **イベントと*一緒に*ユーザープロパティを送信する:** Amplitudeの[HTTP API](https://help.amplitude.com/hc/en-us/articles/204771828-HTTP-API)経由で送信されたイベントで、サーバー側のコールにユーザープロパティを含めることができます。更新されたユーザープロパティの値はイベントがAmplitudeで受け取られるとすぐにUIに反映されます。イベントが取り込まれた後、ユーザープロパティテーブルも更新されます。ユーザープロパティテーブルの値が再度更新されるまで、以後のイベントには更新後のユーザープロパティの値が含まれます。

新しいユーザープロパティの値がUIに反映されるようにするためには、イベントは更新をフォローするか、更新と一緒に送信される必要があります。ユーザープロパティは[Identify API](https://developers.amplitude.com/docs/identify-api)経由で更新できます。 Identify APIを使用する前にこれに関するドキュメンテーションをよくお読みの上、理解してください。

![pasted_image_at_2017_04_11_06_16_pm.png](/docs/output/img/jp/pasted-image-at-2017-04-11-06-16-pm-png.png)

## イベントプロパティ

イベントプロパティは、ユーザーが発動するイベントの属性で、開発者はこれをAmplitudeに送信します。各イベントにはそれ自身のイベントプロパティのセットがあります。これらのプロパティの性質は、プロダクトの種類と開発者が解析に最も関心がある特定の情報の両方によって決まります。例えば、 `Swipe` がトラックするイベントである場合、 `Direction` というイベントプロパティには `Left` または `Right` の値が入ります。

イベントプロパティの例としては、説明、カテゴリー、種類、時間、レベル、完了率（%）、カウント、ソース、ステータス、数、ライブ、認証済み、エラー数、ランク、アクション、モードなどがあります。イベントプロパティは、トラックするイベントの数を削減したり、イベントの分析を改善したりするために使用します。

**注：**Amplitudeは、イベントベースのプラットフォームであり、イベントはトリガーされた時点でイベントプロパティとユーザープロパティと共に記録されます。これはチャートに反映されます。チャートが期待した結果を返さない場合、間違ったプロパティタイプでクエリしている可能性があります  
  
。例えば、`メ`ールというユーザープロパティと`メ`ールという別のイベントプロパティがあるとしましょう。ユーザープロパティ`のメ`ールにはすべてのデータが保存されていますが、代わりにイベントプロパティの`メ`ールでメールを指定してクエリを実行すると、チャートは予期しない結果を返すでしょう。ドロップダウンリストを上下にスクロールすると、*イベントプロパティ*と*ユ*ーザープロパティの両方が表示されます。必ず正しい方を選択してください！

## プロパティの非表示

[必要に応じて、古いプロパティやバグのあるプロパティを非表示にする](/docs/data/remove-invalid-data)ことができます。イベントプロパティまたはユーザープロパティを非表示にすると、プラットフォームUI上で非表示になりますが削除されることはありません。非表示にしたプロパティはいつでも再表示できます。