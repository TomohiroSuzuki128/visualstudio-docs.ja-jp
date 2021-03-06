---
title: IDebugEngineLaunch2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b6f59c9444b0c54f8a230f8eb4487e16b65ebf4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345223"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
起動し、プログラムを終了するデバッグ エンジン (DE) で使用します。

## <a name="syntax"></a>構文

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>実装についてのメモ
 このインターフェイスは、カスタム ポートで完全処理できません。 プロセスを起動するための特別な要件がある場合、カスタム DE によって実装されます。 これは通常、ケース、DE、インタープリターの一部であるし、デバッグ中のプロセスがスクリプト: インタープリターが最初に、起動する必要があると、スクリプトが読み込まれ、起動します。 ポートは、インタープリターを起動できますが、スクリプトは特別な処理 (つまり、DE がロールを持つ) 必要があります。 カスタム ポートを処理できないプログラムを起動するための一意の要件がある場合にのみ、このインターフェイスが実装されます。

## <a name="notes-for-callers"></a>呼び出し元のノート
 このインターフェイスを呼び出してセッション デバッグ マネージャー (SDM)、SDM は、このインターフェイスを取得できる場合から、 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)インターフェイス (QueryInterface を使用)。 このインターフェイスを取得できる場合、DE が特別な要件し、起動、ポートではなくプログラムを起動するには、このインターフェイスを呼び出す、SDM を認識します。

## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド
 次の表は、メソッドの`IDebugEngineLaunch2`します。

|メソッド|説明|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|デを使用して、プロセスを起動します。|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|再開では、実行を処理します。|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|プロセスが終了するかどうかを決定します。|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|プロセスを終了します。|

## <a name="requirements"></a>必要条件
 ヘッダー:Msdbg.h

 名前空間: Microsoft.VisualStudio.Debugger.Interop

 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)