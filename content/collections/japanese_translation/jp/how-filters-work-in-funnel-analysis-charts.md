---
id: baa1897f-1bba-4d53-b7c7-2a281f78b456
blueprint: japanese_translation
title: ファネル分析チャートでのフィルタの機能
title_en: 'How filters work in funnel analysis charts'
source: 'https://help.amplitude.com/hc/ja/articles/14740839213339'
---
#### この記事のテーマ：

* Amplitudeがファネル分析チャートの様々なフィルタをどのように解釈するか理解します

ファネル分析でフィルタを適用する際には、特定のニュアンスがあります：

## セグメンテーションモジュールでフィルタを適用

ファネルチャートでは、セグメンテーションモジュールを介して適用されたフィルタは最初のイベントにのみ適用されます。ただし、イベントモジュールで個々のステップに直接フィルタを追加することが可能です。

**注：**Amplitudeは最初のイベントに適用されたフィルタの条件を満たすイベントをトリガーしたユーザーのみ、ファネルに入ったものとしてカウントします。

## グループ化フィルタの適用

セグメンテーションモジュールでは最大2つのプロパティに対してグループ化フィルタを適用できます。グループ化フィルタは、セグメンテーションモジュールの他のフィルタと同様、最初のイベントにのみ適用されます。

ユニークユーザー指標でユーザーがファネルのステップを複数回完了できる場合、グループ化フィルタは最初のイベントの発生を捉え、そのイベントの値をもってユーザーをバケツに入れます。

**注：**「プロパティを一定に保持」が同時に適用された場合、Amplitudeは各プロパティ値とユーザーのペアを別々のユーザーとしてカウントするため、ユーザーはそのユーザーが持つプロパティ値ごとに１回含まれることになります。

イベントにグループ化フィルタを使用することもできます（１ファネルにつきグループ化は１イベントに制限）結果は、特定のイベントまたはユーザープロパティを持つユーザーがファネルの他のステップでどのようにコンバージョンされたかを示します。

例えば、このファネル分析チャートを見てください：

![group-by_events.png](/docs/output/img/jp/group-by-events-png.png)

ここでの*グループ化*は、ユーザーの`お気に入り楽曲や動画`イベントがトリガーされた時点の`ジャンルタイプ`に対するユーザーのプロパティ値を調べ、ファネルの残りのイベントを通してどのようにコンバージョンしたかを示しています。

例えば、`お気に入りの楽曲や動画`イベントがトリガーされた時点で、`ジャンルタイプ`の`ポップ`のプロパティ値を持つユーザーは、`楽曲や動画`再生イベントの`ポップ`プロパティバーにも表示されます。

**注：**ファネルのユーザーが複数回ステップを完了できる場合、この方法は各イベントの最初の発生を受け、そのイベントの値でユーザーをバケツに入れます。

### 