# <a name="extensionpoint-element"></a><span data-ttu-id="61c78-101">ExtensionPoint 要素</span><span class="sxs-lookup"><span data-stu-id="61c78-101">ExtensionPoint element</span></span>

 <span data-ttu-id="61c78-102">Office UI でアドインが機能を公開する場所を定義します。</span><span class="sxs-lookup"><span data-stu-id="61c78-102">Defines where an add-in exposes functionality in the Office UI.</span></span> <span data-ttu-id="61c78-103">**ExtensionPoint** 要素は、[AllFormFactors](allformfactors.md)、[DesktopFormFactor](desktopformfactor.md)、[MobileFormFactor](mobileformfactor.md) の子要素です。</span><span class="sxs-lookup"><span data-stu-id="61c78-103">The **ExtensionPoint** element is a child element of [AllFormFactors](allformfactors.md), [DesktopFormFactor](desktopformfactor.md) or [MobileFormFactor](mobileformfactor.md).</span></span> 

## <a name="attributes"></a><span data-ttu-id="61c78-104">属性</span><span class="sxs-lookup"><span data-stu-id="61c78-104">Attributes</span></span>

|  <span data-ttu-id="61c78-105">属性</span><span class="sxs-lookup"><span data-stu-id="61c78-105">Attribute</span></span>  |  <span data-ttu-id="61c78-106">必須</span><span class="sxs-lookup"><span data-stu-id="61c78-106">Required</span></span>  |  <span data-ttu-id="61c78-107">説明</span><span class="sxs-lookup"><span data-stu-id="61c78-107">Description</span></span>  |
|:-----|:-----|:-----|
|  <span data-ttu-id="61c78-108">**xsi:type**</span><span class="sxs-lookup"><span data-stu-id="61c78-108">**xsi:type**</span></span>  |  <span data-ttu-id="61c78-109">はい</span><span class="sxs-lookup"><span data-stu-id="61c78-109">Yes</span></span>  | <span data-ttu-id="61c78-110">定義される拡張点の種類。</span><span class="sxs-lookup"><span data-stu-id="61c78-110">The type of extension point being defined.</span></span>|

## <a name="extension-points-for-excel-only"></a><span data-ttu-id="61c78-111">Excel のみの拡張点</span><span class="sxs-lookup"><span data-stu-id="61c78-111">Extension points for Excel only</span></span>

- <span data-ttu-id="61c78-112">**CustomFunctions** - Excel 向けの JavaScript で記述されたカスタム関数。</span><span class="sxs-lookup"><span data-stu-id="61c78-112">**CustomFunctions** - a custom function written in JavaScript for Excel.</span></span>

<span data-ttu-id="61c78-113">[この XML コードのサンプル](https://github.com/OfficeDev/Excel-Custom-Functions/blob/master/customfunctions.xml) では、 **CustomFunctions** 属性値とともに**ExtensionPoint** 要素を使用する方法と、使用する子要素を示します。</span><span class="sxs-lookup"><span data-stu-id="61c78-113">The following examples show how to use the ExtensionPoint element with the CustomFunctions attribute value, and the child elements to be used.</span></span>

## <a name="extension-points-for-word-excel-powerpoint-and-onenote-add-in-commands"></a><span data-ttu-id="61c78-114">Word、Excel、PowerPoint、OneNote アドイン コマンドの拡張点</span><span class="sxs-lookup"><span data-stu-id="61c78-114">Extension points for Word, Excel, PowerPoint, and OneNote add-in commands</span></span>

- <span data-ttu-id="61c78-115">**PrimaryCommandSurface** - Office のリボン。</span><span class="sxs-lookup"><span data-stu-id="61c78-115">**PrimaryCommandSurface** - The ribbon in Office.</span></span>
- <span data-ttu-id="61c78-116">**ContextMenu**- Office UI で右クリックしたときに表示されるショートカット メニュー。</span><span class="sxs-lookup"><span data-stu-id="61c78-116">**ContextMenu** - The shortcut menu that appears when you right-click in the Office UI.</span></span>

<span data-ttu-id="61c78-117">次の例は、 **PrimaryCommandSurface** と **ContextMenu** の属性値を持つ **ExtensionPoint** 要素を使用する方法と、各要素と併用する必要がある子要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="61c78-117">The following examples show how to use the  **ExtensionPoint** element with **PrimaryCommandSurface** and **ContextMenu** attribute values, and the child elements that should be used with each.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="61c78-118">ID 属性を含む要素では、一意の ID を指定してください。</span><span class="sxs-lookup"><span data-stu-id="61c78-118">IMPORTANT  For elements that contain an ID attribute, make sure you provide a unique ID.</span></span> <span data-ttu-id="61c78-119">あなたの ID と共に、会社の名前を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61c78-119">We recommend that you use your company's name along with your ID.</span></span> <span data-ttu-id="61c78-120">たとえば、次の形式にします。</span><span class="sxs-lookup"><span data-stu-id="61c78-120">For example, use the following format.</span></span> <CustomTab id="mycompanyname.mygroupname">

```XML
<ExtensionPoint xsi:type="PrimaryCommandSurface">
          <CustomTab id="Contoso Tab">
          <!-- If you want to use a default tab that comes with Office, remove the above CustomTab element, and then uncomment the following OfficeTab element -->
            <!-- <OfficeTab id="TabData"> -->
            <Label resid="residLabel4" />
            <Group id="Group1Id12">
              <Label resid="residLabel4" />
              <Icon>
                <bt:Image size="16" resid="icon1_32x32" />
                <bt:Image size="32" resid="icon1_32x32" />
                <bt:Image size="80" resid="icon1_32x32" />
              </Icon>
              <Tooltip resid="residToolTip" />
              <Control xsi:type="Button" id="Button1Id1">

                  <!-- information about the control -->
              </Control>
              <!-- other controls, as needed -->
            </Group>
          </CustomTab>
        </ExtensionPoint>

      <ExtensionPoint xsi:type="ContextMenu">
        <OfficeMenu id="ContextMenuCell">
          <Control xsi:type="Menu" id="ContextMenu2">
                  <!-- information about the control -->
          </Control>
          <!-- other controls, as needed -->
        </OfficeMenu>
        </ExtensionPoint>
```

#### <a name="child-elements"></a><span data-ttu-id="61c78-121">子要素</span><span class="sxs-lookup"><span data-stu-id="61c78-121">Child elements</span></span>
 
|<span data-ttu-id="61c78-122">**要素**</span><span class="sxs-lookup"><span data-stu-id="61c78-122">**Element**</span></span>|<span data-ttu-id="61c78-123">**説明**</span><span class="sxs-lookup"><span data-stu-id="61c78-123">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="61c78-124">**CustomTab**</span><span class="sxs-lookup"><span data-stu-id="61c78-124">**CustomTab**</span></span>|<span data-ttu-id="61c78-p103">カスタム タブをリボンに追加する場合は必須です (  **PrimaryCommandSurface** を使用)。 **CustomTab** 要素を使用する場合、 **OfficeTab** 要素は使用できません。 **id** 属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="61c78-p103">Required if you want to add a custom tab to the ribbon (using  **PrimaryCommandSurface**). If you use the  **CustomTab** element, you can't use the **OfficeTab** element. The **id** attribute is required.</span></span>|
|<span data-ttu-id="61c78-128">**OfficeTab**</span><span class="sxs-lookup"><span data-stu-id="61c78-128">**OfficeTab**</span></span>|<span data-ttu-id="61c78-p104">既定の Office リボン タブを拡張する場合は必須です (**PrimaryCommandSurface** を使用)。**OfficeTab** 要素を使用する場合、**CustomTab** 要素は使用できません。詳細については、「[OfficeTab](officetab.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61c78-p104">Required if you want to extend a default Office ribbon tab (using **PrimaryCommandSurface**). If you use the  **OfficeTab** element, you can't use the **CustomTab** element. For details, see [OfficeTab](officetab.md).</span></span>|
|<span data-ttu-id="61c78-132">**OfficeMenu**</span><span class="sxs-lookup"><span data-stu-id="61c78-132">**OfficeMenu**</span></span>|<span data-ttu-id="61c78-p105">既定のコンテキスト メニューにアドイン コマンドを追加する場合は必須です (**ContextMenu** を使用)。**id** 属性は以下に設定する必要があります。 </span><span class="sxs-lookup"><span data-stu-id="61c78-p105">Required if you're adding add-in commands to a default context menu (using  **ContextMenu**). The  **id** attribute must be set to: </span></span><br/> <span data-ttu-id="61c78-p106">- Excel または Word の \*\* ContextMenuText\*\* 。テキストが選択され、ユーザーが選択されたテキストを右クリックしたときに、コンテキスト メニューに項目が表示されます。 </span><span class="sxs-lookup"><span data-stu-id="61c78-p106">- **ContextMenuText** for Excel or Word. Displays the item on the context menu when text is selected and then the user right-clicks on the selected text. </span></span><br/> <span data-ttu-id="61c78-p107">- Excel の場合は **ContextMenuCell**。ユーザーがスプレッドシートのセルを右クリックすると、コンテキスト メニューに項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="61c78-p107">- **ContextMenuCell** for Excel. Displays the  item on the context menu when the user right-clicks on a cell on the spreadsheet.</span></span>|
|<span data-ttu-id="61c78-139">**グループ**</span><span class="sxs-lookup"><span data-stu-id="61c78-139">**Group**</span></span>|<span data-ttu-id="61c78-p108">タブのユーザー インターフェイスの拡張点のグループ。グループには、最大 6 個のコントロールを指定できます。 **id** 属性が必要です。id は最大 125 文字の文字列です。</span><span class="sxs-lookup"><span data-stu-id="61c78-p108">A group of user interface extension points on a tab. A group can have up to six controls. The  **id** attribute is required. It's a string with a maximum of 125 characters.</span></span>|
|<span data-ttu-id="61c78-143">**ラベル**</span><span class="sxs-lookup"><span data-stu-id="61c78-143">**Label**</span></span>|<span data-ttu-id="61c78-p109">必須。グループのラベル。 **resid** 属性は、 **String** 要素の **id** 属性の値に設定する必要があります。 **String** 要素は、 **Resources** 要素の子要素である **ShortStrings** 要素の子要素です。</span><span class="sxs-lookup"><span data-stu-id="61c78-p109">Required. The label of the group. The  **resid** attribute must be set to the value of the **id** attribute of a **String** element. The **String** element is a child element of the **ShortStrings** element, which is a child element of the **Resources** element.</span></span>|
|<span data-ttu-id="61c78-148">**アイコン**</span><span class="sxs-lookup"><span data-stu-id="61c78-148">**Icon**</span></span>|<span data-ttu-id="61c78-p110">必須。小型のフォーム ファクターのデバイス、または表示されるボタンが多すぎるときに使用されるグループのアイコンを指定します。 **resid** 属性は、 **Image** 要素の **id** 属性の値に設定する必要があります。 **Image** 要素は、 **Resources** 要素の子要素である **Images** 要素の子要素です。 **size** 属性は、イメージのサイズをピクセル単位で指定します。3 つのイメージのサイズ (16、32、80) が必要です。5 つのサイズ オプション (20、24、40、48、64) もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="61c78-p110">Required. Specifies the group's icon to be used on small form factor devices, or when too many buttons are displayed. The  **resid** attribute must be set to the value of the **id** attribute of an **Image** element. The **Image** element is a child element of the **Images** element, which is a child element of the **Resources** element. The **size** attribute gives the size, in pixels, of the image. Three image sizes are required: 16, 32, and 80. Five optional sizes are also supported: 20, 24, 40, 48, and 64.</span></span>|
|<span data-ttu-id="61c78-156">**ヒント**</span><span class="sxs-lookup"><span data-stu-id="61c78-156">**Tooltip**</span></span>|<span data-ttu-id="61c78-p111">省略可能。グループのツールヒント。 **resid** 属性は、 **String** 要素の **id** 属性の値に設定する必要があります。 **String** 要素は、 **Resources** 要素の子要素である **LongStrings** 要素の子要素です。</span><span class="sxs-lookup"><span data-stu-id="61c78-p111">Optional. The tooltip of the group. The  **resid** attribute must be set to the value of the **id** attribute of a **String** element. The **String** element is a child element of the **LongStrings** element, which is a child element of the **Resources** element.</span></span>|
|<span data-ttu-id="61c78-161">**コントロール**</span><span class="sxs-lookup"><span data-stu-id="61c78-161">**Control**</span></span>|<span data-ttu-id="61c78-162">各グループには、最低でもコントロールが一つ必要です。</span><span class="sxs-lookup"><span data-stu-id="61c78-162">Each group requires at least one control.</span></span> <span data-ttu-id="61c78-163"> *\*Control** 要素は、*\*Button** または *\*Menu** のどちらかになります。</span><span class="sxs-lookup"><span data-stu-id="61c78-163">A  **Control** element can be either a **Button** or a **Menu**.</span></span> <span data-ttu-id="61c78-164">ボタン コントロールのドロップダウン リストを指定する場合は、**Menu** を使用します。</span><span class="sxs-lookup"><span data-stu-id="61c78-164">Use  **Menu** to specify a drop-down list of button controls.</span></span> <span data-ttu-id="61c78-165">現在は、ボタンとメニューのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="61c78-165">Currently, only buttons and menus are supported.</span></span> <span data-ttu-id="61c78-166">詳細については、「[Button コントロール](control.md#button-control)」および「[Menu コントロール](control.md#menu-dropdown-button-controls)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="61c78-166">See the [Button controls](control.md#button-control) and [Menu controls](control.md#menu-dropdown-button-controls) sections for more information.</span></span><br/><span data-ttu-id="61c78-167">**注**  トラブルシューティングを簡単にするために、 **Control**  要素と関連する  **Resources**  子要素を一度に 1 つずつ追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61c78-167">**Note**  To make troubleshooting easier, we recommend that a  **Control** element and the related **Resources** child elements be added one at a time.</span></span>|
|<span data-ttu-id="61c78-168">**スクリプト**</span><span class="sxs-lookup"><span data-stu-id="61c78-168">**Script**</span></span>|<span data-ttu-id="61c78-169">カスタム関数の定義と登録コードを含む JavaScript ファイルにリンクします。</span><span class="sxs-lookup"><span data-stu-id="61c78-169">Links to the JavaScript file with the custom function definition and registration code.</span></span> <span data-ttu-id="61c78-170">Developer Preview では、この要素は使用しません。</span><span class="sxs-lookup"><span data-stu-id="61c78-170">This element is not used in the Developer Preview.</span></span> <span data-ttu-id="61c78-171">代わりに、HTML ページはすべての JavaScript ファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="61c78-171">Instead, the HTML page is responsible for loading all JavaScript files.</span></span>|
|<span data-ttu-id="61c78-172">**ページ**</span><span class="sxs-lookup"><span data-stu-id="61c78-172">**Page**</span></span>|<span data-ttu-id="61c78-173">カスタム関数についての HTML ページにリンクします。</span><span class="sxs-lookup"><span data-stu-id="61c78-173">Links to the HTML page for your custom functions.</span></span>|

## <a name="extension-points-for-outlook"></a><span data-ttu-id="61c78-174">Outlook の拡張ポイント</span><span class="sxs-lookup"><span data-stu-id="61c78-174">Extension points for Outlook add-in commands</span></span>

- [<span data-ttu-id="61c78-175">MessageReadCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-175">MessageReadCommandSurface</span></span>](#messagereadcommandsurface) 
- [<span data-ttu-id="61c78-176">MessageComposeCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-176">MessageComposeCommandSurface</span></span>](#messagecomposecommandsurface) 
- [<span data-ttu-id="61c78-177">AppointmentOrganizerCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-177">AppointmentOrganizerCommandSurface</span></span>](#appointmentorganizercommandsurface) 
- [<span data-ttu-id="61c78-178">AppointmentAttendeeCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-178">AppointmentAttendeeCommandSurface</span></span>](#appointmentattendeecommandsurface)
- <span data-ttu-id="61c78-179">[Module](#module) ([DesktopFormFactor](desktopformfactor.md) でのみ使用できます。)</span><span class="sxs-lookup"><span data-stu-id="61c78-179">[Module](#module) (Can only be used in the [DesktopFormFactor](desktopformfactor.md).)</span></span>
- [<span data-ttu-id="61c78-180">MobileMessageReadCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-180">MobileMessageReadCommandSurface</span></span>](#mobilemessagereadcommandsurface)
- [<span data-ttu-id="61c78-181">イベント</span><span class="sxs-lookup"><span data-stu-id="61c78-181">Events</span></span>](#events)
- [<span data-ttu-id="61c78-182">DetectedEntity</span><span class="sxs-lookup"><span data-stu-id="61c78-182">DetectedEntity</span></span>](#detectedentity)

### <a name="messagereadcommandsurface"></a><span data-ttu-id="61c78-183">MessageReadCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-183">MessageReadCommandSurface</span></span>
<span data-ttu-id="61c78-p114">この拡張点により、メールの閲覧ビューのコマンド サーフェスにボタンが配置されます。Outlook デスクトップでは、これはリボンに表示されます。</span><span class="sxs-lookup"><span data-stu-id="61c78-p114">This extension point puts buttons in the command surface for the mail read view. In Outlook desktop, this appears in the ribbon.</span></span>

#### <a name="child-elements"></a><span data-ttu-id="61c78-186">子要素</span><span class="sxs-lookup"><span data-stu-id="61c78-186">Child elements</span></span>

|  <span data-ttu-id="61c78-187">要素</span><span class="sxs-lookup"><span data-stu-id="61c78-187">Element</span></span> |  <span data-ttu-id="61c78-188">説明</span><span class="sxs-lookup"><span data-stu-id="61c78-188">Description</span></span>  |
|:-----|:-----|
|  [<span data-ttu-id="61c78-189">OfficeTab</span><span class="sxs-lookup"><span data-stu-id="61c78-189">OfficeTab</span></span>](officetab.md) |  <span data-ttu-id="61c78-190">コマンドを既定のリボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-190">Adds the command(s) to the default ribbon tab.</span></span>  |
|  [<span data-ttu-id="61c78-191">CustomTab</span><span class="sxs-lookup"><span data-stu-id="61c78-191">CustomTab</span></span>](customtab.md) |  <span data-ttu-id="61c78-192">コマンドをカスタム リボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-192">Adds the command(s) to the custom ribbon tab.</span></span>  |

#### <a name="officetab-example"></a><span data-ttu-id="61c78-193">OfficeTab の例</span><span class="sxs-lookup"><span data-stu-id="61c78-193">OfficeTab example</span></span>
```xml
<ExtensionPoint xsi:type="MessageReadCommandSurface">
  <OfficeTab id="TabDefault">
        <-- OfficeTab Definition -->
  </OfficeTab>
</ExtensionPoint>
```

#### <a name="customtab-example"></a><span data-ttu-id="61c78-194">CustomTab の例</span><span class="sxs-lookup"><span data-stu-id="61c78-194">CustomTab example</span></span>
```xml
<ExtensionPoint xsi:type="MessageReadCommandSurface">
  <CustomTab id="TabCustom1">
        <-- CustomTab Definition -->
  </CustomTab>
</ExtensionPoint>
```

### <a name="messagecomposecommandsurface"></a><span data-ttu-id="61c78-195">MessageComposeCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-195">MessageComposeCommandSurface</span></span>
<span data-ttu-id="61c78-196">この拡張点は、メールの新規作成フォームを使用してアドイン用のリボンにボタンを配置します。</span><span class="sxs-lookup"><span data-stu-id="61c78-196">This extension point puts buttons on the ribbon for add-ins using mail compose form.</span></span> 

#### <a name="child-elements"></a><span data-ttu-id="61c78-197">子要素</span><span class="sxs-lookup"><span data-stu-id="61c78-197">Child elements</span></span>

|  <span data-ttu-id="61c78-198">要素</span><span class="sxs-lookup"><span data-stu-id="61c78-198">Element</span></span> |  <span data-ttu-id="61c78-199">説明</span><span class="sxs-lookup"><span data-stu-id="61c78-199">Description</span></span>  |
|:-----|:-----|
|  [<span data-ttu-id="61c78-200">OfficeTab</span><span class="sxs-lookup"><span data-stu-id="61c78-200">OfficeTab</span></span>](officetab.md) |  <span data-ttu-id="61c78-201">コマンドを既定のリボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-201">Adds the command(s) to the default ribbon tab.</span></span>  |
|  [<span data-ttu-id="61c78-202">CustomTab</span><span class="sxs-lookup"><span data-stu-id="61c78-202">CustomTab</span></span>](customtab.md) |  <span data-ttu-id="61c78-203">コマンドをカスタム リボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-203">Adds the command(s) to the custom ribbon tab.</span></span>  |

#### <a name="officetab-example"></a><span data-ttu-id="61c78-204">OfficeTab の例</span><span class="sxs-lookup"><span data-stu-id="61c78-204">OfficeTab example</span></span>
```xml
<ExtensionPoint xsi:type="MessageComposeCommandSurface">
  <OfficeTab id="TabDefault">
        <-- OfficeTab Definition -->
  </OfficeTab>
</ExtensionPoint>
```

#### <a name="customtab-example"></a><span data-ttu-id="61c78-205">CustomTab の例</span><span class="sxs-lookup"><span data-stu-id="61c78-205">CustomTab example</span></span>

```xml
<ExtensionPoint xsi:type="MessageComposeCommandSurface">
  <CustomTab id="TabCustom1">
        <-- CustomTab Definition -->
  </CustomTab>
</ExtensionPoint>
```

### <a name="appointmentorganizercommandsurface"></a><span data-ttu-id="61c78-206">AppointmentOrganizerCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-206">AppointmentOrganizerCommandSurface</span></span>

<span data-ttu-id="61c78-207">この拡張点は、会議の開催者に表示されるフォームのリボンにボタンを配置します。</span><span class="sxs-lookup"><span data-stu-id="61c78-207">This extension point puts buttons on the ribbon for the form that's displayed to the organizer of the meeting.</span></span> 

#### <a name="child-elements"></a><span data-ttu-id="61c78-208">子要素</span><span class="sxs-lookup"><span data-stu-id="61c78-208">Child elements</span></span>

|  <span data-ttu-id="61c78-209">要素</span><span class="sxs-lookup"><span data-stu-id="61c78-209">Element</span></span> |  <span data-ttu-id="61c78-210">説明</span><span class="sxs-lookup"><span data-stu-id="61c78-210">Description</span></span>  |
|:-----|:-----|
|  [<span data-ttu-id="61c78-211">OfficeTab</span><span class="sxs-lookup"><span data-stu-id="61c78-211">OfficeTab</span></span>](officetab.md) |  <span data-ttu-id="61c78-212">コマンドを既定のリボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-212">Adds the command(s) to the default ribbon tab.</span></span>  |
|  [<span data-ttu-id="61c78-213">CustomTab</span><span class="sxs-lookup"><span data-stu-id="61c78-213">CustomTab</span></span>](customtab.md) |  <span data-ttu-id="61c78-214">コマンドをカスタム リボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-214">Adds the command(s) to the custom ribbon tab.</span></span>  |

#### <a name="officetab-example"></a><span data-ttu-id="61c78-215">OfficeTab の例</span><span class="sxs-lookup"><span data-stu-id="61c78-215">OfficeTab example</span></span>
```xml
<ExtensionPoint xsi:type="AppointmentOrganizerCommandSurface">
  <OfficeTab id="TabDefault">
        <-- OfficeTab Definition -->
  </OfficeTab>
</ExtensionPoint>
```

#### <a name="customtab-example"></a><span data-ttu-id="61c78-216">CustomTab の例</span><span class="sxs-lookup"><span data-stu-id="61c78-216">CustomTab example</span></span>
```xml
<ExtensionPoint xsi:type="AppointmentOrganizerCommandSurface">
  <CustomTab id="TabCustom1">
        <-- CustomTab Definition -->
  </CustomTab>
</ExtensionPoint>
```

### <a name="appointmentattendeecommandsurface"></a><span data-ttu-id="61c78-217">AppointmentAttendeeCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-217">AppointmentAttendeeCommandSurface</span></span>

<span data-ttu-id="61c78-218">この拡張点は、会議の出席者に表示されるフォームのリボンにボタンを配置します。</span><span class="sxs-lookup"><span data-stu-id="61c78-218">This extension point puts buttons on the ribbon for the form that's displayed to the attendee of the meeting.</span></span> 

#### <a name="child-elements"></a><span data-ttu-id="61c78-219">子要素</span><span class="sxs-lookup"><span data-stu-id="61c78-219">Child elements</span></span>

|  <span data-ttu-id="61c78-220">要素</span><span class="sxs-lookup"><span data-stu-id="61c78-220">Element</span></span> |  <span data-ttu-id="61c78-221">説明</span><span class="sxs-lookup"><span data-stu-id="61c78-221">Description</span></span>  |
|:-----|:-----|
|  [<span data-ttu-id="61c78-222">OfficeTab</span><span class="sxs-lookup"><span data-stu-id="61c78-222">OfficeTab</span></span>](officetab.md) |  <span data-ttu-id="61c78-223">コマンドを既定のリボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-223">Adds the command(s) to the default ribbon tab.</span></span>  |
|  [<span data-ttu-id="61c78-224">CustomTab</span><span class="sxs-lookup"><span data-stu-id="61c78-224">CustomTab</span></span>](customtab.md) |  <span data-ttu-id="61c78-225">コマンドをカスタム リボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-225">Adds the command(s) to the custom ribbon tab.</span></span>  |

#### <a name="officetab-example"></a><span data-ttu-id="61c78-226">OfficeTab の例</span><span class="sxs-lookup"><span data-stu-id="61c78-226">OfficeTab example</span></span>
```xml
<ExtensionPoint xsi:type="AppointmentAttendeeCommandSurface">
  <OfficeTab id="TabDefault">
        <-- OfficeTab Definition -->
  </OfficeTab>
</ExtensionPoint>
```

#### <a name="customtab-example"></a><span data-ttu-id="61c78-227">CustomTab の例</span><span class="sxs-lookup"><span data-stu-id="61c78-227">CustomTab example</span></span>
```xml
<ExtensionPoint xsi:type="AppointmentAttendeeCommandSurface">
  <CustomTab id="TabCustom1">
        <-- CustomTab Definition -->
  </CustomTab>
</ExtensionPoint>
```

### <a name="module"></a><span data-ttu-id="61c78-228">Module</span><span class="sxs-lookup"><span data-stu-id="61c78-228">Module</span></span>

<span data-ttu-id="61c78-229">この拡張点は、モジュール拡張機能用のリボンにボタンを配置します。</span><span class="sxs-lookup"><span data-stu-id="61c78-229">This extension point puts buttons on the ribbon for the module extension.</span></span> 

#### <a name="child-elements"></a><span data-ttu-id="61c78-230">子要素</span><span class="sxs-lookup"><span data-stu-id="61c78-230">Child elements</span></span>

|  <span data-ttu-id="61c78-231">要素</span><span class="sxs-lookup"><span data-stu-id="61c78-231">Element</span></span> |  <span data-ttu-id="61c78-232">説明</span><span class="sxs-lookup"><span data-stu-id="61c78-232">Description</span></span>  |
|:-----|:-----|
|  [<span data-ttu-id="61c78-233">OfficeTab</span><span class="sxs-lookup"><span data-stu-id="61c78-233">OfficeTab</span></span>](officetab.md) |  <span data-ttu-id="61c78-234">コマンドを既定のリボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-234">Adds the command(s) to the default ribbon tab.</span></span>  |
|  [<span data-ttu-id="61c78-235">CustomTab</span><span class="sxs-lookup"><span data-stu-id="61c78-235">CustomTab</span></span>](customtab.md) |  <span data-ttu-id="61c78-236">コマンドをカスタム リボン タブに追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-236">Adds the command(s) to the custom ribbon tab.</span></span>  |

### <a name="mobilemessagereadcommandsurface"></a><span data-ttu-id="61c78-237">MobileMessageReadCommandSurface</span><span class="sxs-lookup"><span data-stu-id="61c78-237">MobileMessageReadCommandSurface</span></span>
<span data-ttu-id="61c78-238">この拡張点により、モバイル フォーム ファクターのメールの閲覧ビューのコマンド領域にボタンが配置されます。</span><span class="sxs-lookup"><span data-stu-id="61c78-238">This extension point puts buttons in the command surface for the mail read view in the mobile form factor.</span></span>

#### <a name="child-elements"></a><span data-ttu-id="61c78-239">子要素</span><span class="sxs-lookup"><span data-stu-id="61c78-239">Child elements</span></span>

|  <span data-ttu-id="61c78-240">要素</span><span class="sxs-lookup"><span data-stu-id="61c78-240">Element</span></span> |  <span data-ttu-id="61c78-241">説明</span><span class="sxs-lookup"><span data-stu-id="61c78-241">Description</span></span>  |
|:-----|:-----|
|  [<span data-ttu-id="61c78-242">グループ</span><span class="sxs-lookup"><span data-stu-id="61c78-242">Group</span></span>](group.md) |  <span data-ttu-id="61c78-243">コマンド領域にボタングループを追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-243">Adds a group of buttons to the command surface.</span></span>  |

<span data-ttu-id="61c78-244">この種類の **ExtensionPoint** 要素は子要素を一つだけ含むことができます (**Group** 要素)。</span><span class="sxs-lookup"><span data-stu-id="61c78-244">**ExtensionPoint** elements of this type can only have one child element: a **Group** element.</span></span>

<span data-ttu-id="61c78-245">この拡張点に含まれる **Control** 要素の **xsi:type** 属性を `MobileButton` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c78-245">**Control** elements contained in this extension point must have the **xsi:type** attribute set to `MobileButton`.</span></span>

#### <a name="example"></a><span data-ttu-id="61c78-246">例</span><span class="sxs-lookup"><span data-stu-id="61c78-246">Example</span></span>
```xml
<ExtensionPoint xsi:type="MobileMessageReadCommandSurface">
  <Group id="mobileGroupID">
    <Label resid="residAppName"/>
      <Control id="mobileButton1" xsi:type="MobileButton">
        <!-- Control definition -->
      </Control>
  </Group>
</ExtensionPoint>
```

### <a name="events"></a><span data-ttu-id="61c78-247">イベント</span><span class="sxs-lookup"><span data-stu-id="61c78-247">Events</span></span>

<span data-ttu-id="61c78-248">この拡張点は、指定したイベントのイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-248">This extension point adds an event handler for a specified event.</span></span>

> [!NOTE]
> <span data-ttu-id="61c78-249">この要素は、Office 365 の Outlook on the web でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="61c78-249">Note: This element type is only supported by Outlook on the web in Office 365.</span></span>

| <span data-ttu-id="61c78-250">要素</span><span class="sxs-lookup"><span data-stu-id="61c78-250">Element</span></span> | <span data-ttu-id="61c78-251">説明</span><span class="sxs-lookup"><span data-stu-id="61c78-251">Description</span></span>  |
|:-----|:-----|
|  [<span data-ttu-id="61c78-252">イベント</span><span class="sxs-lookup"><span data-stu-id="61c78-252">Event</span></span>](event.md) |  <span data-ttu-id="61c78-253">イベントとイベント ハンドラーの関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="61c78-253">Specifies the event and event handler function.</span></span>  |

#### <a name="itemsend-event-example"></a><span data-ttu-id="61c78-254">ItemSend イベントの例</span><span class="sxs-lookup"><span data-stu-id="61c78-254">ItemSend event example</span></span>

```xml
<ExtensionPoint xsi:type="Events"> 
  <Event Type="ItemSend" FunctionExecution="synchronous" FunctionName="itemSendHandler" /> 
</ExtensionPoint> 
```

### <a name="detectedentity"></a><span data-ttu-id="61c78-255">DetectedEntity</span><span class="sxs-lookup"><span data-stu-id="61c78-255">DetectedEntity</span></span>

<span data-ttu-id="61c78-256">この拡張点は、指定したエンティティの種類に対するコンテキスト アドインのアクティブ化を追加します。</span><span class="sxs-lookup"><span data-stu-id="61c78-256">This extension point adds a contextual add-in activation on a specified entity type.</span></span>

<span data-ttu-id="61c78-257">これを収容している [VersionOverrides](versionoverrides.md) 要素は、`xsi:type` 属性の値が `VersionOverridesV1_1` になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c78-257">The containing [VersionOverrides](versionoverrides.md) element must have an `xsi:type` attribute value of `VersionOverridesV1_1`.</span></span>

> [!NOTE]
> <span data-ttu-id="61c78-258">この要素は、Office 365 の Outlook on the web でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="61c78-258">Note: This element type is only supported by Outlook on the web in Office 365.</span></span>

|  <span data-ttu-id="61c78-259">要素</span><span class="sxs-lookup"><span data-stu-id="61c78-259">Element</span></span> |  <span data-ttu-id="61c78-260">説明</span><span class="sxs-lookup"><span data-stu-id="61c78-260">Description</span></span>  |
|:-----|:-----|
|  [<span data-ttu-id="61c78-261">ラベル</span><span class="sxs-lookup"><span data-stu-id="61c78-261">Label</span></span>](#label) |  <span data-ttu-id="61c78-262">アドインのコンテキスト ウィンドウのラベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="61c78-262">Specifies the label for the add-in in the contextual window.</span></span>  |
|  [<span data-ttu-id="61c78-263">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="61c78-263">SourceLocation</span></span>](sourcelocation.md) |  <span data-ttu-id="61c78-264">コンテキスト ウィンドウの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="61c78-264">Specifies the URL for the contextual window.</span></span>  |
|  [<span data-ttu-id="61c78-265">ルール</span><span class="sxs-lookup"><span data-stu-id="61c78-265">Rule</span></span>](rule.md) |  <span data-ttu-id="61c78-266">アドインをアクティブ化するタイミングを決定するルールを一つ以上指定します。</span><span class="sxs-lookup"><span data-stu-id="61c78-266">Specifies the rule or rules that determine when an add-in activates.</span></span>  |

#### <a name="label"></a><span data-ttu-id="61c78-267">ラベル</span><span class="sxs-lookup"><span data-stu-id="61c78-267">Label</span></span>

<span data-ttu-id="61c78-p115">必須。グループのラベルです。**resid** 属性には、 **Resources** 要素の **ShortStrings** 要素にある **String** 要素の [id](resources.md) 属性の値を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c78-p115">Required. The label of the group. The  **resid** attribute must be set to the value of the **id** attribute of a **String** element in the **ShortStrings** element in the [Resources](resources.md) element.</span></span>

#### <a name="highlight-requirements"></a><span data-ttu-id="61c78-271">強調表示の要件</span><span class="sxs-lookup"><span data-stu-id="61c78-271">Highlight requirements</span></span>

<span data-ttu-id="61c78-p116">ユーザーは、強調表示されたエンティティに対話型の操作を実行する方法でのみコンテキスト アドインを有効化できます。開発者は、`ItemHasKnownEntity` および `ItemHasRegularExpressionMatch` のルールの種類に対応する `Rule` 要素の `Highlight` 属性を使用して、強調表示にするエンティティを制御します。</span><span class="sxs-lookup"><span data-stu-id="61c78-p116">The only way a user can activate a contextual add-in is to interact with a highlighted entity. Developers can control which entities are highlighted by using the `Highlight` attribute of the `Rule` element for `ItemHasKnownEntity` and `ItemHasRegularExpressionMatch` rule types.</span></span>

<span data-ttu-id="61c78-p117">ただし、注意する必要のある制限があります。これらの制限は、ユーザーにアドインをアクティブ化する方法を提供するために、適用可能なメッセージや予定で強調表示されたエンティティが常に存在するようにするために実施されます。</span><span class="sxs-lookup"><span data-stu-id="61c78-p117">However, there are some limitations to be aware of. These limitations are in place to ensure that there will always be a highlighted entity in applicable messages or appointments to give the user a way to activate the add-in.</span></span>

- <span data-ttu-id="61c78-276">`EmailAddress` および `Url` のエンティティの種類は、強調表示できません。そのため、アドインをアクティブ化するためには使用できません。</span><span class="sxs-lookup"><span data-stu-id="61c78-276">The `EmailAddress` and `Url` entity types cannot be highlighted, and therefore cannot be used to activate an add-in.</span></span>
- <span data-ttu-id="61c78-277">単一のルールを使用する場合、`Highlight` は `all` に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c78-277">If using a single rule, `Highlight` MUST be set to `all`.</span></span>
- <span data-ttu-id="61c78-278">複数のルールを組み合わせるために `Mode="AND"` で `RuleCollection` のルールの種類を使用する場合は、少なくとも 1 つのルールの `Highlight` が `all` に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c78-278">If using a `RuleCollection` rule type with `Mode="AND"` to combine multiple rules, at least one of the rules MUST have `Highlight` set to `all`.</span></span>
- <span data-ttu-id="61c78-279">複数のルールを組み合わせるために `Mode="OR"` で `RuleCollection` のルールの種類を使用する場合は、すべてのルールの `Highlight` が `all` に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c78-279">If using a `RuleCollection` rule type with `Mode="OR"` to combine multiple rules, all of the rules MUST have `Highlight` set to `all`.</span></span>

#### <a name="detectedentity-event-example"></a><span data-ttu-id="61c78-280">DetectedEntity イベントの例</span><span class="sxs-lookup"><span data-stu-id="61c78-280">DetectedEntity event example</span></span>

```xml
<ExtensionPoint xsi:type="DetectedEntity">
  <Label resid="residLabelName"/>
  <SourceLocation resid="residDetectedEntityURL" />
  <Rule xsi:type="RuleCollection" Mode="And">
    <Rule xsi:type="ItemIs" ItemType="Message" />
    <Rule xsi:type="ItemHasKnownEntity" EntityType="MeetingSuggestion" Highlight="all" />
    <Rule xsi:type="ItemHasKnownEntity" EntityType="Address" Highlight="none" />
  </Rule>
</ExtensionPoint> 
```