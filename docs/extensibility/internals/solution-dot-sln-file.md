---
title: ソリューション (します。Sln) ファイル
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b0e0b09b12dca964958d5d7b35c6b0d83906fa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322606"
---
# <a name="solution-sln-file"></a>ソリューション (.sln) ファイル

ソリューションは、Visual Studio でプロジェクトを整理するための構造です。 ソリューションには、2 つのファイル内のプロジェクトの状態情報が保持しています。

- .sln ファイル (テキスト ベースの共有)

- .suo ファイル (バイナリ、ユーザー固有のソリューションのオプション)

.Suo ファイルの詳細については、次を参照してください。[ソリューション ユーザー オプション (します。Suo) ファイル](../../extensibility/internals/solution-user-options-dot-suo-file.md)します。

.Sln ファイルで参照されている結果として、VSPackage が読み込まれる場合、環境を呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>.sln ファイルを読み取るようにします。

.Sln ファイルには、環境を検索して読み込む永続化されたデータおよびプロジェクトを参照して Vspackage の名前と値のパラメーターを使用して、テキスト ベースの情報が含まれています。 ユーザーがソリューションを開いたときは、環境が繰り返し、 `preSolution`、 `Project`、および`postSolution`については、ソリューションを読み込むには .sln ファイルでは、ソリューション内でプロジェクトし、ソリューションに接続されているすべての永続化された情報。

各プロジェクトのファイルには、そのプロジェクトの項目を含む階層を設定する環境で読み取られた追加の情報が含まれています。 階層データの永続化は、プロジェクトによって制御されます。 データは通常格納されません、.sln ファイルで記述できますが意図的にプロジェクト情報 .sln ファイルをそのためには選択した場合。 永続化の詳細については、次を参照してください。[プロジェクトの永続化](../../extensibility/internals/project-persistence.md)と[とプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)します。

## <a name="file-header"></a>ファイルのヘッダー

.Sln ファイルのヘッダーはようになります。

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>定義

`Microsoft Visual Studio Solution File, Format Version 12.00`\
ファイル形式のバージョンを定義する標準のヘッダー。

`# Visual Studio 15`\
このソリューション ファイルを保存 (最新) Visual Studio のメジャー バージョン。 この情報は、ソリューション アイコンのバージョン番号を制御します。

`VisualStudioVersion = 15.0.26730.15`\
Visual Studio ソリューション ファイルを保存 (最新) の完全なバージョン。 ソリューション ファイルは、同じメジャー バージョンが Visual Studio の新しいバージョンで保存する場合、ソリューション ファイル内の大きな変化を軽減するためにこの値は更新されません。

`MinimumVisualStudioVersion = 10.0.40219.1`\
このソリューション ファイルを開くことができる Visual Studio の最小の (最も古い) バージョン。

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>定義

`Microsoft Visual Studio Solution File, Format Version 12.00`\
ファイル形式のバージョンを定義する標準のヘッダー。

`# Visual Studio Version 16`\
このソリューション ファイルを保存 (最新) Visual Studio のメジャー バージョン。 この情報は、ソリューション アイコンのバージョン番号を制御します。

`VisualStudioVersion = 16.0.28701.123`\
Visual Studio ソリューション ファイルを保存 (最新) の完全なバージョン。 ソリューション ファイルは、同じメジャー バージョンが Visual Studio の新しいバージョンで保存する場合、ファイル内の大きな変化を軽減するためにこの値は更新されません。

`MinimumVisualStudioVersion = 10.0.40219.1`\
このソリューション ファイルを開くことができる Visual Studio の最小の (最も古い) バージョン。

::: moniker-end

## <a name="file-body"></a>ファイルの本文

いくつかのセクションではラベル付けの .sln ファイルの本文で構成されます`GlobalSection`、次のようにします。

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

ソリューションを読み込むには、環境は、次の一連のタスクを実行します。

1. 環境の .sln ファイルのグローバル セクションの読み取りし、マークされているすべてのセクションを処理`preSolution`します。 このファイルの例では、このような 1 つのステートメントです。

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   環境を読み取るとき、`GlobalSection('name')`タグ、レジストリを使用して VSPackage に名をマップにします。 キー名は、下のレジストリに存在する必要があります [HKLM\\< アプリケーション ID のレジストリ ルート\>\SolutionPersistence\AggregateGUIDs]。 キーの既定値は、エントリを記述した VSPackage のパッケージ GUID (REG_SZ) です。

2. 環境に呼び出し、VSPackage が読み込まれる`QueryInterface`の VSPackage に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>インターフェイス、および呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> VSPackage が、データを格納するためのセクションでは、データを持つメソッド。 環境ごとにこのプロセスを繰り返します`preSolution`セクション。

3. 環境は、プロジェクトの永続化要素を反復処理します。 この場合は、1 つのプロジェクトがあります。

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   このステートメントには、GUID の一意のプロジェクトおよびプロジェクトの種類の GUID が含まれています。 この情報は、プロジェクト ファイルまたはソリューションに属するファイルを検索する環境で使用し、VSPackage は、各プロジェクトに必要なします。 GUID に渡されるプロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>し、プロジェクトに関連する特定の VSPackage を読み込むには、プロジェクトは、VSPackage によって読み込まします。 ここでは、このプロジェクトに読み込まれる VSPackage は、Visual Basic です。

   ソリューション内の他のプロジェクトで必要に応じて、アクセスできるように、各プロジェクトは、一意のプロジェクト インスタンス ID を保持できます。 理想的には、ソリューションとプロジェクトがソース コード管理下にある場合は、プロジェクトにパスの起点ソリューションへのパスにする必要があります。 ソリューションが最初に読み込まれたときに、プロジェクト ファイルは、ユーザーのコンピューターにすることはできません。 ソリューション ファイルの相対サーバーに格納されているプロジェクト ファイルで、プロジェクト ファイルを見つけ、ユーザーのコンピューターにコピーの比較的シンプルです。 コピーにし、プロジェクトに必要なファイルの残りの部分を読み込みます。

4. .Sln ファイルの [プロジェクト] セクションに含まれている情報に基づいて、環境は、各プロジェクト ファイルを読み込みます。 プロジェクト自体は、プロジェクト階層を設定し、任意の入れ子になったプロジェクトの読み込みを担当します。

5. .Sln ファイルのセクションではすべてが処理された後、ソリューションはソリューション エクスプ ローラーで表示され、ユーザーによる変更の準備ができて。

ソリューションにプロジェクトを実装するすべての VSPackage を読み込むが失敗した場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>メソッドが呼び出され、ソリューション内の他のすべてのプロジェクトが読み込み中に加えた可能性のある変更を無視するチャンスが与えられる。 解析エラーが発生した場合は、ソリューション ファイルをできるだけ多くの情報が保持され、環境には、ソリューションが破損していることをユーザーに警告 ダイアログ ボックスが表示されます。

ソリューションを保存または閉じたときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>メソッドが呼び出され、.sln ファイルに入力する必要があるソリューションに変更が加えられましたかどうかに表示する階層に渡されます。 渡される、null 値`QuerySaveSolutionProps`で<xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>情報は、ソリューションの永続化されることを示します。 ポインターによって決定されます、特定のプロジェクトの永続化された情報は、値が null でない場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイス。

保存する情報がある場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>インターフェイスへのポインターを使用して呼び出した、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>メソッド。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>から名前/値ペアを取得するための環境ではメソッドが呼び出されます`IPropertyBag`インターフェイスし、.sln ファイルに情報を書き込みます。

`SaveSolutionProps` `WriteSolutionProps`から保存する情報を取得するための環境でオブジェクトに再帰的が呼び出されます、 `IPropertyBag` .sln ファイルにすべての変更が入力されるまでのインターフェイスします。 これにより、ソリューションと使用可能な次に、ソリューションを開いたときの情報を保存することを確認できます。

.Sln ファイルに保存するものがあるかどうかをすべて読み込む VSPackage が列挙されます。 レジストリ キーがクエリの読み込み時にのみになります。 環境は、ソリューションを保存時にメモリ内にいるため、すべての読み込まれたパッケージについて認識します。

だけ、.sln ファイル内のエントリが含まれる、`preSolution`と`postSolution`セクション。 ありませんと同様のセクションでは、.suo ファイルでソリューションには、この情報を正常に読み込むことが必要があるため。 .Suo ファイルには、共有またはソース コード管理下に配置するものではありませんが秘密のノートなど、ユーザー固有のオプションが含まれています。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [ソリューション ユーザー オプション (.Suo) ファイル](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [ソリューション](../../extensibility/internals/solutions-overview.md)