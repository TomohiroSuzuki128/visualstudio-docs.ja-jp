---
title: Visual Studio の検出 |Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7187fbcc3e3aca990846176676a47f5d17aaf00
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878144"
---
# <a name="locate-visual-studio"></a>Visual Studio を検索します。

Visual Studio 2017 以降では、同じバージョンまたはエディションでも複数のインスタンスをインストールできます。 これは、機能は、以前のインストールを維持しながら主要な開発コンピューターに新しい機能をプレビューする場合に便利です。 これらの変更により、インスタンスの検索に使用できる 1 つの環境変数またはレジストリ値はありません。 代わりに、使用、 [COM クエリ API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx)拡張機能に関連する条件に基づいてインスタンスを検索します。

これは、ネイティブおよびマネージ コードの使用可能な NuGet パッケージで高速の読み取り専用の API です。

| コード | パッケージ |
| ---- | --- |
| ネイティブ | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| マネージド | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

指定されたパスまたは現在のプロセスでは、1 つのインスタンスを検索したり、すべてのインスタンスを列挙できます。 参照してください[サンプル](https://github.com/Microsoft/vs-setup-samples)Visual Studio を検索する方法の完全な例です。

## <a name="tools"></a>ツール

ビルド環境、PowerShell スクリプト、インストーラー、およびより多くのシナリオで Visual Studio およびその他のツールを検索するには、さまざまなオープン ソース ツールを直接使用したり、独自のスクリプトと共に再配布があります。

| プロジェクト | 説明 |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | 1 つのファイルのネイティブ リリースなどの条件を満たすインスタンスを検索する実行可能ファイルまたはプレリリース版では、どのような製品がインストールされている、およびどのワークロードがインストールされています。 以下の情報が返さを Visual Studio 2017 以降、2010 以降、Visual Studio の検索もサポートします。 参照してください、 [wiki](https://github.com/Microsoft/vswhere/wiki)例についてはします。 |
| [VSSetup コマンドレット](https://github.com/Microsoft/vssetup.powershell) | サポートされている PowerShell コマンドレットと同じ条件に基づいてインスタンスを検索する際のオブジェクトとしての豊富な情報を返す 2.0 と新しい_vswhere_インスタンスに関するさらに多くのプロパティを検出するとします。 参照してください、 [wiki](https://github.com/Microsoft/vssetup.powershell/wiki)例についてはします。 |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | 自動的に検出_VSIXInstaller_しインストールをコマンドラインに渡します、**.vsix*ファイル。 この機能は、クエリ Api を直接サポートはありません。 インストーラーで役立ちます。 参照してください、 [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki)例についてはします。 |

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 セットアップの変更点](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [DTE を使用して Visual Studio を起動します。](launch-visual-studio-dte.md)