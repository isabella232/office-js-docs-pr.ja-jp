---
title: Outlook アドインの API
description: Outlook アドインの API を参照して、Outlook アドインにアクセス許可を宣言する方法について説明します。
ms.date: 02/27/2020
localization_priority: Normal
ms.openlocfilehash: bd7f3b5a1b52ec3ca7a48ae7a2d467c6cd30f1e4
ms.sourcegitcommit: 5d29801180f6939ec10efb778d2311be67d8b9f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2020
ms.locfileid: "42325472"
---
# <a name="outlook-add-in-apis"></a><span data-ttu-id="54690-103">Outlook アドインの API</span><span class="sxs-lookup"><span data-stu-id="54690-103">Outlook add-in APIs</span></span>

<span data-ttu-id="54690-104">Outlook アドインで API を使用するには、Office.js ライブラリの場所、要件セット、スキーマ、アクセス許可を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54690-104">To use APIs in your Outlook add-in, you must specify the location of the Office.js library, the requirement set, the schema, and the permissions.</span></span> <span data-ttu-id="54690-105">[メールボックス](#mailbox-object)オブジェクトを通じて公開される Office JavaScript api を主に使用します。</span><span class="sxs-lookup"><span data-stu-id="54690-105">You'll primarily use the Office JavaScript APIs exposed through the [Mailbox](#mailbox-object) object.</span></span>

## <a name="officejs-library"></a><span data-ttu-id="54690-106">Office.js ライブラリ</span><span class="sxs-lookup"><span data-stu-id="54690-106">Office.js library</span></span>

<span data-ttu-id="54690-107">Outlook アドイン API と対話操作するには、Office.js の JavaScript API を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54690-107">To interact with the Outlook add-in API, you need to use the JavaScript APIs in Office.js.</span></span> <span data-ttu-id="54690-108">ライブラリ用の CDN は `https://appsforoffice.microsoft.com/lib/1/hosted/Office.js` です。</span><span class="sxs-lookup"><span data-stu-id="54690-108">The CDN for the library is `https://appsforoffice.microsoft.com/lib/1/hosted/Office.js`.</span></span> <span data-ttu-id="54690-109">AppSource に送られるアドインは、この CDN で Office.js を参照しなければなりません。ローカル参照は使用できません。</span><span class="sxs-lookup"><span data-stu-id="54690-109">Add-ins submitted to AppSource must reference Office.js by this CDN; they can't use a local reference.</span></span>

<span data-ttu-id="54690-110">アドインの UI を実行する Web ページ (.html、.aspx、.php のファイル) の `<head>` タグの中の `<script>` タグの中で CDN を参照します。</span><span class="sxs-lookup"><span data-stu-id="54690-110">Reference the CDN in a `<script>` tag in the `<head>` tag of the web page (.html, .aspx, or .php file) that implements the UI of your add-in.</span></span>

```HTML
<script src="https://appsforoffice.microsoft.com/lib/1/hosted/Office.js" type="text/javascript"></script>
```
<span data-ttu-id="54690-p103">新しい API が追加されても、Office.js への URL は同じままになります。URL 内のバージョンは、既存の API の動作を分割する場合にのみ変更されます。</span><span class="sxs-lookup"><span data-stu-id="54690-p103">As we add new APIs, the URL to Office.js will stay the same. We will change the version in the URL only if we break an existing API behavior.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54690-113">任意の Office ホストアプリケーションのアドインを開発する場合は、ページのセクションの`<head>`内側から OFFICE JavaScript API を参照します。</span><span class="sxs-lookup"><span data-stu-id="54690-113">When developing an add-in for any Office host application, reference the Office JavaScript API from inside the `<head>` section of the page.</span></span> <span data-ttu-id="54690-114">これにより、あらゆる body 要素の前に API が完全に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="54690-114">This ensures that the API is fully initialized prior to any body elements.</span></span> <span data-ttu-id="54690-115">Office ホストでは、アクティブ化の 5 秒以内にアドインを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54690-115">Office hosts require that add-ins initialize within 5 seconds of activation.</span></span> <span data-ttu-id="54690-116">このしきい値を超えるとアドインが応答なしと宣言され、ユーザーにエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54690-116">Crossing this threshold results in the add-in being declared unresponsive and an error message is displayed to the user.</span></span>

## <a name="requirement-sets"></a><span data-ttu-id="54690-117">要件セット</span><span class="sxs-lookup"><span data-stu-id="54690-117">Requirement sets</span></span>

<span data-ttu-id="54690-118">すべての Outlook API は `Mailbox` 要件セットに属しています。</span><span class="sxs-lookup"><span data-stu-id="54690-118">All Outlook APIs belong to the `Mailbox` requirement set.</span></span> <span data-ttu-id="54690-119">`Mailbox` の要件セットにはバージョンがあり、リリースされる新しい API の各セットは、新しいバージョンのセットに属しています。</span><span class="sxs-lookup"><span data-stu-id="54690-119">The `Mailbox` requirement set has versions, and each new set of APIs that are released belongs to a higher version of the set.</span></span> <span data-ttu-id="54690-120">最新の API セットがリリースされても、すべての Outlook クライアントがそれをサポートするわけではありませんが、ある Outlook クライアントが 1 つの要件セットのサポートを宣言した場合、その要件セットの中のすべての API がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="54690-120">Not all Outlook clients will support the newest set of APIs when they are released, but if an Outlook client declares support for a requirement set, it will support all the APIs in that requirement set.</span></span>

<span data-ttu-id="54690-p106">どの Outlook クライアントにアドインを表示するかを制御するには、最小の要件セットのバージョンをマニフェストで指定します。たとえば、要件セットのバージョン 1.3 を指定すると、最小バージョンの 1.3 をサポートしていない Outlook クライアントにはアドインが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="54690-p106">To control which Outlook clients the add-in appears in, specify a minimum requirement set version in the manifest. For example, if you specify requirement set version 1.3, the add-in will not show up in any Outlook client that doesn't support a minimum version of 1.3.</span></span>

<span data-ttu-id="54690-p107">要件セットを指定しても、そのバージョンの API にアドインを限定することにはなりません。要件セット v1.1 を指定しているアドインが、v1.3 をサポートする Outlook クライアントで実行されると、そのアドインは v1.3 の API を使用できます。要件セットでは、どの Outlook クライアントにアドインを表示するかのみを制御します。</span><span class="sxs-lookup"><span data-stu-id="54690-p107">Specifying a requirement set doesn't limit your add-in to the APIs in that version. If the add-in specifies requirement set v1.1 but is running in an Outlook client that supports v1.3, the add-in can still use v1.3 APIs. The requirement set only controls which Outlook clients the add-in appears in.</span></span>

<span data-ttu-id="54690-126">マニフェストで指定した要件セットよりも上位の要件セットの API が使用できるかどうかを確認する場合は、標準の JavaScript を使用できます。</span><span class="sxs-lookup"><span data-stu-id="54690-126">To check the availability of any APIs from a requirement set greater than the one specified in the manifest, you can use standard JavaScript:</span></span>

```js
if (item.somePropertyOrFunction) {
   item.somePropertyOrFunction...  
}
```

> [!NOTE]
> <span data-ttu-id="54690-127">このような確認は、マニフェストで指定された要件セットのバージョンに存在する API には必要ありません。</span><span class="sxs-lookup"><span data-stu-id="54690-127">These checks are not needed for any APIs that are in the requirement set version specified in the manifest.</span></span>

<span data-ttu-id="54690-128">それなしではアドインの機能が機能しないような、シナリオに絶対必要な API のセットをサポートする最低限要件セットを指定します。</span><span class="sxs-lookup"><span data-stu-id="54690-128">Specify the minimum requirement set that supports the critical set of APIs for your scenario, without which features of your add-in won't work.</span></span> <span data-ttu-id="54690-129">要件セットは、`<Requirements>` 要素内のマニフェストで指定します。</span><span class="sxs-lookup"><span data-stu-id="54690-129">You specify the requirement set in the manifest in the `<Requirements>` element.</span></span> <span data-ttu-id="54690-130">詳細は、[Outlook のアドイン マニフェスト](manifests.md)と「[Outlook API 要件セットについて](../reference/requirement-sets/outlook-api-requirement-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54690-130">For more information, see [Outlook add-in manifests](manifests.md) and [Understanding Outlook API requirement sets](../reference/requirement-sets/outlook-api-requirement-sets.md).</span></span>

<span data-ttu-id="54690-131">`<Methods>` 要素は Outlook アドインには適用されないので、特定のメソッドのサポートは宣言できません。</span><span class="sxs-lookup"><span data-stu-id="54690-131">The `<Methods>` element doesn't apply to Outlook add-ins, so you can't declare support for specific methods.</span></span>

## <a name="permissions"></a><span data-ttu-id="54690-132">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="54690-132">Permissions</span></span>

<span data-ttu-id="54690-p109">アドインには、そのアドインが必要とする API を使用するための適切なアクセス許可が必要になります。アクセス許可には、4 つのレベルがあります。詳細については、「[Outlook アドインのアクセス許可モデルを理解する](understanding-outlook-add-in-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54690-p109">Your add-in requires the appropriate permissions to use the APIs that it needs. There are four levels of permissions. For more details, see [Understanding Outlook add-in permissions](understanding-outlook-add-in-permissions.md).</span></span>

<br/>

|<span data-ttu-id="54690-136">権限レベル</span><span class="sxs-lookup"><span data-stu-id="54690-136">Permission level</span></span>|<span data-ttu-id="54690-137">説明</span><span class="sxs-lookup"><span data-stu-id="54690-137">Description</span></span>|
|:-----|:-----|
| <span data-ttu-id="54690-138">**制限付き**</span><span class="sxs-lookup"><span data-stu-id="54690-138">**Restricted**</span></span> | <span data-ttu-id="54690-139">エンティティは使用できますが、正規表現は使用できません。</span><span class="sxs-lookup"><span data-stu-id="54690-139">Allows use of entities but not regular expressions.</span></span> |
| <span data-ttu-id="54690-140">**アイテムの読み取り**</span><span class="sxs-lookup"><span data-stu-id="54690-140">**Read item**</span></span> | <span data-ttu-id="54690-141">**制限付き**で許可されているものに加えて、以下のものが許可されます。</span><span class="sxs-lookup"><span data-stu-id="54690-141">In addition to what is allowed in **Restricted**, it allows:</span></span><ul><li><span data-ttu-id="54690-142">正規表現</span><span class="sxs-lookup"><span data-stu-id="54690-142">regular expressions</span></span></li><li><span data-ttu-id="54690-143">Outlook アドイン API の読み取りアクセス</span><span class="sxs-lookup"><span data-stu-id="54690-143">Outlook add-in API read access</span></span></li><li><span data-ttu-id="54690-144">アイテムのプロパティとコールバック トークンの取得</span><span class="sxs-lookup"><span data-stu-id="54690-144">getting the item properties and the callback token</span></span></li></ul> |
| <span data-ttu-id="54690-145">**読み取り/書き込み**</span><span class="sxs-lookup"><span data-stu-id="54690-145">**Read/write**</span></span> | <span data-ttu-id="54690-146">**アイテムの読み取り**で許可される内容に加えて、次に示す内容が許可されます。</span><span class="sxs-lookup"><span data-stu-id="54690-146">In addition to what is allowed in **Read item**, it allows:</span></span><ul><li><span data-ttu-id="54690-147">`makeEwsRequestAsync` を除いた、完全な Outlook アドイン API のアクセス</span><span class="sxs-lookup"><span data-stu-id="54690-147">full Outlook add-in API access except `makeEwsRequestAsync`</span></span></li><li><span data-ttu-id="54690-148">アイテムのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="54690-148">setting the item properties</span></span></li></ul> |
| <span data-ttu-id="54690-149">**メールボックスの読み取り/書き込み**</span><span class="sxs-lookup"><span data-stu-id="54690-149">**Read/write mailbox**</span></span> | <span data-ttu-id="54690-150">**読み取り/書き込み**で許可されているものに加えて、以下のものが許可されます。</span><span class="sxs-lookup"><span data-stu-id="54690-150">In addition to what is allowed in **Read/write**, it allows:</span></span><ul><li><span data-ttu-id="54690-151">アイテムやフォルダーの作成、読み取り、書き込み</span><span class="sxs-lookup"><span data-stu-id="54690-151">creating, reading, writing items and folders</span></span></li><li><span data-ttu-id="54690-152">アイテムの送信</span><span class="sxs-lookup"><span data-stu-id="54690-152">sending items</span></span></li><li><span data-ttu-id="54690-153">[makeEwsRequestAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.md#methods) の呼び出し</span><span class="sxs-lookup"><span data-stu-id="54690-153">calling [makeEwsRequestAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.md#methods)</span></span></li></ul> |

<span data-ttu-id="54690-154">一般的には、アドインに必要な最低限のアクセス許可を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54690-154">In general, you should specify the minimum permission needed for your add-in.</span></span> <span data-ttu-id="54690-155">アクセス許可は、マニフェスト内の `<Permissions>` 要素で宣言されます。</span><span class="sxs-lookup"><span data-stu-id="54690-155">Permissions are declared in the `<Permissions>` element in the manifest.</span></span> <span data-ttu-id="54690-156">詳細については、「[Outlook アドインのマニフェスト](manifests.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54690-156">For more information, see [Outlook add-in manifests](manifests.md).</span></span> <span data-ttu-id="54690-157">セキュリティの問題の詳細については、「 [Office アドインのプライバシーとセキュリティ](../concepts/privacy-and-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54690-157">For information about security issues, see [Privacy and security for Office Add-ins](../concepts/privacy-and-security.md).</span></span>

## <a name="mailbox-object"></a><span data-ttu-id="54690-158">Mailbox オブジェクト</span><span class="sxs-lookup"><span data-stu-id="54690-158">Mailbox object</span></span>

[!include[information about Mailbox object](../includes/mailbox-object-desc.md)]

## <a name="see-also"></a><span data-ttu-id="54690-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="54690-159">See also</span></span>

- [<span data-ttu-id="54690-160">Outlook アドインのマニフェスト</span><span class="sxs-lookup"><span data-stu-id="54690-160">Outlook add-in manifests</span></span>](manifests.md)
- [<span data-ttu-id="54690-161">Outlook API 要件セットについて</span><span class="sxs-lookup"><span data-stu-id="54690-161">Understanding Outlook API requirement sets</span></span>](../reference/requirement-sets/outlook-api-requirement-sets.md)
- [<span data-ttu-id="54690-162">Office アドインのプライバシーとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="54690-162">Privacy and security for Office Add-ins</span></span>](../concepts/privacy-and-security.md)