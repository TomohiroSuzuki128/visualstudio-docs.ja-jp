---
title: '方法: エンティティ間の関連付けを作成する |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cba9d712e2bcfa90ae37d47e3c518697f10b6add
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981830"
---
# <a name="how-to-create-an-association-between-entities"></a>方法: エンティティ間の関連付けを作成する
  関連付けを作成することによって、Business Data Connectivity (BDC) モデルのエンティティ間のリレーションシップを定義できます。 Visual Studio では、モデルのコンシューマーに各アソシエーションに関する情報を提供するメソッドが生成されます。 これらのメソッドは、SharePoint web パーツ、リスト、またはカスタムアプリケーションで、ユーザーインターフェイス (UI) にデータリレーションシップを表示するために使用できます。

 BDC デザイナーでは、外部キーベースの関連付けと外部キーなしの関連付けの2種類の関連付けを作成できます。 詳細については、「[エンティティ間の関連付けを作成](../sharepoint/creating-an-association-between-entities.md)する」を参照してください。

### <a name="to-create-an-association-between-entities"></a>エンティティ間の関連付けを作成するには

1. **ツールボックス**の **[BusinessDataConnectivity]** タブで、 **[Association]** 項目を選択します。

2. BDC デザイナーで、[ソース] エンティティを選択し、目的のエンティティを選択します。

     **関連付けエディター**が表示されます。

3. 外部キーベースの関連付けを作成する場合は、 **[外部キーの関連付け]** チェックボックスをオンにします。

    1. **識別子マッピング**テーブルの **[ソース ID]** 列で、[**フィールド]** 列に表示される一致する各型記述子の横にある識別子を選択します。

         たとえば、 **[ソース ID]** 列で、`ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` 型記述子と `ReadItem.salesOrder.SalesOrder.ContactID` 型記述子の横にある [`ContactID`] を選択します。

4. 外部キーなし関連付けを作成する場合は、 **[外部キーの関連付け]** チェックボックスをオフにします。

5. **[OK]** を選択します。

6. BDC デザイナーでは、関連付けを表す線が、ソースエンティティとターゲットエンティティの間に表示されます。

     Visual Studio では、ターゲットエンティティのサービスクラスとソースエンティティのサービスクラスに Association Navigator メソッドが追加されます。 アソシエーションナビゲーションメソッドの詳細については、「[サポートされる操作](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))」を参照してください。

7. ソースエンティティの Association Navigator メソッドで、変換先エンティティのコレクションを返すコードを追加します。

8. ターゲットエンティティの Association Navigator メソッドで、関連するソースエンティティを返すコードを追加します。

     アソシエーションナビゲーターのメソッドの例については、「[エンティティ間の関連付けを作成](../sharepoint/creating-an-association-between-entities.md)する」を参照してください。

## <a name="see-also"></a>関連項目
- [エンティティ間の関連付けを作成する](../sharepoint/creating-an-association-between-entities.md)
- [ビジネスデータ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)
- [方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)
- [方法: 特定の Finder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)
- [方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md)
- [方法: 削除子メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md)
- [方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md)
- [BDC モデルのデザインツールの概要](../sharepoint/bdc-model-design-tools-overview.md)
- [方法: メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [方法: メソッドインスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)
- [方法: パラメーターの型記述子を定義する](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [チュートリアル: ビジネスデータを使用した SharePoint での外部リストの作成](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
