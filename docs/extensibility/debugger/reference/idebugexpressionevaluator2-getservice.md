---
title: IDebugExpressionEvaluator2::GetService |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42a4027b4153f262eb8164a915f229f04c7cbed4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325563"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
その一意識別子を指定したサービス オブジェクトを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>パラメーター
`uid`\
[in]取得するサービスの一意の識別子。

`ppService`\
[out]サービスを表すオブジェクトを返します。

## <a name="return-value"></a>戻り値
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。

## <a name="remarks"></a>Remarks
 これは、別の式エバリュエーターからサービスを取得するサード パーティ製の式エバリュエーターで使用できます。 たとえば、このメソッドは、既定の式エバリュエーターからビジュアライザー サービスのインターフェイスを取得する使用でした。 サード パーティ製の式エバリュエーターされない可能性があるこのインターフェイスを実装する必要があります。

## <a name="see-also"></a>関連項目
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)