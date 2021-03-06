---
title: ブレークポイントのヒット |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d95abd66f248ca994d7712f1bf51519022de9d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344042"
---
# <a name="hit-a-breakpoint"></a>ブレークポイントに到達する
次のセクションでは、デバッグ エンジン (DE) を実行している、またはステップ実行中にブレークポイントに達すると、プロセスが説明します。

## <a name="troubleshoot-a-hit-breakpoint"></a>ブレークポイントをヒットのトラブルシューティングします。

1. DE 送信、 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)インターフェイスとして、 **EVENT_SYNC_STOP**します。

2. セッション デバッグ マネージャー (SDM) を呼び出す[IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)ヒットしたブレークポイントを取得します。

## <a name="see-also"></a>関連項目
- [デバッガー イベントを呼び出す](../../extensibility/debugger/calling-debugger-events.md)