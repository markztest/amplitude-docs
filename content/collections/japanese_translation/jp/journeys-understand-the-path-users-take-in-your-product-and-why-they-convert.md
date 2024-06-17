---
id: 7a79aaaf-211d-4af3-bea4-27ad2e7a9b95
blueprint: japanese_translation
title: ジャーニー：プロダクト内でユーザーがたどるパスと、コンバージョンする理由を理解する
title_en: 'Journeys: Understand the path users take in your product and why they convert'
source: 'https://help.amplitude.com/hc/ja/articles/16427637651995'
---
Amplitudeの**ジャーニー**チャートには、従来の[ジャーニー](/docs/analytics/charts/legacy-charts/legacy-charts-pathfinder)、[パスファインダーユーザー](/docs/analytics/charts/legacy-charts/legacy-charts-pathfinder-users)チャートが組み込まれています。これにより、ユーザーが「プロダクトの主要なトランジション間でどのようにコンバージョン（またはコンバージョン失敗）するか」についての完全な360度分析を生成します。ユーザーのプロダクトジャーニーを、2つの方法：「特定のパスをたどったユニークユーザー数ごと」または「パスを選択した合計回数ごと」に確認することができます。

**注：**このチャートは、現在ベータ版であり、まだ開発中です。ジャーニーでは、ダッシュボード、ノートブック、公開リンク、エクスポート、Slackの展開、検索での表示など、Amplitudeの一部の機能が利用できない場合があります。これらは、今後数週間で追加される予定です。従来のジャーニー、パスファインダー、ユーザーチャート、および対応するドキュメントは、このチャートが一般公開されるまでアクセスできます。

ジャーニーチャートでは、次のことができます。

* 顧客がたどるパスをハイレベルで調査するには、まず、**パスファインダー**から、開始イベント、終了イベント、または2つのイベント間に基づいて、特定のブランチ上でドリルインします。これは、何を見たいのか必ずしも分かっていない場合に役立つ出発点です。
* **ジャーニーマップ**で深く掘り下げて、すべてのカスタマーパスを相互に比較し、詳細を理解し、頻度、類似度、または完了までの平均時間ごとにパスを分析し、最も詳細なレベルでパスが分岐する場所を簡単に確認し、変換されたパスとドロップオフされたパスを比較します。
* **トップユーザーパス**を使用して、プロセスのどこにドロップオフが発生するかに関係なく、単一のビューの各ステップでの相対的なドロップオフを理解します。

ジャーニーの一般的なユースケースは、ジャーニーマップやパスファインダー分析に示すように、**理想的な**カスタマージャーニー（ファネルチャートで生成できる）と、ユーザーが**実際に**たどっているカスタマージャーニーとの間のギャップを埋めることです。

ビジュアライゼーション（**パスファインダー**、**ジャーニーマップ**、**トップユーザーパス**）の詳細については、[*Amplitudeヘルプセンターの記事「ジャーニービジュアライゼーションの理解と使用」*](/docs/analytics/charts/journeys/journeys-understand-visualizations)を参照してください。

## ジャーニーチャートを作成する

ジャーニーチャートでは、次のパスを分析できます。

* 特定のイベントを含める
* プロパティで特定のイベントごとに除外する
* プロパティごとにイベントを展開する
* 特定のコンバージョンウィンドウ内でパスを測定する
* 単一のセグメントごとに分析する

ノイズの多いイベントを非表示にし、特定のイベントのみを表示し、繰り返しイベントを折りたたみ、カスタムイベントを表示することもできます。あるビジュアライゼーションを表示中に変更する設定は、いずれも、他のビジュアライゼーションに引き継がれます。

最後に、ジャーニービジュアライゼーションでは、イベントの削除、プロパティごとのイベント展開、イベントとプロパティペアを含むシーケンスのフィルター、イベントからのコホート作成ができます。イベントをクリックして、表示されるメニューから必要なオプションを選択します。

新しいジャーニーチャートを作成するには、次のステップに従ってください。

1. *[新規作成]>[分析]>[ジャーニー]をクリックします*。
2. [パス]モジュールで、ドロップダウンを使用して、特定のイベントで**開始**するパス、特定のイベントで**終了**するパス、または2つの特定のイベント**間**のパスを作成するか指定します。
3. *[+イベントを追加]*をクリックして、目的のイベントを追加します。
4. *パスでフィルターし、プロパティモジュールで展開し*、次をクリックします。

* *[+フィルタにイベントを追加]* - 指定されたイベントを表示するパスのみを含めるように、結果を絞り込みます。
* *[+除外するイベントを追加]* - 結果から指定されたイベントとプロパティ値を非表示にします。
* *[+イベントでグループ展開する]* - イベントごとにグループ化し、プロパティ値を個別に表示します（これは、基本的にグループ化条件を適用するのと同じです）。

5. *[測定値]*モジュールで、このチャートをユニークまたはイベント合計で測定するかどうかを指定します。
6. *[セグメント化]*モジュールで、[この分析に含めるユーザーを指定します](/docs/analytics/charts/build-charts-add-user-segments)。
7. チャート領域で、優先**バケットをしきい値未満**に設定します。このズームしきい値は、チャートでノード表示の下の境界を設定します。つまり、特定のパスを選択したユーザーの割合がしきい値以下のバケットよりも**低い**場合、Amplitudeはそのパスを表示**しません**。
8. チャートが表示されます。ノイズの多いイベントを非表示にし、特定のイベントのみを表示し、カスタムイベントを表示し、繰り返しイベントを折りたたむ場合は、*[フィルターイベント]*ドロップダウンをクリックて、選択を行います。

**注：**非アクティブイベントは、デフォルトで非表示になります。それらを表示するには、*[イベントを選択して除外]*をクリックして、表示させたいものを選択解除します

![](/docs/output/img/jp/3kd7ifhLg-hLRYwAD-5yyN3dD-YVmIhCy4U9Q6kc9j4YCTn66OvxbWwuypySg9aWWo-KeY1Xm97_DKXFbgsXc30_mPmQMkL_SEhjdYa3NKsEW8hw-IVbLS41qZn5IuQcczh-DXfR-OWlJftEN3KBcm0)

この手順で設定する変更は、[3つのジャーニービジュアライゼーションすべてに反映されますのでご注意ください。](/docs/analytics/charts/journeys/journeys-understand-visualizations)詳細については、こちらをご覧ください

## ジャーニーチャートでコンバージョンウィンドウがどのように機能するか

他のAmplitudeチャートと同様に、分析のための時間を設定する必要があります。ジャーニーチャートでは、これは**コンバージョンウィンドウ**で行われます。

![](/docs/output/img/jp/tEzAMjPOTHZ2jjsumP8BRwqaN7clzTQnhhtWdxElSGiowh8L77-tFfua6Kk5KU3V2FtBc0kiZ_2G2K0rwqyigmxKF2gRMogP_B7U5AidrM_P5xLrg9RhG5SBazwnxX0rgPKpg0VaLlkoQlTgNROFCfY)

コンバージョンウィンドウは、**クロック時間**で測定することも、**セッション**で測定することもできます。ウィンドウを時計時間の単位に設定すると、チャートには、いくつのセッションを要したかに関わらず、その時間内に完了したイベントパスが含まれます。

ウィンドウを1つのセッションに設定すると、チャートには、経過時間に関係なく（チャートでカバーされる時間を超えない限り）1つのセッション内で完了したイベントパスが含まれます。

[これでジャーニー分析を構築しました。その意味するところについては、ヘルプセンターの記事をご覧ください。](/docs/analytics/charts/journeys/journeys-understand-visualizations)

## レガシージャーニー、パスファインダー、パスファインダーユーザーにアクセスする

このジャーニーエクスペリエンスは、[パスファインダー](/docs/analytics/charts/legacy-charts/legacy-charts-pathfinder)と[パスファインダーユーザー](/docs/analytics/charts/legacy-charts/legacy-charts-pathfinder-users)チャートと、[レガシージャーニー機能](/docs/analytics/charts/legacy-charts/legacy-charts-journeys)（旧名称「ファネル分析チャート」に含まれていました）を組み合わせて構築されました。これらのレガシー分析にアクセスすることはまだ可能です：

* 興味のあるバーをタップし、*[ユーザージャーニーを表示]*を選択することで、[ファネル分析](/docs/analytics/charts/funnel-analysis/funnel-analysis-build)から任意のレガシージャーニーチャートにアクセスします。
* レガシーパスファインダーとパスファインダーユーザーチャートは、画面の左上にあるチャートスイッチャーからアクセスできます。