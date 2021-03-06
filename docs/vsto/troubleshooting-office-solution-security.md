---
title: Office ソリューションのセキュリティに関するトラブルシューティング
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 289ffc3b5260260c9da8d0ec61e5c79890394802
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985560"
---
# <a name="troubleshoot-office-solution-security"></a>Office ソリューションのセキュリティに関するトラブルシューティング
  このトピックでは、Office ソリューションをセキュリティで保護する際に発生する可能性のある一般的な問題を解決するためのヒントを示します。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>信頼済みソリューションを制限付きサイトからインストールできない
 Web サイトが Internet Explorer の制限付きサイトゾーンに一覧表示されている場合、ユーザーは web サイトからソリューションをインストールできません。 これは、ソリューションが信頼された証明書で署名されている場合でも当てはまります。

 デプロイマニフェストの URL は、5つのゾーンのいずれかに分類できます。

- マイ コンピューター

- インターネット

- ローカルイントラネット

- 信頼済みサイト

- 制限付きサイト

  配置マニフェストの場所が制限付きサイトゾーンに割り当てられている場合、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によってソリューションがインストールされません。 場所が既知で信頼できる場合、ユーザーは、制限付きサイトゾーンから場所を削除して、ソリューションをインストールできます。 ゾーンの管理方法の詳細については、「 [ClickOnce 信頼された発行元の構成](/previous-versions/dotnet/articles/ms996418(v=msdn.10))」を参照してください。

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer セキュリティ強化の構成または Internet Explorer 7 がインストールされている場合、ネットワークファイル共有または web サイトからソリューションをインストールすることはできません。
 Windows Server 2003 以降の internet Explorer セキュリティ強化の構成 (IEESC)、および Internet Explorer 7 以降では、ユーザーがインターネットを参照する機能が大幅に制限されています。 ユーザーがネットワークファイル共有または web サイトから Office ソリューションをインストールしようとすると、次のエラーメッセージが表示されることがあります。 "このアプリケーションでのカスタマイズされた機能は、の*配置マニフェストの署名に使用される証明書のために機能しません。SolutionName*は信頼されていません。 詳細については、管理者にお問い合わせください。 "

 IEESC と Internet Explorer 7 以降では、配置マニフェストの URL がインターネットゾーンに分類されている場合、マニフェストに信頼された発行元の証明書が含まれている必要があります。または、ソリューションをインストールできません。 IEESC を使用しない場合、既定の動作では、エンドユーザーに対して信頼の決定を求めるメッセージが表示されます。

 IEESC と Internet Explorer 7 以上の効果を管理するには、信頼できる web サイトおよび汎用名前付け規則 (UNC) パスを特定し、信頼できるセキュリティゾーン (ローカルイントラネットまたは信頼済みサイト) のいずれかに追加します。ゾーンの管理方法の詳細については、「 [Configure ClickOnce trusted publishers](/previous-versions/dotnet/articles/ms996418(v=msdn.10))」を参照してください。

## <a name="see-also"></a>関連項目
- [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)
