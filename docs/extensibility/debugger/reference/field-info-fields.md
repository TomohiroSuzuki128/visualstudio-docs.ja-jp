---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01853df78bfe731ea4b7159f7b3ebe352f3c5eaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337679"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
取得するには、どのような情報を指定します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)オブジェクト。

## <a name="syntax"></a>構文

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>フィールド
`FIF_FULLNAME`\
初期化/使用、`bstrFullName`フィールドに、 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)構造体。

`FIF_NAME`\
初期化/使用、`bstrName`フィールドに、`FIELD_INFO`構造体。

`FIF_TYPE`\
初期化/使用、`bstrType`フィールドに、`FIELD_INFO`構造体。

`FIF_MODIFIERS`\
初期化/使用、`bstrModifiers`フィールドに、`FIELD_INFO`構造体。

## <a name="remarks"></a>Remarks
これらの値がへの引数として渡されることも、 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)のどのフィールドを指定するメソッド、 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)構造体が初期化するには。

これらの値が使用されることも、`dwFields`のメンバー、`FIELD_INFO`フィールドが使用し、有効なときは、構造体。

これらのフラグは、演算と組み合わせることがあります`OR`します。

## <a name="requirements"></a>必要条件
ヘッダー: sh.h

名前空間: Microsoft.VisualStudio.Debugger.Interop

アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目
- [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
