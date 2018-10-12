
# <a name="diagnostics"></a><span data-ttu-id="5328e-101">診断</span><span class="sxs-lookup"><span data-stu-id="5328e-101">diagnostics</span></span>

### <span data-ttu-id="5328e-p101">[Office](Office.md)[.context](Office.context.md)[.mailbox](Office.context.mailbox.md).diagnostics</span><span class="sxs-lookup"><span data-stu-id="5328e-p101">[Office](Office.md)[.context](Office.context.md)[.mailbox](Office.context.mailbox.md). diagnostics</span></span>

<span data-ttu-id="5328e-104">Outlook アドインに診断情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5328e-104">Provides diagnostic information to an Outlook add-in.</span></span>

##### <a name="requirements"></a><span data-ttu-id="5328e-105">要件</span><span class="sxs-lookup"><span data-stu-id="5328e-105">Requirements</span></span>

|<span data-ttu-id="5328e-106">要件</span><span class="sxs-lookup"><span data-stu-id="5328e-106">Requirement</span></span>| <span data-ttu-id="5328e-107">値</span><span class="sxs-lookup"><span data-stu-id="5328e-107">Value</span></span>|
|---|---|
|[<span data-ttu-id="5328e-108">メールボックス要件セットの最小バージョン</span><span class="sxs-lookup"><span data-stu-id="5328e-108">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="5328e-109">1.0</span><span class="sxs-lookup"><span data-stu-id="5328e-109">1.0</span></span>|
|[<span data-ttu-id="5328e-110">最小限のアクセス許可レベル</span><span class="sxs-lookup"><span data-stu-id="5328e-110">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="5328e-111">ReadItem</span><span class="sxs-lookup"><span data-stu-id="5328e-111">ReadItem</span></span>|
|[<span data-ttu-id="5328e-112">適用可能な Outlook のモード</span><span class="sxs-lookup"><span data-stu-id="5328e-112">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="5328e-113">作成または読み取り</span><span class="sxs-lookup"><span data-stu-id="5328e-113">Compose or read</span></span>|

##### <a name="members-and-methods"></a><span data-ttu-id="5328e-114">メンバーとメソッド</span><span class="sxs-lookup"><span data-stu-id="5328e-114">Members and methods</span></span>

| <span data-ttu-id="5328e-115">メンバー</span><span class="sxs-lookup"><span data-stu-id="5328e-115">Member</span></span> | <span data-ttu-id="5328e-116">型</span><span class="sxs-lookup"><span data-stu-id="5328e-116">Type</span></span> |
|--------|------|
| [<span data-ttu-id="5328e-117">ホスト名</span><span class="sxs-lookup"><span data-stu-id="5328e-117">hostName</span></span>](#hostname-string) | <span data-ttu-id="5328e-118">メンバー</span><span class="sxs-lookup"><span data-stu-id="5328e-118">Member</span></span> |
| [<span data-ttu-id="5328e-119">ホストバージョン</span><span class="sxs-lookup"><span data-stu-id="5328e-119">hostVersion</span></span>](#hostversion-string) | <span data-ttu-id="5328e-120">メンバー</span><span class="sxs-lookup"><span data-stu-id="5328e-120">Member</span></span> |
| [<span data-ttu-id="5328e-121">OWAView</span><span class="sxs-lookup"><span data-stu-id="5328e-121">OWAView</span></span>](#owaview-string) | <span data-ttu-id="5328e-122">メンバー</span><span class="sxs-lookup"><span data-stu-id="5328e-122">Member</span></span> |

### <a name="members"></a><span data-ttu-id="5328e-123">メンバー</span><span class="sxs-lookup"><span data-stu-id="5328e-123">Members</span></span>

####  <a name="hostname-string"></a><span data-ttu-id="5328e-124">ホスト名: 文字列</span><span class="sxs-lookup"><span data-stu-id="5328e-124">hostName :String</span></span>

<span data-ttu-id="5328e-125">ホスト アプリケーションの名前を表す文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="5328e-125">Gets a string that represents the name of the host application.</span></span>

<span data-ttu-id="5328e-126">文字列は、値 `Outlook`、`Mac Outlook`、`OutlookIOS`、または `OutlookWebApp` のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="5328e-126">A string that can be one of the following values: `Outlook`, `Mac Outlook`, `OutlookIOS`, or `OutlookWebApp`.</span></span>

##### <a name="type"></a><span data-ttu-id="5328e-127">型:</span><span class="sxs-lookup"><span data-stu-id="5328e-127">Type:</span></span>

*   <span data-ttu-id="5328e-128">文字列</span><span class="sxs-lookup"><span data-stu-id="5328e-128">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="5328e-129">要件</span><span class="sxs-lookup"><span data-stu-id="5328e-129">Requirements</span></span>

|<span data-ttu-id="5328e-130">要件</span><span class="sxs-lookup"><span data-stu-id="5328e-130">Requirement</span></span>| <span data-ttu-id="5328e-131">値</span><span class="sxs-lookup"><span data-stu-id="5328e-131">Value</span></span>|
|---|---|
|[<span data-ttu-id="5328e-132">メールボックス要件セットの最小バージョン</span><span class="sxs-lookup"><span data-stu-id="5328e-132">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="5328e-133">1.0</span><span class="sxs-lookup"><span data-stu-id="5328e-133">1.0</span></span>|
|[<span data-ttu-id="5328e-134">最小限のアクセス許可レベル</span><span class="sxs-lookup"><span data-stu-id="5328e-134">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="5328e-135">ReadItem</span><span class="sxs-lookup"><span data-stu-id="5328e-135">ReadItem</span></span>|
|[<span data-ttu-id="5328e-136">適用可能な Outlook のモード</span><span class="sxs-lookup"><span data-stu-id="5328e-136">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="5328e-137">作成または読み取り</span><span class="sxs-lookup"><span data-stu-id="5328e-137">Compose or read</span></span>|

####  <a name="hostversion-string"></a><span data-ttu-id="5328e-138">hostVersion: 文字列</span><span class="sxs-lookup"><span data-stu-id="5328e-138">hostVersion :String</span></span>

<span data-ttu-id="5328e-139">ホスト アプリケーションまたは Exchange Server のバージョンを表す文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="5328e-139">Gets a string that represents the version of either the host application or the Exchange Server.</span></span>

<span data-ttu-id="5328e-p102">メール アドインを Outlook デスクトップ クライアントまたは Outlook for iOS で実行している場合、`hostVersion` プロパティは、ホスト アプリケーションである Outlook のバージョンを返します。Outlook Web App では、プロパティは、Exchange Server のバージョンを返します。たとえば、文字列 `15.0.468.0` です。</span><span class="sxs-lookup"><span data-stu-id="5328e-p102">If the mail add-in is running on the Outlook desktop client or Outlook for iOS, the `hostVersion` property returns the version of the host application, Outlook. In Outlook Web App, the property returns the version of the Exchange Server. An example is the string `15.0.468.0`.</span></span>

##### <a name="type"></a><span data-ttu-id="5328e-143">型:</span><span class="sxs-lookup"><span data-stu-id="5328e-143">Type:</span></span>

*   <span data-ttu-id="5328e-144">文字列</span><span class="sxs-lookup"><span data-stu-id="5328e-144">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="5328e-145">要件</span><span class="sxs-lookup"><span data-stu-id="5328e-145">Requirements</span></span>

|<span data-ttu-id="5328e-146">要件</span><span class="sxs-lookup"><span data-stu-id="5328e-146">Requirement</span></span>| <span data-ttu-id="5328e-147">値</span><span class="sxs-lookup"><span data-stu-id="5328e-147">Value</span></span>|
|---|---|
|[<span data-ttu-id="5328e-148">メールボックス要件セットの最小バージョン</span><span class="sxs-lookup"><span data-stu-id="5328e-148">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="5328e-149">1.0</span><span class="sxs-lookup"><span data-stu-id="5328e-149">1.0</span></span>|
|[<span data-ttu-id="5328e-150">最小限のアクセス許可レベル</span><span class="sxs-lookup"><span data-stu-id="5328e-150">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="5328e-151">ReadItem</span><span class="sxs-lookup"><span data-stu-id="5328e-151">ReadItem</span></span>|
|[<span data-ttu-id="5328e-152">適用可能な Outlook のモード</span><span class="sxs-lookup"><span data-stu-id="5328e-152">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="5328e-153">作成または読み取り</span><span class="sxs-lookup"><span data-stu-id="5328e-153">Compose or read</span></span>|

####  <a name="owaview-string"></a><span data-ttu-id="5328e-154">OWAView: 文字列</span><span class="sxs-lookup"><span data-stu-id="5328e-154">OWAView :String</span></span>

<span data-ttu-id="5328e-155">Outlook Web App の現在のビューを表す文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="5328e-155">Gets a string that represents the current view of Outlook Web App.</span></span>

<span data-ttu-id="5328e-156">返される文字列は、値 `OneColumn`、`TwoColumns`、または `ThreeColumns` のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="5328e-156">The returned string can be one of the following values: `OneColumn`, `TwoColumns`, or `ThreeColumns`.</span></span>

<span data-ttu-id="5328e-157">ホスト アプリケーションが Outlook Web App ではない場合、このプロパティへのアクセスは `undefined` となります。</span><span class="sxs-lookup"><span data-stu-id="5328e-157">If the host application is not Outlook Web App, then accessing this property results in `undefined`.</span></span>

<span data-ttu-id="5328e-158">Outlook Web App には、画面とウィンドウの幅、および表示可能な列数に応じて 3 つのビューがあります。</span><span class="sxs-lookup"><span data-stu-id="5328e-158">Outlook Web App has three views that correspond to the width of the screen and the window, and the number of columns that can be displayed:</span></span>

*   <span data-ttu-id="5328e-p103">`OneColumn`これは、画面の幅が狭い場合に表示されます。Outlook Web App は、このシングル コラム レイアウトを使用してスマートフォンの画面全体に表示します。</span><span class="sxs-lookup"><span data-stu-id="5328e-p103">`OneColumn`, which is displayed when the screen is narrow. Outlook Web App uses this single-column layout on the entire screen of a smartphone.</span></span>
*   <span data-ttu-id="5328e-p104">`TwoColumns`画面幅がやや広い場合に表示される 。Outlook Web App は、ほとんどのタブレットでこのビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="5328e-p104">`TwoColumns`, which is displayed when the screen is wider. Outlook Web App uses this view on most tablets.</span></span>
*   <span data-ttu-id="5328e-p105">`ThreeColumns`画面幅が広い場合に表示される 。Outlook Web App は、デスクトップ コンピューターのフル スクリーン ウィンドウなどでこのビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="5328e-p105">`ThreeColumns`, which is displayed when the screen is wide. For example, Outlook Web App uses this view in a full screen window on a desktop computer.</span></span>

##### <a name="type"></a><span data-ttu-id="5328e-165">型:</span><span class="sxs-lookup"><span data-stu-id="5328e-165">Type:</span></span>

*   <span data-ttu-id="5328e-166">文字列</span><span class="sxs-lookup"><span data-stu-id="5328e-166">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="5328e-167">要件</span><span class="sxs-lookup"><span data-stu-id="5328e-167">Requirements</span></span>

|<span data-ttu-id="5328e-168">要件</span><span class="sxs-lookup"><span data-stu-id="5328e-168">Requirement</span></span>| <span data-ttu-id="5328e-169">値</span><span class="sxs-lookup"><span data-stu-id="5328e-169">Value</span></span>|
|---|---|
|[<span data-ttu-id="5328e-170">メールボックス要件セットの最小バージョン</span><span class="sxs-lookup"><span data-stu-id="5328e-170">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="5328e-171">1.0</span><span class="sxs-lookup"><span data-stu-id="5328e-171">1.0</span></span>|
|[<span data-ttu-id="5328e-172">最小限のアクセス許可レベル</span><span class="sxs-lookup"><span data-stu-id="5328e-172">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="5328e-173">ReadItem</span><span class="sxs-lookup"><span data-stu-id="5328e-173">ReadItem</span></span>|
|[<span data-ttu-id="5328e-174">適用可能な Outlook のモード</span><span class="sxs-lookup"><span data-stu-id="5328e-174">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="5328e-175">作成または読み取り</span><span class="sxs-lookup"><span data-stu-id="5328e-175">Compose or read</span></span>|