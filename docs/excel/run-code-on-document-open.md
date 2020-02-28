---
title: ドキュメントを開くときに Excel アドインでコードを実行する (プレビュー)
description: ドキュメントが開いたときに、Excel アドインでコードを実行します。
ms.date: 02/20/2020
localization_priority: Normal
ms.openlocfilehash: 5b8c646a1154540244b1f5e0ac47ad8eaec1801f
ms.sourcegitcommit: dd6d00202f6466c27418247dad7bd136555a6036
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2020
ms.locfileid: "42284189"
---
# <a name="run-code-in-your-excel-add-in-when-the-document-opens-preview"></a><span data-ttu-id="e9e7d-103">ドキュメントを開くときに Excel アドインでコードを実行する (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="e9e7d-103">Run code in your Excel add-in when the document opens (preview)</span></span>

[!include[Running custom functions in browser runtime note](../includes/excel-shared-runtime-preview-note.md)]

<span data-ttu-id="e9e7d-104">ドキュメントが開かれるとすぐに、コードを読み込んで実行するように Excel アドインを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-104">You can configure your Excel add-in to load and run code as soon as the document is opened.</span></span> <span data-ttu-id="e9e7d-105">これは、アドインが表示される前に、イベントハンドラーの登録、作業ウィンドウのデータの事前読み込み、UI の同期、またはその他のタスクの実行を行う必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-105">This is useful if you need to register event handlers, preload data for the task pane, synchronize UI, or perform other tasks before the add-in is visible.</span></span>

[!include[Excel shared runtime note](../includes/note-requires-shared-runtime.md)]

## <a name="configure-your-add-in-to-load-when-the-document-opens"></a><span data-ttu-id="e9e7d-106">ドキュメントが開いたときに読み込まれるようにアドインを構成する</span><span class="sxs-lookup"><span data-stu-id="e9e7d-106">Configure your add-in to load when the document opens</span></span>

<span data-ttu-id="e9e7d-107">次のコードは、ドキュメントが開かれたときに読み込み、実行を開始するようにアドインを構成します。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-107">The following code configures your add-in to load and start running when the document is opened.</span></span>

```JavaScript
Office.addin.setStartupBehavior(Office.StartupBehavior.load);
```

> [!NOTE]
> <span data-ttu-id="e9e7d-108">`setStartupBehavior`メソッドは非同期です。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-108">The `setStartupBehavior` method is asynchronous.</span></span>

## <a name="configure-your-add-in-for-no-load-behavior-on-document-open"></a><span data-ttu-id="e9e7d-109">ドキュメントを開くときに読み込み動作を行わないようにアドインを構成する</span><span class="sxs-lookup"><span data-stu-id="e9e7d-109">Configure your add-in for no load behavior on document open</span></span>

<span data-ttu-id="e9e7d-110">次のコードは、ドキュメントが開かれたときに開始しないようにアドインを構成します。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-110">The following code configures your add-in not to start when the document is opened.</span></span> <span data-ttu-id="e9e7d-111">代わりに、ユーザーが何らかの方法 (リボンボタンを選択したときや作業ウィンドウを開いたときなど) に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-111">Instead it will start when the user engages it in some way (such as choosing a ribbon button, or opening the task pane.)</span></span>

```JavaScript
Office.addin.setStartupBehavior(Office.StartupBehavior.none);
```

## <a name="get-the-current-load-behavior"></a><span data-ttu-id="e9e7d-112">現在の読み込み動作を取得する</span><span class="sxs-lookup"><span data-stu-id="e9e7d-112">Get the current load behavior</span></span>

<span data-ttu-id="e9e7d-113">現在のスタートアップ動作を確認するには、次の関数を実行します。この関数は、Office の StartupBehavior オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-113">To determine what the current startup behavior is, run the following function, which returns an Office.StartupBehavior object.</span></span>

```JavaScript
let behavior = await Office.addin.getStartupBehavior();
```

## <a name="how-to-run-code-when-the-document-opens"></a><span data-ttu-id="e9e7d-114">ドキュメントが開いたときにコードを実行する方法</span><span class="sxs-lookup"><span data-stu-id="e9e7d-114">How to run code when the document opens</span></span>

<span data-ttu-id="e9e7d-115">アドインがドキュメントを開いたときに読み込むように構成すると、すぐに実行されます。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-115">When your add-in is configured to load on document open, it will run immediately.</span></span> <span data-ttu-id="e9e7d-116">`Office.initialize`イベントハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-116">The `Office.initialize` event handler will be called.</span></span> <span data-ttu-id="e9e7d-117">スタートアップコードを`Office.initialize`イベントハンドラーに配置します。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-117">Place your startup code in the `Office.initialize` event handler.</span></span>

<span data-ttu-id="e9e7d-118">次のコードは、作業中のワークシートから変更イベントのイベントハンドラーを登録する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-118">The following code shows how to register an event handler for change events from the active worksheet.</span></span> <span data-ttu-id="e9e7d-119">アドインをドキュメントを開いたときに読み込むように構成した場合、このコードは、ドキュメントが開かれたときにイベントハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-119">If you configure your add-in to load on document open, this code will register the event handler when the document is opened.</span></span> <span data-ttu-id="e9e7d-120">作業ウィンドウを開く前に、変更イベントを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="e9e7d-120">You can handle change events before the task pane is opened.</span></span>


```JavaScript
//This is called as soon as the document opens.
//Put your startup code here.
Office.initialize = () => {
  // Add the event handler
  Excel.run(async context => {
    let sheet = context.workbook.worksheets.getActiveWorksheet();
    sheet.onChanged.add(onChange);

    await context.sync();
    console.log("A handler has been registered for the onChanged event.");
  });
};

/**
 * Handle the changed event from the worksheet.
 *
 * @param event The event information from Excel
 */
async function onChange(event) {
  return Excel.run(function(context) {
    return context.sync().then(function() {
      console.log("Change type of event: " + event.changeType);
      console.log("Address of event: " + event.address);
      console.log("Source of event: " + event.source);
    });
  });
}

```

## <a name="see-also"></a><span data-ttu-id="e9e7d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9e7d-121">See also</span></span>

- [<span data-ttu-id="e9e7d-122">Excel カスタム関数と作業ウィンドウチュートリアルの間でデータとイベントを共有する</span><span class="sxs-lookup"><span data-stu-id="e9e7d-122">Share data and events between Excel custom functions and task pane tutorial</span></span>](../tutorials/share-data-and-events-between-custom-functions-and-the-task-pane-tutorial.md)