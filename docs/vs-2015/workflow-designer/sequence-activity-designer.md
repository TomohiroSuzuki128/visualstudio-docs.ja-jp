---
title: Sequence アクティビティデザイナー |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3acf02ab478eee244557e04f19f78ba2d5f0b950
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663259"
---
# <a name="sequence-activity-designer"></a>Sequence アクティビティ デザイナー
<xref:System.Activities.Statements.Sequence> アクティビティには、子アクティビティの順序付きコレクションが含まれており、これらのコレクションが順番に実行されます。

 他の方法でアクティビティのセットを順番に実行するには、<xref:System.Activities.Statements.Flowchart> アクティビティを使用します。 フローチャートを作成する単純な分岐またはループプログラムフローがある場合は、[フローチャート](../workflow-designer/flowchart-activity-designer.md)の使用を検討してください。

## <a name="using-the-sequence-activity-designer"></a>Sequence アクティビティ デザイナーの使用
 @No__t_0 アクティビティを追加するには、 **[ツールボックス]** から**Sequence**アクティビティデザイナーをドラッグし、[!INCLUDE[wfd1](../includes/wfd1-md.md)] 画面にドロップします。 この <xref:System.Activities.Statements.Sequence> アクティビティに子アクティビティを追加するには、**ツールボックス** から他のアクティビティをドラッグし、ここにアクティビティをドロップします というヒントテキストが表示されているボックス内の三角形にドロップします。

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの Sequence アクティビティのプロパティ
 次の表に、<xref:System.Activities.Statements.Sequence> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。

|プロパティ名|必要|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.Sequence> アクティビティ デザイナーの表示名を指定します。 既定値は Sequence です。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|

## <a name="see-also"></a>参照
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)の[制御フロー](../workflow-designer/control-flow-activity-designers.md)