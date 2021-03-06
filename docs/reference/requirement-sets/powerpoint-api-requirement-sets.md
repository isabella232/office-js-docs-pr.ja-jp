---
title: PowerPoint JavaScript API の要件セット
description: PowerPoint JavaScript API の要件セットの詳細情報。
ms.date: 10/26/2020
ms.prod: powerpoint
localization_priority: Priority
ms.openlocfilehash: cf9ab510e4b35a140c77ee958279cb85a2189fa2
ms.sourcegitcommit: a4e09546fd59579439025aca9cc58474b5ae7676
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "48774729"
---
# <a name="powerpoint-javascript-api-requirement-sets"></a>PowerPoint JavaScript API の要件セット

要件セットは、API メンバーの名前付きグループです。Office アドインは、マニフェストで指定されている要件セットを使用するか、ランタイム チェックを使用して、Office アプリケーションがアドインに必要な API をサポートしているかどうかを判別します。詳しくは、「[Office のバージョンと要件セット](../../develop/office-versions-and-requirement-sets.md)」をご覧ください。

次の表は、PowerPoint の要件セット、それらの要件セットをサポートする Office クライアント アプリケーション、ビルド バージョンまたは一般提供開始日の一覧です。

|  要件セット  |  Windows での Office<br>(Microsoft 365 サブスクリプションに接続)  |  Office on iPad<br>(Microsoft 365 サブスクリプションに接続)  |  Office on Mac<br>(Microsoft 365 サブスクリプションに接続)  | Office on the web |
|:-----|-----|:-----|:-----|:-----|:-----|
| [プレビュー](powerpoint-preview-apis.md)  | プレビュー API を試すには、最新版 Office を使用してください (場合によっては、[Office Insider プログラム](https://insider.office.com)に参加する必要があります)。 |
| PowerPointApi 1.1 | バージョン 1810 (ビルド 11001.20074) 以降 | 2.17 以降 | 16.19 以降 | 2018 年 10 月 |

## <a name="office-versions-and-build-numbers"></a>Office のバージョンとビルド番号

Office のバージョンとビルド番号の詳細については、次を参照してください。

[!INCLUDE [Links to get Office versions and how to find Office client version](../../includes/links-get-office-versions-builds.md)]

## <a name="powerpoint-javascript-api-11"></a>PowerPoint JavaScript API 1.1

PowerPoint JavaScript API 1.1 には、[新しいプレゼンテーションを作成するための 1 つの API](/javascript/api/powerpoint#powerpoint-createpresentation-base64file-) が含まれます。 API の詳細については、「[プレゼンテーションを作成する](../../powerpoint/powerpoint-add-ins.md#create-a-presentation)」を参照してください。

## <a name="how-to-use-powerpoint-requirement-sets-at-runtime-and-in-the-manifest"></a>実行時およびマニフェストで PowerPoint 要件セットを使用する方法

> [!NOTE]
> このセクションでは、[Office バージョンと要件セット](../../develop/office-versions-and-requirement-sets.md) の概要、および [Office アプリケーションと API 要件の指定](../../develop/specify-office-hosts-and-api-requirements.md) について理解していることを前提としています。

要件セットは、API メンバーの名前付きグループです。 Office アドインはランタイム チェックを実行できます。または、マニフェストで指定されている要件セットを使用して、Office アプリケーションがアドインに必要な API をサポートしているかどうかを確認できます。

### <a name="checking-for-requirement-set-support-at-runtime"></a>実行時に要件セットのサポートを確認する

次のコード サンプルは、アドインが実行されている Office アプリケーションが指定された API の要件セットをサポートしているかどうかを確認する方法を示しています。

```js
if (Office.context.requirements.isSetSupported('PowerPointApi', '1.1')) {
  // Perform actions.
} else {
  // Provide alternate flow/logic.
}
```

### <a name="defining-requirement-set-support-in-the-manifest"></a>マニフェストで要件セットのサポートを定義する

アドインのマニフェストで [Requirements 要素](../manifest/requirements.md) を使用して、アドインをアクティブにするために必要な最小要件セットや API メソッド (またはその両方) を指定できます。 Office アプリケーションまたはプラットフォームが、マニフェストの `Requirements` 要素で指定されている要件セットまたは API メソッドをサポートしていない場合、アドインはそのアプリケーションまたはプラットフォームで実行されず、 **[マイ アドイン]** に表示されるアドインのリストに表示されません。アドインが完全な機能のために特定の要件セットを必要とするが、要件セットをサポートしていないプラットフォームのユーザーにも価値を提供できる場合は、マニフェストの要件セットのサポートを定義する代わりに、上記のように実行時に要件サポートを確認することをお勧めします。

次のコード サンプルは、アドインが PowerPointApi 要件セットのバージョン 1.1 以上をサポートする Office クライアント アプリケーションのすべてで読み込まれる必要があることを指定する、アドインのマニフェストの `Requirements` 要素を示しています。

```xml
<Requirements>
   <Sets DefaultMinVersion="1.1">
      <Set Name="PowerPointApi" MinVersion="1.1"/>
   </Sets>
</Requirements>
```

## <a name="office-common-api-requirement-sets"></a>Office 共通 API の要件セット

PowerPoint のほとんどのアドイン機能は、共通の API セットから取得されます。 共通 API の要件セットの詳細については、「[Office 共通 API の要件セット](office-add-in-requirement-sets.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- [PowerPoint JavaScript API リファレンス ドキュメント](/javascript/api/powerpoint)
- [Office のバージョンと要件セット](../../develop/office-versions-and-requirement-sets.md)
- [Office アプリケーションと API 要件を指定する](../../develop/specify-office-hosts-and-api-requirements.md)
- [Office アドインの XML マニフェスト](../../develop/add-in-manifests.md)
