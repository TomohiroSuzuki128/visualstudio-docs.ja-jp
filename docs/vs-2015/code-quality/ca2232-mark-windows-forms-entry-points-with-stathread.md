---
title: 'CA2232: Windows フォームのエントリポイントを、すべてのスレッドでマークします。Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 084e7a093f92aa8eda9d9edc11865ac319adfad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662790"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows フォームのエントリ ポイントを STAThread に設定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|カテゴリ|Microsoft. 使用方法|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 アセンブリが <xref:System.Windows.Forms> 名前空間を参照し、そのエントリポイントが <xref:System.STAThreadAttribute?displayProperty=fullName> 属性でマークされていません。

## <a name="rule-description"></a>規則の説明
 <xref:System.STAThreadAttribute> は、アプリケーションの COM スレッドモデルがシングルスレッドアパートメントであることを示します。 この属性は、Windows フォームを使用するすべてのアプリケーションのエントリ ポイントに指定する必要があります。省略すると、Windows コンポーネントが正常に機能しないことがあります。 属性が存在しない場合、アプリケーションは、Windows フォームでサポートされていないマルチスレッドアパートメントモデルを使用します。

> [!NOTE]
> アプリケーションフレームワークを使用する [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] プロジェクトは、 **Main**メソッドをスレッドでマークする必要はありません。 @No__t_0 コンパイラは自動的にそれを行います。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、エントリポイントに <xref:System.STAThreadAttribute> 属性を追加します。 @No__t_0 属性が存在する場合は、削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 @No__t_0 属性が不要で、サポートされていない .NET Compact Framework を開発している場合は、この規則からの警告を抑制することが安全です。

## <a name="example"></a>例
 次の例は、<xref:System.STAThreadAttribute> の正しい使用方法を示しています。

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
