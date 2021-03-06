---
title: Visual Studio SDK の用語集 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c189c4c9e06d224d7cef296a2c39e732cbc29f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538716"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK の用語集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この用語集で使用される用語の定義を提供する、[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]ドキュメント。  
  
## <a name="terms"></a>用語  
 アドイン  
 ユーティリティのアプリケーション、ドライバー、またはその他のソフトウェアの主要なアプリケーションに追加します。 Visual Studio 統合開発環境 (IDE) でアドインを IDE の機能を拡張するオートメーション ベースのアプリケーションです。  
  
 オートメーション モデル  
 以前のバージョンの Visual Studio 機能拡張モデルとして知られている、オートメーション モデルが提供されるプログラミング インターフェイスでは、そのドライブの IDE を基になるルーチンにアクセスします。 アドイン、ウィザード、およびマクロは、コントロールにオートメーション モデルのオブジェクトを使用または IDE の機能を拡張します。  
  
 コマンド UI コンテキスト  
 UI コマンドやツールバーなどの要素の可視性を持つ、GUID の関連付けです。 コマンド UI コンテキストは選択コンテキストとは異なり、ウィンドウにアタッチされていません。  
  
 コマンド UI コンテキストを使用できます。  
  
- 特定のウィンドウがアクティブ化されるときに表示されるツールバーに GUID を割り当てます。  
  
- コマンドの可用性をロードまたは VSPackage を実行することがなく、GUID を割り当てます。  
  
- アクティブなキー バインドに影響を与えるには、GUID を割り当てます。  
  
- マクロの記録を有効にするのには、GUID を割り当てます。  
  
- デバッグ モードをアクティブ化、またはデザインと、エディターでの実行モードを切り替える GUID を割り当てます。  
  
  コンポーネント  
  そのアプリケーションの既存ソフトウェアの実装に関する情報を持つことがなく、アプリケーションの機能の一部を作成できるソフトウェアの一部です。 コンポーネントとアプリケーション間の通信は、OLE スタイルのインターフェイスを通じてのみです。  
  
  コンポーネント マネージャー  
  サービス、 `SOleComponentManager`、最上位のコンポーネントの非ユーザー インターフェイスの調整のサービスを提供します。 `SOleComponentManager`サービスの実装、`IOleComponentManager`インターフェイス。  
  
  コンポーネントの UI マネージャー  
  サービス、 `SOleComponentUIManager`、ユーザー インターフェイスの調整サービス提供します。 `SOleComponentUIManager`サービスの実装、`IOleComponentUIManager`と`IOleInPlaceComponentUIManager`インターフェイス。  
  
  コンテキスト バッグ  
  `IVsUserContext`オブジェクト (COM オブジェクト) は、環境のコンポーネントにアタッチします。 このオブジェクトは、検索キーワード、F1 キーワード、およびコンポーネントに関連する属性を保持します。 コンテキスト バッグは、さらに、それらにリンクされている任意のサブコンテキスト バッグをポイントします。  
  
  コンテキスト プロバイダー  
  関連付けられているコンテキスト バッグ IDE 内のコンポーネント。 このようなコンポーネントには、ツール ウィンドウ、エディター、またはプロジェクトの階層が含まれます。  
  
  designer  
  ユーザー (フォーム、ボタン、およびその他のコントロール) の UI の要素を操作できるようにするプログラミング インターフェイスです。  
  
  DocData  
  世界中のドキュメントの基になるデータをカプセル化する COM オブジェクトがドキュメント/ビューの分離がある場合 (たとえば、テキスト エディターの場合、これはすべてのテキスト エディター ビューを基になるテキスト バッファー)。 EditorFactory がこのオブジェクトを指定しない場合は、自身のために IDE は製造します。 このオブジェクトの責任は、データの永続化を管理して、複数の共有セマンティクスが同じには、このビュー`DocData`します。 場合、`DocData`サポートしています、`IOleCommandTarget`インターフェイス、UIShell のコマンドのルーティングに入ります。  
  
  DocObject  
  テクノロジは、ホストによって提供されるフレーム内で UI をホストするために使用します。 サポートする任意の埋め込みに関係する用語の具体的には、`IOleDocument`および関連するインターフェイス。 このテクノロジでは、COM ドキュメントの実装の詳細ツール ウィンドウには、Visual Basic 5.0、Visual Basic 6.0 での ActiveX デザイナーなどの多くの潜在的なアプリケーションがあります。  
  
  document  
  一般的に、ドキュメント全体として参照するために使用 — 両方、 `DocData` 、`DocView`します。 など、DocumentFrame が含まれています、`DocView`への参照が保持されますが、`DocData`永続化を処理します。  
  
  DocView  
  基になる操作を表示したり、ユーザーが対話する、DocObject/埋め込み/ペイン`DocData`します。 ユーザーが含まれているドキュメント/ビューの分離の利点を実行できませんに注意してください、`DocObject`インターフェイスを設計します。 ユーザーでは、全体の DocObject を使用して、抽象的 (と小さい形式化された) と呼ばれる、基になるデータの概念を使用する代わりにビューとして機能する`DocData`します。 `DocView` オブジェクトは、IDE のドキュメント フレーム オブジェクト (MDI 子ウィンドウ) を常に埋め込まれます。  
  
  DTE  
  `DTE` (開発ツールの拡張機能) のオブジェクトは最上位のアクセス ポイントでは、Visual Studio のオートメーション モデルをプログラムでの自動化や、IDE を拡張することができます。  
  
  [ダイナミック ヘルプ] ウィンドウ  
  ツール ウィンドウは IDE によって実装され、検索キーワードまたは F1 ヘルプ トピックの一覧を表示します。  
  
  エディター  
  (クラス、CLSID) を実装するコード、`DocView`します。 またも実装`DocData`ビュー/データの分離がサポートされている場合。  
  
  拡張機能  
  変更、カスタマイズ、または IDE に追加する機能です。 Vspackage、オートメーション モデルを使用して拡張機能を作成します。  
  
  外部エディター  
  エディターは、Microsoft Word など、IDE に固有ではないです。 独自のメカニズムによって登録されているし、IDE の外部で使用できます。 このエディターを埋め込むことができる場合は、IDE のウィンドウに表示されます。 、埋め込むことができない場合は、独立したトップレベル ウィンドウが作成されます。  
  
  階層構造  
  ツリー ノードの各ノードに関連付けられたプロパティのセット。  
  
  独立した最上位のコンポーネント  
  モードレスの最上位ウィンドウを使用してとをスタンドアロンのアプリケーション ウィンドウとして効果的に操作できますがプロセスでオブジェクトとして実装するコンポーネント。 そのため、独立した最上位コンポーネントでは、モダリティおよび IDE にメッセージ ループのサービスを調整する必要があります。 プロセス内のオブジェクトには、独自のメッセージ ループはありません。  
  
  情報プロバイダー  
  情報プロバイダーは、キーワードを検索できの形式で、トピックの一覧を返すモジュール`IVsUserContextItem`オブジェクト。 情報プロバイダーの F1 および検索キーワードの項目を提供する、コンパイル済みヘルプ ファイルを登録します (します。HxS) システムとします。 これらのファイルのヘルプ トピックを使用して、ダイナミック ヘルプ ウィンドウに表示され、ユーザーが f1 キーを押したかどうかを示すトピックの一覧を提供します。  
  
  インプレース コンポーネント  
  実装する VSPackage オブジェクト、 `IOleInPlaceComponent` IDE によって所有されているドキュメント ウィンドウ内で視覚的に含まれているウィンドウを管理するインターフェイス。 インプレース コンポーネントは、標準 OLE メニュー結合; に参加していません。代わりに、ユーザー インターフェイス要素を IDE に統合します。  
  
  インプレース コンポーネントの 2 種類があります。 固定インプレース コンポーネントとコントロールのコンポーネント。  
  
  有線インプレース コンポーネントは、メニューのツールバー、およびとして表示される、IDE に直接ビルドされたかどうか、IDE のユーザー インターフェイスに緊密に統合されているコマンドがあります。  
  
  コンポーネントのコントロール、IDE に統合されて、独自のユーザー インターフェイス要素のいずれかがありません。代わりに、IDE のメニューのコマンド、およびツールバーを使用します。 たとえば、太字のコマンドは、フォームに埋め込まれているリッチ テキスト コントロール内で選択した単語を太字にされる可能性があります。 ただし、コンポーネント コントロールが動的にインストールされているコンポーネントに固有の UI 要素が表示されることを要求することができます。  
  
  言語サービス  
  コンピューター言語コード エディター、テキストをマークして、色分けなどの機能を実装する VSPackage 開発者のオブジェクトのセット。  
  
  その他のファイル プロジェクト  
  任意のプロジェクトに含まれない家の開いているファイルに使用するプロジェクト。 このプロジェクト内の項目の一覧は保持されません。  
  
  プロジェクト  
  プロジェクトが、オブジェクトの階層の構成または COM オブジェクトを実装する、`IVsHierarchy`インターフェイス。  
  
  プロジェクトに固有のデザイナーまたはエディター  
  デザイナーをプロジェクトの種類とは無関係に使用することはできません。 プロジェクトに固有のすべてのデザイナーでレジストリ エディター ファクトリ情報の入力する必要があります。 IDE、インスタンス化できますデザイナー、特定のプロジェクトで、特定の種類のファイルが開かれるたびにします。  
  
  プロジェクトの種類 ウィンドウ  
  常にグローバルの選択コンテキストから、階層の現在アクティブなプロジェクトと項目を追跡するウィンドウです。 プロジェクトの種類の windows を使用して、`SVsTrackSelectionEx`サービス変更の IDE のアラートを生成して、ユーザーにフィードバックを表示します。 ソリューション エクスプ ローラーでは、プロジェクトの種類 ウィンドウの例を示します。  
  
  [プロパティ] ウィンドウ  
  以前はプロパティ ブラウザーです。  
  
  プロジェクトの参照に基づく  
  同じディレクトリにあるプロジェクトのファイルを必要としないプロジェクトです。 代わりに、関連付けられていないその他のディレクトリからファイルへの参照が格納され、プロジェクト自体によって管理されます。  
  
  実行中の document テーブル  
  IDE が現在開いているすべてのドキュメントの一覧を保持する内部構造体。 この一覧には、ドキュメントの現在編集されているかどうかに関係なく、メモリ内のすべての開いているドキュメントが含まれています。 ドキュメントでは、エディター、プロジェクト内のファイルまたはメイン プロジェクト ファイル (たとえば、*.vcproj ファイル) で開かれているストアド プロシージャを含む、保存されているすべての項目です。  
  
  選択範囲のコンテキスト  
  IDE ですべてのウィンドウの詳細の一部であるし、アクティブな選択範囲を追跡するために使用されるデータ。 選択範囲のコンテキストで構成されます。  
  
- ポインター、`IVsHierarchy`プロジェクト階層のインターフェイス  
  
- プロジェクト項目の項目の識別子です。  
  
- ポインター、`ISelectionContainer`アクティブなオブジェクトのプロパティにアクセスを提供するインターフェイス。  
  
- 要素の値の配列。  
  
  サービス  
  1 つの COM オブジェクト内に存在する COM インターフェイスの一連のコントラクト。 GUID により識別される、サービスを作成するときに、サービスを実行する COM インターフェイスのセットを定義します。 COM オブジェクトは、相互に通信するサービスを使用します。  
  
  ソリューション  
  ユーザーには、関連するプロジェクトのグループです。  
  
  標準的なデザイナー  
  プロジェクトの種類の独立した使用できるデザイナー。 すべての標準的なデザイナーでレジストリ エディター ファクトリ情報の入力する必要があります。 IDE、インスタンス化できますデザイナー特定の拡張子を持つファイルが開かれるたびにします。 データは、ファイルに保存する必要があります。  
  
  標準エディター  
  あらゆる種類の特定のプロジェクトの独立した使用できるエディターです。 このようなエディターでは、レジストリに登録されている EditorFactories があります。 これにより、IDE を見つけて、エディターを起動できます。  
  
  OS の標準エディター  
  Visual Studio でない埋め込みを特定します。 よく知られている Win32 のキーを使用して登録されている (たとえば、Win32 エクスプ ローラーを呼び出す方法を認識する)。 このようなエディターを埋め込むことができる場合、エディターは、IDE でその場所にまだ表示します。 それ以外の場合、このようなエディターの独立したトップレベル ウィンドウが作成されます。  
  
  サブコンテキスト バッグ  
  `IVsUserContext`コンテキスト バッグにリンクされているオブジェクト。 このオブジェクトは、検索キーワード、F1 キーワード、および、IDE のコンポーネント内の選択項目の属性を保持します。 サブコンテキストの例には、ツール ウィンドウ、またはエディターでのキーワードでコマンドが含まれます。  
  
  タスク一覧  
  ツール ウィンドウは IDE によって実装され、アクティブなタスクの一覧を表示します。  
  
  テキスト バッファー  
  オブジェクトの共通名`VSTextBuffer`します。  
  
  テキスト ビュー  
  オブジェクトの共通名`VSTextView`します。  
  
  ツールの最上位のコンポーネント  
  IDE のユーザー インターフェイスと緊密に調整、モードレスのポップアップ ウィンドウとして動作するコンポーネント。 独立系の最上位コンポーネントと同様にツールの最上位のコンポーネントをモダリティおよび IDE にメッセージ ループのサービスも調整する必要があります。  
  
  最上位のコンポーネント  
  IDE ウィンドウのクライアント領域ではなくモードレス トップレベル ウィンドウを管理する VSPackage オブジェクト。 最上位のコンポーネントは、実装、`IOleComponent`アイドル時間にメッセージ ループなどのサービスへのアクセスを利用するインターフェイス。  
  
  アクティブな UI  
  VSPackage オブジェクトが表示されると、現在フォーカスがあるです。  
  
  UI 階層  
  実装する COM オブジェクト、`IVsUIHierarchy`階層を表示できるようにするインターフェイス。 UI 階層ウィンドウの実装、`ISelectionContainer`インターフェイスのプロパティ ウィンドウを更新する; 他のプロジェクトの種類の windows が必要な場合、この実装を使用できます。  
  
  VSCT  
  Visual Studio コマンド テーブルです。 .Vsct ファイルには、配置、メニューのツールバー、および XML 形式でコマンドの動作に関する情報が含まれています。  
  
  VSPackage  
  次の 1 つ以上提供することによって、Visual Studio IDE を拡張するソフトウェアのインストール可能な部分: ユーザー インターフェイス、サービス、プロジェクトの種類、またはエディターとデザイナー。 VSPackage を実装する COM オブジェクトから成る、`IVsPackage`インターフェイスと 1 つまたは複数の他の COM オブジェクトの選択とその他の機能をサポートするその他のインターフェイスを実装します。 さらに、VSPackage では、特定の登録要件がいます。
