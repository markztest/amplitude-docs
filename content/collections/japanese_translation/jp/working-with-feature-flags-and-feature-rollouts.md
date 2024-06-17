---
id: 8d7143e5-03a1-4e08-a161-77d5a73ba82d
blueprint: japanese_translation
title: 機能フラグと機能ロールアウトでの作業
title_en: 'Working with feature flags and feature rollouts'
source: 'https://help.amplitude.com/hc/ja/articles/360061687311'
---
|  |
| --- |
| この記事のテーマ：* Amplitude Experimentで**フラグ**の役割を理解する
* 新しいフラグを作成する
* フラグを使用して、新しい機能をロールアウトする
 |

Amplitude Experimentでは、**フラグ**は実験と機能の両方のロールアウトを推進します。フラグは、新しいコードを毎回導入することなく、プロダクトの機能を有効または無効にする方法です。Amplitude Experimentでは、*アクティブ*スイッチをオンまたはオフに切り替えて操作します。フラグは、実験を始めるか、十分なデータを収集した後に実験を終了するか、または新しい機能をロールアウトする（必要に応じて、迅速にロールバックする）場合に理想的です。

この記事では、**機能ロールアウト**でフラグを作成する方法について説明します。実験でのフラグの使用方法の情報については、[実験をユーザーにロールアウトする](https://help.amplitude.com/hc/en-us/articles/360061687611)ヘルプセンターの記事を参照してください。

## 新しいフラグを作成する

デプロイメントを作成してSDKをインストールするまで、新しい機能フラグを作成することはできません。完了したら、次のステップに従ってください。

1. メインの[実験]ページから、*[+新規]*をクリックして、ドロップダウンメニューから*[ロールアウト]*を選択するか、または左側のサイドバーから[フラグ]ページに移動して、*[+フラグを作成]をクリックします*。
2. *[フラグを作成]*モーダルで、*[プロジェクト]*ドロップダウンメニューから、このフラグを含むプロジェクトを選択します。次に、フラグに名前と説明を付けます。これは、コードベースで使用されるフラグの識別子です。Amplitude Experimentは、選択した名前からフラグキーを自動的に生成します。  
  
![experiment_create_rollout.png](/docs/output/img/jp/experiment-create-rollout-png.png)
3. 実験の[評価モード](https://www.docs.developers.amplitude.com/experiment/general/evaluation/local-evaluation/)は、*[リモート]*（Amplitudeサーバーで評価される）または*[ローカル]*のいずれかを指定します。次に、この実験に使用するバケットユニットを**指定します**。  
  
**ヒント：**最適のバケットユニットは通常、ユーザーです。ただし、一部のB2Bユースケースでは、バケットユニットとして会社のIDまたは都市を使用する場合があります。例えば、会社のIDでバケットを行うことで、特定の企業内のすべてのユーザーが同じユーザーエクスペリエンスを持つことが確実になります。どのユニットを選択しても、[処置に対する効果の安定性条件](https://blogs.iq.harvard.edu/violations_of_s#:~:text=Methods%20for%20causal%20inference%2C%20in,treatments%20of%20others%20around%20him)が保たれていることを確認してください。
4. 完了したら、*[作成]*をクリックします。Experimentは、フラグの空白のテンプレートを開きます。
5. 次に、*[設定]*タブの横の**[デプロイメント]**ドロップダウンメニューから実験のための*デプロイメントを*選択します。デプロイメントでの作業の詳細については、[Amplitude Experimentの設定に関するこちらの記事](https://help.amplitude.com/hc/en-us/articles/360061270372)を参照してください。
6. *[詳細設定]では*、バケット・ソルトを変更できます。しかし、変更した場合、実験でユーザーがバリアントを切り替える可能性があります。そのため、**何をしているのかがわからない限り、**バケット・ソルトを変更しないことを推奨します。詳細については、[Amplitude Experimentでランダム化がどのように機能するか](https://help.amplitude.com/hc/en-us/articles/360061687351)についてのヘルプセンターの記事を参照してください。
7. フラグには、少なくとも1つの**バリアントが必要です**。バリアントは、ユーザーにロールアウトすることを求める、新しい機能またはプロダクトエクスペリエンスです。  
  
フラグを最初に作成する場合、Amplitude Experimentは自動的に`true`のバリアントを生成します。これはフラグがアクティブのときに返されます。このバリアントは編集できます。追加する他のバリアントはデフォルトで`false`値で、フラグがアクティブでないことを示しています。  
  
機能フラグに必要なだけ多くのバリアントを追加できます。  
  
フラグにバリアントを追加するには、*[+バリアントを作成]をクリックします*。[バリアントを作成]モーダルが表示されます。  
  
適切なフィールドで、バリアントの名前と説明を入力![スクリーン](/docs/output/img/jp/sukurin.png)  
  
します。Amplitude Experimentは、入力した名前からバリアント値を自動的に生成します。 バリアント値は、コードベースでフラグとして使用する文字列です。完了したら、*[バリアントを作成]*をクリックします。

**注意**：バリアントに**「OFF」**という名前を**付けないでください**。Amplitude Experimentでは、この名前は、フォールバック（実験に含まれていないユーザーセグメント）に予約されています。

8. *[割り当て]*パネルでは、新しい機能が表示される**ユーザーセグメント**を定義して、ロールアウトするユーザーの割合を指定し、各バリアントの相対的な配布ウェイトを設定できます。

ユーザーセグメントを定義すると、特定の地理的な場所でユーザーへのロールアウトを制限する場合、または特定の人口統計グループに属するユーザーや製品で特定の使用しきい値を満たすユーザー（パワーユーザー）へのロールアウトを制限する場合に役立ちます。

ユーザーセグメントを定義するには、*[ルールベースのユーザーセグメント]*セクションにスクロールして、[セグメント1]をクリックします。次に、Amplitude Analyticsでユーザーセグメントを構築するに使用するものと同じステップに従ってください。

Amplitudeのユーザープロパティとコホートは、ユーザーセグメントを定義するのに使用できます。ここに含めることができるユーザーセグメントの数には制限はありません。

9. 次に、**この機能のロールアウトの割合**を設定します。これは、フラグのユーザーセグメントに含まれるユーザーの割合で、新しい機能が表示されます。プリセット値のいずれかを選択するか、または手動で希望の値を入力します。ユーザーセグメントの全員に機能にアクセスさせる場合は、この値を100%に設定します。
10. Amplitude Experimentに、各バリアントを何人のユーザーに表示するか伝える必要があります。**ウェイト**は相対値です：例えば、バリアントAに1のウェイト、バリアントBに4のウェイトを付与した場合、バリアントAよりもバリアントBを表示するユーザーの数が4倍多くなります。
11. ステップ7で作成したセグメントでカバーされていないすべてのユーザーに個別のルールを設定できます。例えば、先にターゲットした特定のコホートだけに機能をロールアウトする場合は、*[すべての非ターゲットユーザー]*セクションにスクロールして、ロールアウト割合をゼロに設定します。  
  
*[サマリー]*セクションでは、すべてのユーザーでバリアントの合計効果分布の推定値を確認することができます。
12. 次に、フラグを保存します。まだ保存していない場合は、アクティブに設定する前にQAを行ってください。詳細については、Amplitude ExpermientのQAのフラグに関する[ヘルプセンターの記事を参照してください](https://help.amplitude.com/hc/en-us/articles/360061687311)。
13. 準備ができたら、右上隅の*[非アクティブ]*トグルを*[アクティブ]*に切り替えます。これで、機能は選択したユーザーセグメントで動作します。