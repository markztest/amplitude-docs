---
id: 524945e4-f5be-4906-a346-017c5d6cdb8f
blueprint: japanese_translation
title: 'FAQ：Amplitude Experimentでの実験期間の推定'
title_en: 'FAQ: Estimating the duration of an experiment in Amplitude Experiment'
source: 'https://help.amplitude.com/hc/ja/articles/9198556822299'
---
実験期間の推定は、統計的に有意な結果を生成するために必要な実験時間を予測するように設計されています。 主要指標と逐次テストでのみ使用できます。 Experiment Resultsでは、現在サポートされていません。

## どのように機能するか？

Amplitude Experimentは、コントロールとバリアントの平均、分散、露出を使用して、期待される行動を予測し、実験が統計的有意性に達するまでにかかる日数を計算します。Amplitude Experimentは、時間の経過とともにより多くのデータを受信するため、この予測は改善されます。ただし、実験中にこれらの入力のいずれかが大幅に変化した場合、予測の精度が低下する可能性があります。

## 期間の推定が表示されないのはなぜですか？

フォロー基準が満たされると、期間の推定が表示されます。

* 次の統計的仮説が満たされます。
	* 絶対リフトは、信頼区間外である
	* 信頼区間は**反転される**（低信頼区間>上位信頼区間）。これは、実験の実行中に処置またはコントロールの平均が変動する場合、または実験のロールアウトウェイトまたはターゲットセグメントが変更された場合に発生する可能性があります。
	* 標準エラーが非常に小さい
	* 分散が「負」である
	* コンバージョン率 > 1または < 0（該当する場合）
* 指標がまだ統計的有意性に達していない
* 分析ウィンドウの終了日が過去である
* 実験には十分なオブザベーションがある
* 実験がロールアウトまたはロールバックされた

推定が表示されていない場合は、これらの基準の1つ以上が満たされていない可能性があります。

## 最悪のケース、平均ケース、ベストケースの意味は何ですか？

Amplitude Experimentは、最悪のケース、平均ケース、ベストケースを使用して、仮説検定が統計的有意性に達するまでの時間の推定に固有の不確実性を記述します。 

* 3日間の**ベストケース**推定：20％の確率で、実験は3日以内で統計値に達する
* 7日間の**平均ケース**推定：50%の確率で、実験は7日以内に統計値に達する
* 10日間の最悪のケース**の推定：80%の確率で、実験は10日以内に統計値に達する**

## 期間の推定にキャップはありますか？

はい。 期間の推定は、現在、次の理由から40日に制限されています。

* 期間の推定は、リアルタイムのシミュレーションを使用し、遅延はシミュレーションされた日数でスケーリングされます。
* 特に、実行時間が長い実験では、平均と標準偏差が時間の経過とともに変化しないことを考慮するのは賢明ではありません。
* 短期予測は、長期予測よりも正確に行うのが簡単です。 （ですから、例えば、10日間を超える天気予報はめったにないのです。あっても、その日が近づくにつれて頻繁に変更されます。）
* ほとんどの実験は、完了までに40日以上かける必要はありません。

## Amplitude Experimentは、1日の露出数をどのように決定しますか？

Amplitude Experimentは、1日の露出を一定数に割り当てます。 1日あたりの露出は、累積露出（今日の時点）を、実験がこれまでに実行された日数で割って計算します。

## どのような種類のエラーがありますか？

実験期間の推定は、依然として推定であり、グラウンドトゥルース（Ground Truth）として解釈されるべきではありません。 これは、発生する可能性のあるエラータイプのリストです。 

### 既約エラー

既約エラーは、推定プロセスに固有のエラーです。残念ながら、修正することはできません。

シミュレーションで、各々は異なる時刻に統計的有意性に達します。この相違が複数のシミュレーションを実行する主な理由です。これがランダム性の仕組みです。実際、実験が統計値に達するまでにかかる時間は、実際にはランダム変数そのものです。 これはp値に依存しますが、実験で収集するデータによって異なります。コントロール平均をカンニングして知っているふりをし、標準偏差、処置平均、処置標準偏差を制御し、すべてに正規分布と独立性を強制しても、エラーをゼロに減らすことはできません。

詳細については、この[ビデオを参照してください](https://www.youtube.com/watch?v=uoV1g3i9Qmw&ab_channel=MachineLearningTV)。

### 誤った推定

Amplitude Experimentが期間の推定を生成する場合、サンプル推定でコントロール母平均と母集団標準偏差、およびその他を推定します。これらの推定値は、可能な限り正しいものとなります。とはいえ、ここにもエラーの可能性があります。 

### ドリフト

例えば、今日のコントロール平均が5に等しく、今から10日後のコントロール平均が15に等しくなる場合、コントロール平均にドリフトがあります。 ドリフトの一般的な例は、季節によるものです。 統計のいずれかにドリフトがある場合、推定はうまくいきません。 推定値は、仮説検定を行っている時にドリフトを前提としていないからです。
