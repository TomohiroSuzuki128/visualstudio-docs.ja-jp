---
title: IDebugProgram2::EnumModules |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bcc4beb077683cddfe3df14f147c3cc90b4111b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353130"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
このプログラムが読み込まれてが実行されているモジュールの一覧を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>パラメーター
`ppEnum`\
[out]返します、 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)モジュールの一覧を格納しているオブジェクト。

## <a name="return-value"></a>戻り値
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。

## <a name="remarks"></a>Remarks
 モジュールは DLL またはアセンブリには、通常記載、**モジュール**デバッグ ウィンドウ。

## <a name="see-also"></a>関連項目
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)