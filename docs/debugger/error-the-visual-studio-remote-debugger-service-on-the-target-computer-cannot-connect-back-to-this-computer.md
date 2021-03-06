---
title: 'エラー: ターゲット コンピューター上の Visual Studio リモート デバッガーが、このコンピューターに接続できません'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 695c4c9e84ce9eb851a551dc9821bff00123a35c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737402"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>エラー: ターゲット コンピューター上の Visual Studio リモート デバッガーが、このコンピューターに接続できません
このエラーは、リモートデバッガーサービスが、デバッグ元のコンピューターに接続しようとしたときに認証できないユーザーアカウントで実行されていることを意味します。 このエラーは、レガシデバッグエンジンを使用したリモートデバッグで、リモートデバッガーがサービスとして実行されている場合に発生する可能性があります。

 コンピューターにアクセスできるアカウントは、次の表のとおりです。

|||||
|-|-|-|-|
||LocalSystem アカウント|ドメイン アカウント|両方のコンピューターに同じユーザー名とパスワードを持つローカル アカウント|
|両方のコンピューターが同じドメインにある場合|[はい]|[はい]|[はい]|
|両方のコンピューターが双方向の信頼関係を持つドメインにある場合|Ｘ|Ｘ|[はい]|
|一方または両方のコンピューターがワークグループにある場合|Ｘ|Ｘ|[はい]|
|コンピューターが異なるドメインにある場合|Ｘ|Ｘ|[はい]|

 さらに:

- Visual Studio リモート デバッガー サービスを実行するアカウントは、すべてのプロセスをデバッグできるように、リモート コンピューターの管理者アカウントであることが必要です。

- このアカウントには、**ローカル セキュリティ ポリシー**管理ツールを使用して、リモート コンピューターに対する `Log on as a service` 特権が与えられている必要もあります。

- ローカル アカウントを使用してコンピューターにアクセスしている場合は、ローカル アカウントで Visual Studio リモート デバッガー サービスを実行する必要があります。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. リモート コンピューターに Visual Studio リモート デバッガー サービスが正しく設定されていることを確認します。 詳細については、「[リモートデバッグ](../debugger/remote-debugging.md)」を参照してください。

2. 上の表に示した、デバッガー ホスト コンピューターにアクセスできる適切なアカウントを使用して、リモート デバッガー サービスを実行します。

### <a name="to-add-log-on-as-a-service-privilege"></a>"サービスとしてログオンする" 特権を追加するには

1. **[スタート]** メニューの **[コントロール パネル]** を選択します。

2. 必要に応じて、[コントロール パネル] で **[クラシック表示]** を選択します。

3. **[管理ツール]** をダブルクリックします。

4. [管理ツール] ウィンドウで、 **[ローカル セキュリティ ポリシー]** をダブルクリックします。

5. **[ローカル セキュリティ設定]** ウィンドウで、 **[ローカル ポリシー]** フォルダーを展開します。

6. **[ユーザー権利の割り当て]** をクリックします。

7. **[ポリシー]** 列の **[サービスとしてログオン]** をダブルクリックすると、現在のローカル グループ ポリシーの割り当てが **[サービスとしてログオン]** ダイアログ ボックスに表示されます。

8. 新しいユーザーを追加するには、 **[ユーザーまたはグループの追加]** をクリックします。

9. ユーザーの追加作業が終了したら、 **[OK]** をクリックします。

### <a name="to-work-around-this-error"></a>このエラーを回避するには

- リモート デバッグ モニターをサービスとして実行する代わりに、アプリケーションとして実行します。

## <a name="see-also"></a>関連項目
- [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)