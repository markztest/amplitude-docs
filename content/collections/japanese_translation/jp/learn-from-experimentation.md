---
id: 97f46ade-43f1-4f1e-8edd-db4ee4142fac
blueprint: japanese_translation
title: 実験から学ぶ
title_en: 'Learn from experimentation'
source: 'https://help.amplitude.com/hc/ja/articles/360061687631'
---
|  |
| --- |
| この記事のテーマ：* 実験結果を参照する
* それらの結果を理解して解釈する
 |

実験が設計され、ユーザーにロールアウトされて、新しいバリアントとやり取りするのに十分な時間が与えられました。これで、仮説が正しいかどうかを確認することができます。

*[分析]*パネルでは、実験が**統計的に重要な**結果をもたらしたかどうか、そしてそれらの結果が実際に何であるかを一目で知ることができます。Amplitude Experimentは、デザインとロールアウトフェーズで提供した情報を取り出し、自動的にプラグインします。そのため、労力が節約できます。バリアントごとに結果を分解し、便利で詳細なテーブルの内訳を提供します。

**注：**この記事は、[実験をロールアウトするヘルプセンターの記事に直接続きます](https://help.amplitude.com/hc/en-us/articles/360061687611)。まだお読みでなく、説明されているプロセスに従って進んでいない場合は、次のステップに進む前に必ずお読みください。

各バリアントが100人の訪問**および**25のコンバージョンに達するまで、Amplitudeは、バイナリ指標（固有のコンバージョン）を使用する実験の統計計算を生成しません。非バイナリ指標を使用する実験は、バリアントごとに100人の訪問に到達する必要があります。

実験結果を生成して表示するには、次のステップに従ってください。  

1. 実験で、*[分析]*タブを開きます。タブには、実験の仮説を記述し、統計的有意性に達したかどうかを記録する*[サマリー]*と、*[分析]*の2つのセクションがあります。  
実験は、ランダムに結果が発生する可能性が極めて低そうだと確信できる場合、**統計的に有意性がある**と言えます。（厳密に言うと、ヌル仮説を拒否する場合にそうなります。）「可能性が極めて低そうだ」とは、どういうことでしょうか？これは、かなり主観的に聞こえるかもしれませんが、しっかりとした統計に基づいています。統計的有意性は、バリアントの**p値**に依存します。これは、バリアントとコントロールに違いがないと仮定したときに、私たちが見るデータを観察する可能性のことです。この確率が特定のしきい値を下回る場合（統計学者はこのしきい値を**アルファ**と呼びます）、実験が統計的意義を達成したと考えられます。

*[サマリー]*セクションには、統計的有意性が満たされた場合は*[有意]*とラベルされたバッジ、統計的有意性が満たされなかった場合は*[有意差なし]*とラベルされたバッジが表示されます。実験が有意性に達しなかった場合は、*[ロールバック]*ボタンをクリックして、この実験のバリアントをユーザーに表示するのを停止します。

*[サマリー]*セクションには、次のような複数のバッジが同時に含まれる場合があります。

* * * *不明*：検定は、主要指標で決定的ではなかった。
		* *目標超*または*目標未満：*検定の方向に応じて、主要指標の平均が**目標を超えた**または**目標未満**だった（増加=超、減少=未満、任意=超または未満）。
		* *[コントロール超]*または*[コントロール未満]：*主要指標の平均が、検定の方向に応じて、コントロールの平均を**超えた**または**未満**だった（増加=超、減少=未満、任意=超または未満）。これらのバッジは、統計的に有意性のある結果にのみ関連します。

![summary.png](/docs/output/img/jp/summary-png.png)

2. *[分析]*セクションの上部には、実験の実行方法の概要があり、指標とバリアントの内訳があります。その下には実験の**露出定義**があります。表示されるバリアント数、どの主要指標か、どの**露出イベント**かです。このイベントは実験に含まれる前にユーザーが発行しなければなりません。  
  
**注**：露出イベントは、**割り当てイベントと**同じではありません。例えば、価格設定ページで実験を実行している場合、ユーザーが実験のホームページで評価される場合があります。しかし、価格設定ページにアクセスしない場合、実際に露出されることはありません。そのため、このユーザーは実験の一部であるとはみなされません。  
  
露出イベントの詳細については、[Amplitude開発者センターのこちらの記事を参照してください](https://www.docs.developers.amplitude.com/experiment/general/exposure-tracking/)。  
  
露出定義は、デフォルト状態で閉じられています。これを、[開く]アイコンをクリックして開きます。  
  
![experiment_analyze_tab_3.gif](/docs/output/img/jp/experiment-analyze-tab-3-gif.gif)  
  
*[アナリティクスで開く]*をクリックして、この実験からAmplitude Analyticsでチャートを作成することができます。  
  
**注：**A/B/nテストを実行している場合、Amplitude Experimentは各処置に対するコントロールの信頼区間/P値を表示します。その代わりに2つの非制御処置の比較を表示するには、コントロールバリアントを変更する（*[設定]*タブから）、またはアナリティクスで検定を開き、対象の2つの処置を使用してチャートを作成します。
3. *[プラン]*タブの統計設定で、実験の**信頼レベル**を設定します。デフォルトは95%です。[逐次検定とt検定](https://amplitude.com/blog/sequential-test-vs-t-test)から選択することもできます。通常は、逐次検定のほうが優れた選択です。*統計設定*の変更の詳細は[こちらから](https://help.amplitude.com/hc/en-us/articles/13448368364187)お読みいただけます。  
  
**注：**実験の信頼度レベルを下げると、実験が統計的な有意性を達成する可能性は高くなりますが、その反面、実験の偽陽性の可能性も高まります。
4. 事前に設定された**期間**の選択または日付選択ツールを開いてカスタムの日付範囲を選択し、実験の分析時間の枠組みを設定します。

[分析]セクションに表示される表、グラフ、チャートは、Amplitude Experimentの[[実験分析]表示の理解](https://help.amplitude.com/hc/en-us/articles/8485952382235-Understand-the-Experiment-Analysis-view)と、[累積露出グラフの解釈に関するヘルプセンターの記事](https://help.amplitude.com/hc/en-us/articles/7985566141083-Interpret-the-cumulative-exposures-graph-in-Amplitude-Experiment)で、詳しく説明されています。

**注：**Amplitude Experimentは、結果を生成するためにコントロールを比較する何かが必要です。コントロールと**少なくとも1つの**バリアントの**両方**を含めないと、チャートは表示されません。

お疲れさまでした！実験の設計、ロールアウト、分析を正常に完了しました。

## 次へ進みましょう。

失敗した実験というものはないことを覚えておくことが重要です。希望の結果が得られなかった場合でも、テストが統計的有意性に達していなくても、プロセスから何かを学ぶことができます。結果を踏み台として、変更や結果、顧客が製品に何を期待するか、また、それをどのように提供するかについての難しい質問に進めるようにしてください。

一般に、次のステップでは、別の実験を行うために仮説を立証するような、より多くの証拠を取集するか、または最高の結果を提供するバリアントを得て、それを実装するかどうかを決定する必要があります。実験は、Amplitude Analyticsで実験分析にエクスポートして、より深く探求することもできます。そこでは、ユーザーをセグメントにして、より便利なインサイトを生成することができます。