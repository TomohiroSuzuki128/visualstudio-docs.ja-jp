﻿---
title: コードからの依存関係図の作成
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51e33d5f9b20230b056c017c9067bb4b2acafce6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597192"
---
# <a name="create-dependency-diagrams-from-your-code"></a>コードからの依存関係図の作成

ソフトウェア システムの高レベルの論理アーキテクチャを視覚化するには、Visual Studio で*依存関係図*を作成します。 コードがこの設計と一致していることを確認するために、依存関係図を使用してコードを検証します。 Visual C＃ および Visual Basic プロジェクトの依存関係図を作成することができます。 Visual C＃ および Visual Basic プロジェクトの依存関係図を作成することができます[アーキテクチャおよびモデリングツールのエディションサポート](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools) を参照してください。

![依存関係図の作成](../modeling/media/layerdiagramvisualizecode.png)

依存関係図を使用すると、Visual Studio ソリューションの項目を、*レイヤー*と呼ばれる論理的な抽象グループにまとめることができます。 レイヤーを使用して、これらの成果物が実行する主要タスク、またはシステムの主要コンポーネントを示すことができます。 各レイヤーには、より詳細なタスクを示す別のレイヤーを含めることができます。 また、レイヤー間の目的または既存の*依存関係*を指定することもできます。 矢印で表されるこれらの依存関係は、どのレイヤーが、他のレイヤーが表す機能を使用できるか、または現在使用しているかを示します。 コードのアーキテクチャ コントロールを保持するには、目的の依存関係を図で示し、図と照らし合わせてコードを検証します。

[ビデオ: アーキテクチャの依存関係をリアルタイムで検証する](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="CreateDiagram"></a>依存関係図の作成

依存関係図を作成する前に、ソリューションにモデリングプロジェクトがあることを確認してください。

> [!IMPORTANT]
> 既存の依存関係図をモデリングプロジェクトから別のモデリングプロジェクトまたはソリューション内の別の場所に追加、ドラッグ、またはコピーしないでください。 これで、図を変更しても、元の図からの参照が保持されます。 また、これによってレイヤー検証が正しく機能しないため、要素が欠落したり、図を開こうとすると他のエラーが発生するなど、別の問題が生じる可能性があります。
>
> 代わりに、新しい依存関係図をモデリングプロジェクトに追加します。 元の図から新しい図へ要素をコピーします。 モデリングプロジェクトと新しい依存関係図の両方を保存します。

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>新しい依存関係図をモデリングプロジェクトに追加する

> [!NOTE]
> .NET Core プロジェクトの依存関係図は、Visual Studio 2019 バージョン16.2 以降でサポートされています。

1. **[アーキテクチャ]** メニューの **[新しい依存関係ダイアグラム]** をクリックします。

2. **[テンプレート]** で **[依存関係図]** を選択します。

3. 図に名前を付けます。

4. **[モデリングプロジェクトへの追加]** で、ソリューション内の既存のモデリングプロジェクトを参照して選択します。

     -または-

     新しいモデリングプロジェクトをソリューションに追加するには、 **[新しいモデリングプロジェクトの作成]** を選択します。

    > [!NOTE]
    > 依存関係図はモデリングプロジェクト内に存在する必要があります。 ただし、ソリューション内のどの場所にある項目にもリンクできます。

5. モデリングプロジェクトと依存関係図の両方を必ず保存してください。

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>コードマップからのドラッグアンドドロップ (コピーと貼り付け)

1. **[アーキテクチャ]** メニューを使用して、ソリューションのコードマップを生成します。

2. 製品コードに依存関係を適用するだけの場合は、ソリューションフォルダーと "テストアセット" を削除するコードマップフィルターを適用することを検討してください。

3. 生成されたコードマップで、"外部" ノードを削除するか、名前空間の依存関係を適用するかどうかに応じて、外部アセンブリを表示するように展開します。また、コードマップから不要なアセンブリを削除します。

4. **[アーキテクチャ]** メニューを使用して、ソリューションの新しい依存関係図を作成します。

5. コード マップ上のすべてのノードを選択します （_Ctrl_ + _A_を使用するか、_Shift_キーを押してクリック、ドラッグ、リリースする前にラバーバンドを選択します）。

6. 選択した要素を新しい依存関係検証ダイアグラムにドラッグアンドドロップするか、コピーして貼り付けます。

7. これは、現在のアプリのアーキテクチャを示しています。 アーキテクチャの目的を決定し、それに応じて依存関係図を変更します。

![コードマップから生成された依存関係図](media/dependency-validation-01.png)

## <a name="CreateLayers"></a>成果物からレイヤーを作成する
 レイヤーは、プロジェクト、コード ファイル、名前空間、クラス、メソッドなど、Visual Studio ソリューションの項目から生成できます。 これにより、レイヤーと項目の間のリンクが自動的に作成され、レイヤー検証プロセスに含まれます。

 Word 文書や PowerPoint プレゼンテーションなどの検証をサポートしない項目にレイヤーをリンクすることもできます。こうすると、仕様や計画にレイヤーを関連付けることができます。 複数のアプリが共有するプロジェクトのファイルにレイヤーをリンクすることもできます。ただし、これらのレイヤーは検証プロセスには含まれず、"レイヤー 1"、"レイヤー 2" などの汎用名で表示されます。

 リンクされた項目が検証をサポートしているかどうかを確認するには、**レイヤーエクスプローラー**を開き、項目の "**検証をサポート**" プロパティを確認します。 「[成果物へのリンクの管理」を](#Managing)参照してください。

|**目的**|**次の手順に従います。**|
|-|-|
|1 つの成果物を表すレイヤーを生成する|<ol><li>次のソースから依存関係図に項目をドラッグします。<br /><br /> <ul><li>**ソリューション エクスプローラー**<br /><br />         ファイルやプロジェクトなどをドラッグできます。</li><li>コード マップ<br /><br />         「[ソリューション間の依存関係をマップ](../modeling/map-dependencies-across-your-solutions.md)する」および「[コードマップを使用してアプリケーションをデバッグする」を](../modeling/use-code-maps-to-debug-your-applications.md)参照してください。</li><li>**クラスビュー**または**オブジェクトブラウザー**</li></ul><br />     レイヤーが図に表示され、成果物にリンクされます。</li><li>レイヤーの名前を、関連するコードや成果物の役割を表す名前に変更します。</li></ol> **重要:** バイナリファイルを依存関係図にドラッグしても、モデリングプロジェクトへの参照は自動的には追加されません。 検証するバイナリ ファイルを手動でモデリング プロジェクトに追加する必要があります。 **モデリングプロジェクトにバイナリファイルを追加するには** <ol><li>**ソリューションエクスプローラー**で、モデリングプロジェクトのショートカットメニューを開き、 **[既存項目の追加]** を選択します。</li><li>**[既存項目の追加]** ダイアログボックスで、バイナリファイルを参照して選択し、[ **OK]** をクリックします。     バイナリ ファイルがモデリング プロジェクトに表示されます。</li><li>**ソリューションエクスプローラー**で、追加したバイナリファイルを選択し、 **F4**キーを押して **[プロパティ]** ウィンドウを開きます。</li><li>各バイナリファイルで、 **[ビルドアクション]** プロパティを **[検証]** に設定します。</li></ol>|
|選択したすべての成果物を表す 1 つのレイヤーを生成する|すべての成果物を同時に依存関係図にドラッグします。<br /><br /> レイヤーが図に表示され、すべての成果物にリンクされます。|
|選択した各成果物を表すレイヤーを生成する|**Shift**キーを押しながら、すべてのアイテムを依存関係図に同時にドラッグします。 **注:** **SHIFT**キーを使用して項目の範囲を選択する場合は、成果物を選択した後でキーを離します。 成果物を図にドラッグするときは、キーを再び押して、押したままにします。 <br /><br /> 各成果物を表すレイヤーが図に表示され、各成果物にリンクされます。|
|成果物をレイヤーに追加する|成果物をレイヤーにドラッグします。|
|リンクされない新しいレイヤーを生成する|**ツールボックス**で、 **[依存関係ダイアグラム]** セクションを展開し、**レイヤー**を依存関係図にドラッグします。<br /><br /> 複数のレイヤーを追加するには、ツールをダブルクリックします。 操作が完了したら、 **[ポインター]** ツールを選択するか、 **ESC**キーを押します。<br /><br /> または<br /><br /> 依存関係図のショートカットメニューを開き、 **[追加]** を選択し、 **[レイヤー]** を選択します。|
|入れ子になったレイヤーを生成する|既存のレイヤーを別のレイヤー上へドラッグします。<br /><br /> または<br /><br /> レイヤーのショートカットメニューを開き、 **[追加]** 、 **[レイヤー]** の順に選択します。|
|複数の既存レイヤーを含む新しいレイヤーを生成する|レイヤーを選択し、選択したショートカットメニューを開き、 **[グループ]** を選択します。|
|レイヤーの色を変更する|その**color**プロパティを目的の色に設定します。|
|レイヤーに関連付けられている成果物を、指定した名前空間に所属させることができないように指定する|レイヤーの "禁止された**名前空間**" プロパティに名前空間を入力します。 名前空間を区切るには、セミコロン ( **;** ) を使用します。|
|レイヤーに関連付けられている成果物が、指定した名前空間に依存できないように指定する|レイヤーの "禁止された**名前空間の依存関係**" プロパティに名前空間を入力します。 名前空間を区切るには、セミコロン ( **;** ) を使用します。|
|レイヤーに関連付けられている成果物を、指定した名前空間のいずれかに必ず所属させるように指定する|レイヤーの "**必要な名前空間**" プロパティに名前空間を入力します。 名前空間を区切るには、セミコロン ( **;** ) を使用します。|

 レイヤーの数字は、レイヤーにリンクされている成果物の数を示します。 ただし、この数値を読み取るときには、次の点に注意してください。

- 1 つのレイヤーが他の成果物を含む 1 つの成果物にリンクされているが、他の成果物に直接リンクされていない場合、その数字にはリンクされた成果物のみが含まれます。 ただし、レイヤー検証時の分析にはそれらの他の成果物も含まれます。

     たとえば、1 つのレイヤーが 1 つの名前空間にリンクされている場合、その名前空間に複数のクラスが含まれていても、リンクされた成果物の数は 1 です。 レイヤーに名前空間の各クラスへのリンクもある場合、その数字にはリンクされたクラスが含まれます。

- 1 つのレイヤーに成果物にリンクされた他のレイヤーが含まれている場合は、そのコンテナー レイヤーの数字にそれらの成果物が含まれていなくても、コンテナー レイヤーはそれらの成果物にリンクされます。

## <a name="Managing"></a>レイヤーと成果物の間のリンクの管理

1. 依存関係図で、レイヤーのショートカットメニューを開き、[リンクの**表示**] を選択します。

     **レイヤーエクスプローラー**には、選択したレイヤーの成果物のリンクが表示されます。

2. これらのリンクを管理するには、次の操作を行います。

|**目的**|**レイヤーエクスプローラーで**|
|-|-|
|レイヤーと成果物のリンクを削除する|成果物のリンクのショートカットメニューを開き、 **[削除]** を選択します。|
|リンクを別のレイヤーに移動する|成果物のリンクを図上の既存のレイヤーにドラッグします。<br /><br /> または<br /><br /> 1. 成果物のリンクのショートカットメニューを開き、 **[切り取り]** を選択します。<br />2. 依存関係図で、レイヤーのショートカットメニューを開き、 **[貼り付け]** を選択します。|
|リンクを別のレイヤーにコピーする|1. 成果物のリンクのショートカットメニューを開き、 **[コピー]** をクリックします。<br />2. 依存関係図で、レイヤーのショートカットメニューを開き、 **[貼り付け]** を選択します。|
|既存の成果物のリンクから新しいレイヤーを生成する|成果物のリンクを図上の空白領域にドラッグします。|
|リンクされた成果物が依存関係図に対する検証をサポートしていることを確認します。|成果物のリンクについては、**検証をサポート**する列を参照してください。|

## <a name="Discovering"></a>既存の依存関係をリバースエンジニアリングする
 依存関係が存在するのは、あるレイヤーに関連付けられている成果物が、別のレイヤーに関連付けられている成果物を参照している場合です。 たとえば、あるレイヤー内のクラスが、別のレイヤー内のクラスを保持する変数を宣言する場合などです。 図のレイヤーにリンクされている成果物の既存の依存関係はリバース エンジニアリングできます。

> [!NOTE]
> 成果物の種類によっては、依存関係をリバース エンジニアリングできないものもあります。 たとえば、テキスト ファイルにリンクされているレイヤーから、またはそのレイヤーに対して依存関係をリバース エンジニアリングすることはできません。 リバースエンジニアリングできる依存関係がある成果物を確認するには、1つまたは複数のレイヤーのショートカットメニューを開き、 **[リンクの表示]** をクリックします。 **レイヤーエクスプローラー**で、 **[検証をサポート]** 列を確認します。 この列に**False**と表示される成果物の依存関係はリバースエンジニアリングされません。

- 1つまたは複数のレイヤーを選択し、選択したレイヤーのショートカットメニューを開き、 **[依存関係の生成]** を選択します。

  通常は、不要な依存関係がいくつか見つかります。 これらの依存関係を編集して、目的の設計に準拠するようアラインできます。

## <a name="EditDependencies"></a>レイヤーと依存関係を編集して目的のデザインを表示する
 システムまたは目的のアーキテクチャに対して行う変更を記述するには、次のように依存関係図を編集します。

|**目的**|**次の手順を実行します。**|
|-|-|
|依存関係の方向を変更または制限する|**Direction**プロパティを設定します。|
|新しい依存関係を生成する|**依存**関係ツールと**双方向の依存関係**ツールを使用します。<br /><br /> 複数の依存関係を描画するには、ツールをダブルクリックします。 操作が完了したら、 **[ポインター]** ツールを選択するか、 **ESC**キーを押します。|
|レイヤーに関連付けられている成果物が、指定した名前空間に依存できないように指定する|レイヤーの "禁止された**名前空間の依存関係**" プロパティに名前空間を入力します。 名前空間を区切るには、セミコロン ( **;** ) を使用します。|
|レイヤーに関連付けられている成果物を、指定した名前空間に所属させることができないように指定する|レイヤーの "禁止された**名前空間**" プロパティに名前空間を入力します。 名前空間を区切るには、セミコロン ( **;** ) を使用します。|
|レイヤーに関連付けられている成果物を、指定した名前空間のいずれかに必ず所属させるように指定する|レイヤーの "**必要な名前空間**" プロパティに名前空間を入力します。 名前空間を区切るには、セミコロン ( **;** ) を使用します。|

## <a name="EditLayout"></a>図に要素を表示する方法を変更する
 プロパティを編集して、レイヤーのサイズ、形状、色、位置、または依存関係の色を変更できます。

## <a name="Codemaps"></a>コードマップのパターンと依存関係を検出する
 依存関係図を作成するときに、**コードマップ**を作成することもできます。 これらの図を利用することで、コードを検証するときに、パターンと依存関係を見つけやすくなります。 ソリューション エクスプローラー、クラス ビュー、またはオブジェクト ブラウザーを使用して、アセンブリ、名前空間、およびクラスを調べることができます。これらは、通常は既存のレイヤーに対応しています。 コード マップについての詳細は、次を参照してください。

- [ソリューション間の依存関係をマップする](../modeling/map-dependencies-across-your-solutions.md)

- [コード マップを使用してアプリケーションをデバッグする](../modeling/use-code-maps-to-debug-your-applications.md)

- [コード マップ アナライザーを使用して潜在的な問題を検索する](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>関連項目

- [アーキテクチャおよびモデリングツールのエディションサポート](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [ビデオ: アーキテクチャの依存関係をリアルタイムで検証する](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)
- [依存関係図: ガイドライン](../modeling/layer-diagrams-guidelines.md)
- [依存関係図を使用したコードの検証](../modeling/validate-code-with-layer-diagrams.md)
- [コードの視覚化](../modeling/visualize-code.md)
