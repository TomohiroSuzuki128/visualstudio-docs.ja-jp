---
title: 'CA1035: ICollection の実装に厳密に型指定されたメンバー |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d112e2dfb704a785db6bbc5becd2b369d90605b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661847"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|カテゴリ|Microsoft Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型またはプロテクト型が <xref:System.Collections.ICollection?displayProperty=fullName> を実装していますが、厳密に型指定された <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> のメソッドを提供していません。 厳密に型指定された <xref:System.Collections.ICollection.CopyTo%2A> のバージョンでは、2つのパラメーターを受け取る必要があり、最初のパラメーターとして <xref:System.Array?displayProperty=fullName> または <xref:System.Object?displayProperty=fullName> の配列を持つことはできません。

## <a name="rule-description"></a>規則の説明
 この規則では、インターフェイスによって提供される機能を使用するときに、ユーザーが引数を <xref:System.Object> 型にキャストする必要がないように、厳密に型指定されたメンバーを提供する <xref:System.Collections.ICollection> 実装が必要です。 この規則では、<xref:System.Collections.ICollection> を実装する型が、<xref:System.Object> よりも強力な型のインスタンスのコレクションを管理するようにしていることを前提としています。

 <xref:System.Collections.ICollection> は、<xref:System.Collections.IEnumerable?displayProperty=fullName> インターフェイスを実装します。 コレクション内のオブジェクトが <xref:System.ValueType?displayProperty=fullName> を拡張する場合は、ボックス化によって発生するパフォーマンスの低下を回避するために、<xref:System.Collections.IEnumerable.GetEnumerator%2A> の厳密に型指定されたメンバーを指定する必要があります。 コレクションのオブジェクトが参照型である場合、これは必要ありません。

 インターフェイスメンバーの厳密に型指定されたバージョンを実装するには、`InterfaceName.InterfaceMemberName` 形式の名前 (<xref:System.Collections.ICollection.CopyTo%2A> など) を使用して、インターフェイスメンバーを明示的に実装します。 明示的なインターフェイスメンバーは、インターフェイスによって宣言されたデータ型を使用します。 @No__t_0 などのインターフェイスメンバー名を使用して、厳密に型指定されたメンバーを実装します。 厳密に型指定されたメンバーをパブリックとして宣言し、コレクションによって管理される厳密な型のパラメーターと戻り値を宣言します。 厳密な型は、インターフェイスによって宣言されている <xref:System.Object> や <xref:System.Array> などの弱い型を置き換えます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、インターフェイスメンバーを明示的に実装します (<xref:System.Collections.ICollection.CopyTo%2A> として宣言します)。 @No__t_0 として宣言された、厳密に型指定されたパブリックメンバーを追加し、最初のパラメーターとして厳密に型指定された配列を取得します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 バイナリツリーなどの新しいオブジェクトベースのコレクションを実装する場合、この規則からの警告を抑制します。新しいコレクションを拡張する型は、厳密な型を決定します。 これらの型は、この規則に準拠し、厳密に型指定されたメンバーを公開する必要があります。

## <a name="example"></a>例
 次の例は、<xref:System.Collections.ICollection> を実装する正しい方法を示しています。

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1038: 列挙子は厳密に型指定されていなければなりません](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: リストは厳密に型指定されています](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>参照
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
