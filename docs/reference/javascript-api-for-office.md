# <a name="javascript-api-for-office"></a><span data-ttu-id="7be10-101">JavaScript API for Office</span><span class="sxs-lookup"><span data-stu-id="7be10-101">JavaScript API for Office</span></span>

<span data-ttu-id="7be10-102">JavaScript API for Office を使用すると、Office ホスト アプリケーションのオブジェクト モデルと相互作用する Web アプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7be10-102">The JavaScript API for Office enables you to create web applications that interact with the object models in Office host applications.</span></span> <span data-ttu-id="7be10-103">このアプリケーションは、スクリプト ローダーである office.js ライブラリを参照します。</span><span class="sxs-lookup"><span data-stu-id="7be10-103">Your application will reference the office.js library, which is a script loader.</span></span> <span data-ttu-id="7be10-104">office.js ライブラリは、アドインを実行している Office アプリケーションに適用可能なオブジェクト モデルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7be10-104">The office.js library loads the object models that are applicable to the Office application that is running the add-in.</span></span> <span data-ttu-id="7be10-105">次の JavaScript オブジェクト モデルを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="7be10-105">You can use the following JavaScript object models:</span></span>

- <span data-ttu-id="7be10-106">**一般的な API** - **Office 2013** で導入された API です。</span><span class="sxs-lookup"><span data-stu-id="7be10-106">**Common APIs** - APIs that were introduced with **Office 2013**.</span></span> <span data-ttu-id="7be10-107">これは、**すべての Office ホスト アプリケーション**に読み込まれ、アドイン アプリケーションを Office クライアント アプリケーションに接続します。</span><span class="sxs-lookup"><span data-stu-id="7be10-107">This is loaded for **all Office host applications** and connects your add-in application with the Office client application.</span></span> <span data-ttu-id="7be10-108">オブジェクト モデルには、Office クライアントに固有の API と複数の Office クライアントのホスト アプリケーションに適用可能な API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7be10-108">The object model contains APIs that are specific to Office clients, and APIs that are applicable to multiple Office client host applications.</span></span> <span data-ttu-id="7be10-109">すべてのコンテンツは、 **共有 API** の配下にあります。</span><span class="sxs-lookup"><span data-stu-id="7be10-109">All of this content is under **Shared API**.</span></span> 

  <span data-ttu-id="7be10-110">**Outlook** は、共通の API 構文も使用します。</span><span class="sxs-lookup"><span data-stu-id="7be10-110">**Outlook** also uses the common API syntax.</span></span> <span data-ttu-id="7be10-111">エイリアス Office の配下に置かれているすべてのものには、Office アドインからの Office ドキュメント、ワークシート、プレゼンテーション、メール アイテム、およびプロジェクトのコンテンツとインタラクティブなスクリプトを書くために使用できるオブジェクトが含まれます。お使いのアドインが Office 2013 以降を対象としている場合、これらの共通 API を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7be10-111">Everything under the alias Office contains objects you can use to write scripts that interact with content in Office documents, worksheets, presentations, mail items, and projects from your Office Add-ins. You must use these common APIs if your add-in will target Office 2013 and later.</span></span> <span data-ttu-id="7be10-112">このオブジェクト モデルは、コールバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="7be10-112">This object model uses callbacks.</span></span>

- <span data-ttu-id="7be10-113">**ホスト固有の API** - **Office 2016** で導入された API 。</span><span class="sxs-lookup"><span data-stu-id="7be10-113">**Host-specific APIs** - APIs that were introduced with **Office 2016**.</span></span> <span data-ttu-id="7be10-114">このオブジェクト モデルは、Office クライアントの使用時に見られる使い慣れたオブジェクトに対応するホスト固有の厳密に型指定されたオブジェクトを提供し、Office JavaScript API の将来像を表すものです。</span><span class="sxs-lookup"><span data-stu-id="7be10-114">Host-specific - APIs that were introduced with Office 2016. This object model provides host-specific strongly-typed objects that correspond to familiar objects that you see when you use Office clients, and represents the future of Office JavaScript APIs. The host-specific APIs currently include the Word JavaScript API and the Excel JavaScript API.</span></span> <span data-ttu-id="7be10-115">現在、ホスト固有の API には、Word JavaScript API と Excel JavaScript API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7be10-115">The host-specific APIs currently include the Word JavaScript API and the Excel JavaScript API.</span></span>

## <a name="supported-host-applications"></a><span data-ttu-id="7be10-116">サポートされるホスト アプリケーション</span><span class="sxs-lookup"><span data-stu-id="7be10-116">Supported host applications</span></span>

- [<span data-ttu-id="7be10-117">Excel</span><span class="sxs-lookup"><span data-stu-id="7be10-117">Excel</span></span>](overview/excel-add-ins-reference-overview.md)
- [<span data-ttu-id="7be10-118">OneNote</span><span class="sxs-lookup"><span data-stu-id="7be10-118">OneNote</span></span>](overview/onenote-add-ins-javascript-reference.md)
- [<span data-ttu-id="7be10-119">Outlook</span><span class="sxs-lookup"><span data-stu-id="7be10-119">Outlook</span></span>](requirement-sets/outlook-api-requirement-sets.md)
- [<span data-ttu-id="7be10-120">Visio</span><span class="sxs-lookup"><span data-stu-id="7be10-120">Visio</span></span>](overview/visio-javascript-reference-overview.md)
- [<span data-ttu-id="7be10-121">Word</span><span class="sxs-lookup"><span data-stu-id="7be10-121">Word</span></span>](overview/word-add-ins-reference-overview.md)
- [<span data-ttu-id="7be10-122">共有 API</span><span class="sxs-lookup"><span data-stu-id="7be10-122">Shared API</span></span>](requirement-sets/office-add-in-requirement-sets.md)

> [!NOTE] 
> <span data-ttu-id="7be10-123">[PowerPoint および Project ](requirement-sets/powerpoint-and-project-note.md)は、JavaScript API で作成されたアドインをサポートします。</span><span class="sxs-lookup"><span data-stu-id="7be10-123">[PowerPoint and Project](requirement-sets/powerpoint-and-project-note.md) support add-ins made with the JavaScript API.</span></span> <span data-ttu-id="7be10-124">ただし、現在、PowerPoint と Project にはホスト固有の API がありません。</span><span class="sxs-lookup"><span data-stu-id="7be10-124">However, they currently do not have host-specific APIs.</span></span> <span data-ttu-id="7be10-125">共有 API を介して、これらのホストと対話します。</span><span class="sxs-lookup"><span data-stu-id="7be10-125">You interact with these hosts through the Shared API.</span></span>

<span data-ttu-id="7be10-126">[サポートされるホストとその他の要件](https://docs.microsoft.com/office/dev/add-ins/concepts/requirements-for-running-office-add-ins)の詳細を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7be10-126">Learn more about [supported hosts and other requirements](https://docs.microsoft.com/office/dev/add-ins/concepts/requirements-for-running-office-add-ins).</span></span>

## <a name="open-api-specifications"></a><span data-ttu-id="7be10-127">Open API の仕様</span><span class="sxs-lookup"><span data-stu-id="7be10-127">Open API specifications</span></span>

<span data-ttu-id="7be10-p106">Office アドイン用の新しい API の設計と開発にあたり、[Open API の仕様](openspec.md)ページでこれらに関するフィードバックを提供できるようになります。パイプラインの新機能をご確認いただき、設計の仕様に関する情報をお寄せください。</span><span class="sxs-lookup"><span data-stu-id="7be10-p106">As we design and develop new APIs for Office Add-ins, we'll make them available for your feedback on our [Open API specifications](openspec.md) page. Find out what new features are in the pipeline, and provide your input on our design specifications.</span></span>

## <a name="see-also"></a><span data-ttu-id="7be10-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="7be10-130">See also</span></span>

- [<span data-ttu-id="7be10-131">Office JavaScript API のリファレンス</span><span class="sxs-lookup"><span data-stu-id="7be10-131">JavaScript API for Office reference</span></span>](https://docs.microsoft.com/javascript/api/overview/office?view=office-js)