---
id: c5096c97-b510-4fe5-9ab4-c24f89de7dbc
blueprint: japanese_translation
title: AmplitudeでA/Bテスト結果を分析する
title_en: 'Analyze A/B test results with Amplitude'
source: 'https://help.amplitude.com/hc/ja/articles/115001580108'
---
#### この記事のテーマ：

* アプリをA/Bテストに装備する（分割テスト）
* AmplitudeでA/Bテストの結果をレビューする

A/Bテストは、ウェブサイトまたはアプリケーションの指標を改善することを目的とした、制御されたランダム化実験を行う方法です。 Amplitudeの[AB Test View](/docs/analytics/charts/funnel-analysis/funnel-analysis-interpret)（成長とエンタープライズプランで使用可能）を使用すると、各実験グループがアプリケーションでどのように振る舞うかを比較して、実験の影響を測定できます。

例えば、さまざまなグループの新規ユーザーに2つの異なるオンボーディングフローを表示し、結果を使用して、オンボーディングプロセスを完了するためにユーザーを誘導するのにどちらがより効果的かを判断できます。 または、別々のチェックアウトフローをテストして、どちらが売上を生み出すのに効果的かを確認することもできます。

**注意：**この機能は、より堅牢でフル装備の実験プラットフォームである[Amplitude Experiment](/docs/analytics/charts/experiment-results/experiment-results-dig-deeper)と混同しないでください。

## 開始前に行うこと：実験の段取りをつけてください

しかしながら、実験を行う前には段取りをつける必要があります。 ユーザーを所与の実験バリエーションに関連付けるために、ユーザープロパティを使用することをお勧めします。 ユーザープロパティは、プロダクトを使用する各個人に関する特性を反映します。 それらを使用して、Amplitude Analyticsで分析をセグメント化します。

ユーザープロパティを更新するには、主に2つの方法があります。

1) [SDK](https://help.amplitude.com/hc/en-us/articles/205406607-SDKs)と[HTTP API](/docs/apis/analytics/http-v2)：イベントアクションでユーザープロパティを更新します。

* **方法：** ユーザープロパティは、[SDK](https://help.amplitude.com/hc/en-us/articles/205406607-SDKs)または[HTTP API](/docs/apis/analytics/http-v2)を介して、各イベントで送信できます。
* **長所：**ユーザープロパティは、イベントが送信された瞬間に有効になり、プロパティ値が明示的に更新されるまで、その後のすべてのイベントでユーザーに紐づいています。
* **短所：**これらのイベントは、月次イベントボリュームにカウントされます。 さらに、これらのイベントはデフォルトでユーザーを**アクティブ**ユーザーとしてカウントします。そのため、A/Bテスト関連のイベントが[非アクティブイベント](/docs/data/change-event-activity-status)としてマークされていることを確認する必要があります。

2) [APIを識別](https://help.amplitude.com/hc/en-us/articles/205406617-Identify-API-Modify-User-Properties)：イベントを送信せずにユーザープロパティを更新します。

* **方法：**Amplitudeの[IdentifyAPI](https://help.amplitude.com/hc/en-us/articles/205406617-Identify-API-Modify-User-Properties)を使用すると、イベントを送信せずにユーザープロパティを更新できます。
* **長所：**イベントを送信せずにユーザープロパティを非同期に更新できます。また、月次イベントボリュームカウントには影響しません。
* **短所：**ユーザーがアクションを実行するまで、ユーザープロパティは有効になりません。 これは通常、ほとんどの実験では問題ではありませんが、非アクティブユーザーがあなたのアプリケーションに戻ってくるかどうかをトラックすることを目的とした**実験に影響を与える可能性があります**。  
  
たとえば、7日間以上非アクティブだったユーザーをアプリに戻すようにして、それを実現するためにメールの有効性をテストしていると仮定します。 仮に[APIを識別](https://help.amplitude.com/hc/en-us/articles/205406617-Identify-API-Modify-User-Properties)を使用してユーザープロパティを更新する場合、アプリケーションでイベントをトリガーするために戻ったユーザー（任意のイベント、どちらでもかまいません）にのみ適用されます。 メールを受信した後、ユーザーが非アクティブのままである場合、ユーザープロパティは、このユーザーには適用されません。 その結果、ユーザープロパティが添付されていないため、この非アクティブユーザーは、メールを受信した実験グループに含まれません。 このような状況では、オプション#1 — イベントアクション（例：「メール送信」と呼ばれるイベント）でユーザープロパティを更新することをお勧めします。

どのように[Amplitudeでユーザープロパティが同期されるか](/docs/data/user-properties-and-events)について詳細をご覧ください。

## ユーザープロパティをいくつ送信する必要がありますか？

Amplitudeユーザーは、分割テストの段取りをつける際に、2つのアプローチのいずれかを採用する傾向があります。

* 実験ごとに**1つのユーザープロパティを使用します**。  
  
すべてのユーザープロパティは、キーと値のペアとして受信されます。   
  
このアプローチは、実験名をキーとして、実験のすべてのバリエーションを潜在的な値として設定します。ユーザープロパティキー：実験1ユーザープロパティ値：variation\_aPros：ユーザーセグメンテーションタブから、簡単にセグメント別への実験を選択できます。短所：実行されている実験の数に応じて、ユーザープロパティの圧倒的なリストが発生できます。
* 1つのユーザープロパティを**すべての**実験に対して使用します。  
  
すべてのユーザープロパティは、キーと値のペアとして受信されます。このアプローチは、`テストを分割する`キー（または類似のもの）を設定し、値を配列に保存します。  
  
ユーザープロパティ：`テストを分割する`  
ユーザープロパティ値：[`experiment_1_value`、`experiment_2_value`]  
  
ユーザープロパティ`テストを分割する`は、チャートの[セグメンテーションモジュール](/docs/analytics/charts/build-charts-add-user-segments)で適切な値またはテストグループを選択することで、セグメンテーションできます。  
  
**長所：**分割テストに関連するユーザープロパティは（実験ごとに1つではなく）全体で1つだけであるため、ユーザープロパティリストはダッシュボードでより管理しやすくなります。  
**短所：**`append`または`prepend`が使用されている場合、配列は最大10,000文字に制限されます。 配列が文字制限を超過した場合、しきい値を超えた文字は記録されません。

Amplitudeでは、ご自身での分割テストの実験に加えて、[Optimizely](https://www.optimizely.com/)との完全な統合を提供し、各実験のユーザープロパティを自動的に更新します。詳細については、[総合ガイド](https://help.amplitude.com/hc/en-us/articles/225364647)をお読みください。

## Amplitudeで結果を表示する

実験グループ毎にユーザープロパティが更新された後、分割テストの結果のレビューを開始できます。この[ABテストビュー](/docs/analytics/charts/funnel-analysis/funnel-analysis-interpret)チャート内の機能です。

チャートコントロールパネルの[セグメンテーションモジュール](/docs/analytics/charts/build-charts-add-user-segments)を使用して、実験グループ間のアクティビティを比較できます。 これは、実験グループを追加するだけでできます。

![analyze_a_b_results_1.jpeg](/docs/output/img/jp/analyze-a-b-results-1-jpeg.jpeg)