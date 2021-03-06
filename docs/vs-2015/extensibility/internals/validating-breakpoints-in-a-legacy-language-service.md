---
title: 従来の言語サービスでのブレークポイントの検証 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f54dc683aa4287145a27e22d49397241b395f69f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163679"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>従来の言語サービスでのブレークポイントの検証
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ブレークポイントは、デバッガーで実行されている間に特定の時点でプログラムの実行を停止することを示します。 ユーザーは、エディターには、ブレークポイントの有効な場所の構成要素の知識があるないため、ソース ファイルの任意の行にブレークポイントを配置できます。 デバッガーが起動されのすべてのマークされたブレークポイント (保留中のブレークポイントと呼ばれます) は実行中のプログラムで適切な場所にバインドされます。 ブレークポイントが検証されていることを確認すると同時に有効なコードの場所をマークします。 などのソース コード内の場所にコードがないため、コメントのブレークポイントが有効でありません。 デバッガーは、無効なブレークポイントを無効にします。  
  
 言語サービスが表示されているソース コードを認識しているために、デバッガーが起動される前に、ブレークポイントを検証できます。 オーバーライドすることができます、<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>ブレークポイントの有効な場所を指定する範囲を返します。 デバッガーが起動されが、デバッガーを読み込むを待たず、ユーザーに通知が無効なブレークポイントとブレークポイントの位置はまだ検証されます。  
  
## <a name="implementing-support-for-validating-breakpoints"></a>ブレークポイントを検証するためのサポートの実装  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>メソッドには、ブレークポイントの位置が与えられます。 実装には、場所が有効期限、およびコードを特定するテキスト範囲を返すことによってこれに関連付けられている行位置ブレークポイントを示すかどうかを決める必要があります。  
  
- 返す<xref:Microsoft.VisualStudio.VSConstants.S_OK>の場所が、有効な場合または<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>が有効でない場合。  
  
- ブレークポイントが有効な場合は、ブレークポイントと共に、テキスト範囲が強調表示されます。  
  
- ブレークポイントが有効でない場合は、ステータス バーに、エラー メッセージが表示されます。  
  
### <a name="example"></a>例  
 この例の実装を示しています、<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>を指定した場所 (ある場合)、コードの範囲を取得するためにパーサーを呼び出すメソッド。  
  
 この例では、追加した、`GetCodeSpan`メソッドを<xref:Microsoft.VisualStudio.Package.AuthoringSink>テキスト範囲を返しますを検証するクラスを`true`ブレークポイントが有効な場所である場合。  
  
```csharp  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの特徴](../../extensibility/internals/legacy-language-service-features1.md)
