---
title: コマンド ラインから CPU 使用率を測定する
description: アプリケーションの CPU パフォーマンスをコマンド ラインから測定します。
ms.custom: ''
ms.date: 02/19/2019
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 87bf0c236f34e753866ea114dfc7f45e8f16a979
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972420"
---
# <a name="measure-application-performance-from-the-command-line"></a>コマンド ラインからアプリケーションのパフォーマンスを測定する

コマンドライン ツールを使用して、アプリケーションに関するパフォーマンス情報を収集できます。

この記事に記載されている例では、Microsoft メモ帳のパフォーマンス情報を収集しますが、同じ方法を使用して任意のプロセスをプロファイルすることができます。

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio 2019 Preview 3 以降のバージョン

* コマンドライン ツールに関する知識

## <a name="collect-performance-data"></a>パフォーマンス データを収集する

Visual Studio Diagnostics CLI ツールを使用したプロファイリングは、プロファイリング ツールを 1 つのコレクター エージェントと共にプロセスにアタッチすることで機能します。 プロファイリング ツールをアタッチすると、ツールが停止するまでプロファイリング データをキャプチャして保存する診断セッションが開始されます。ツールが停止した時点で、そのデータは *.diagsession* ファイルにエクスポートされます。 このファイルは、Visual Studio で開いて結果を分析できます。

1. メモ帳を起動し、タスク マネージャーを開いてプロセス ID (PID) を取得します。 タスク マネージャーの **[詳細]** タブで PID を見つけます。

1. コマンド プロンプトを開き、実行可能な収集エージェントがあるディレクトリ (通常は次のディレクトリ) に移動します。

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. 次のコマンドを入力して *VSDiagnostics.exe* を起動します。

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   含める必要がある引数は次のとおりです。

   * \<*id*>。収集セッションを識別します。 ID は常に 1 - 255 の数字です。
   * \<*pid*>。プロファイルするプロセスの PID。この場合は手順 1 で見つけた PID です。
   * \<*configFile*>。起動する収集エージェントの構成ファイル。 詳細については、[エージェントの構成ファイル](#config_file)に関するセクションを参照してください。

1. メモ帳のサイズを変更するか、興味深い何らかの入力プロファイリング情報が確実に収集されるようにメモ帳に何かを入力します。

1. 次のコマンドを入力して、収集セッションを停止し、ファイルに出力を送信します。

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. 前のコマンドから出力されたファイルに移動し、Visual Studio でそれを開いて、収集された情報を調べます。

## <a name="config_file"></a> エージェントの構成ファイル

収集エージェントは、測定対象が何かに応じて、さまざまな種類のデータを収集する交換可能なコンポーネントです。

便宜上、その情報をエージェント構成ファイルに保管することができます。 構成ファイルは、少なくとも *.dll* の名前とその COM CLSID を含む *.json* ファイルです。 以下は、次のフォルダー内にある構成ファイルの例です。

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* CpuUsage 構成 (Base/High/Low)。[CPU 使用率](../profiling/cpu-usage.md)プロファイリング ツールについて収集されたデータに対応します。
* DotNetObjectAlloc 構成 (Base/Low)。[.NET オブジェクト割り当てツール](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-version-15-8-preview-3/#tooling)について収集されたデータに対応します。

Base/Low/High 構成はサンプリング レートを表します。 たとえば、Low は 100 サンプル/秒、High は 4,000 サンプル/秒です。

*VSDiagnostics.exe* ツールを収集エージェントと連携させるには、適切なエージェントの DLL と COM CLSID の両方が必要です。また、エージェントに追加の構成オプションが存在する場合があります。 構成ファイルなしでエージェントを使用する場合は、次のコマンドでこの形式を使用してください。

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>アクセス許可

昇格されたアクセス許可が必要なアプリケーションをプロファイルするには、昇格されたコマンド プロンプトから実行する必要があります。
