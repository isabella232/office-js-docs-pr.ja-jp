
# <a name="mailbox"></a>mailbox

### [Office](Office.md)[.context](Office.context.md). mailbox

Microsoft Outlook と Microsoft Outlook on the web の Outlook アドイン オブジェクト モデルへのアクセスを提供します。

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0以降|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| 制限あり|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="members-and-methods"></a>メンバーとメソッド

| メンバー | 種類 |
|--------|------|
| [ewsUrl](#ewsurl-string) | メンバー |
| [restUrl](#resturl-string) | メンバー |
| [addHandlerAsync](#addhandlerasynceventtype-handler-options-callback) | メソッド |
| [convertToEwsId](#converttoewsiditemid-restversion--string) | メソッド |
| [convertToLocalClientTime](#converttolocalclienttimetimevalue--localclienttimejavascriptapioutlook16officelocalclienttime) | メソッド |
| [convertToRestId](#converttorestiditemid-restversion--string) | メソッド |
| [convertToUtcClientTime](#converttoutcclienttimeinput--date) | メソッド |
| [displayAppointmentForm](#displayappointmentformitemid) | メソッド |
| [displayMessageForm](#displaymessageformitemid) | メソッド |
| [displayNewAppointmentForm](#displaynewappointmentformparameters) | メソッド |
| [displayNewMessageForm](#displaynewmessageformparameters) | メソッド |
| [getCallbackTokenAsync](#getcallbacktokenasyncoptions-callback) | メソッド |
| [getCallbackTokenAsync](#getcallbacktokenasynccallback-usercontext) | メソッド |
| [getUserIdentityTokenAsync](#getuseridentitytokenasynccallback-usercontext) | メソッド |
| [makeEwsRequestAsync](#makeewsrequestasyncdata-callback-usercontext) | メソッド |

### <a name="namespaces"></a>名前空間

[diagnostics](Office.context.mailbox.diagnostics.md): Outlook アドインに診断情報を提供します。

[item](Office.context.mailbox.item.md):Outlook アドインのメッセージや予定にアクセスするためのメソッドとプロパティを提供します。

[userProfile](Office.context.mailbox.userProfile.md):Outlook アドインのユーザーに関する情報を提供します。

### <a name="members"></a>メンバー

#### <a name="ewsurl-string"></a>ewsUrl: 文字列

このメール アカウントの Exchange Web サービス (EWS) エンドポイントの URL を取得します。閲覧モードのみです。

> [!NOTE]
> このメンバーは、Outlook for iOS または Outlook for Android ではサポートされていません。

`ewsUrl` 値は、リモート サービスで、ユーザーのメールボックスに EWS 呼び出しを行うために使用することができます。たとえば、[選択した項目から添付ファイルを取得する](https://docs.microsoft.com/outlook/add-ins/get-attachments-of-an-outlook-item)ためにリモート サービスを作成できます。

閲覧モードで `ewsUrl` メンバーを呼び出すには、アプリでマニフェスト内に **ReadItem** アクセス許可を指定する必要があります。

新規作成モードでは、[`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback)メソッドを呼び出してから、`ewsUrl`メンバーを使用する必要があります。アプリには、`saveAsync`メソッドを呼び出す **ReadWriteItem** アクセス許可が必要です。

##### <a name="type"></a>種類:

*   文字列

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0以降|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

#### <a name="resturl-string"></a>restUrl: 文字列

この電子メール アカウントの REST エンドポイントの URL を取得します。

`restUrl` 値は、ユーザーのメールボックスに [REST API](https://docs.microsoft.com/outlook/rest/) 呼び出しを行うために使用することができます。

閲覧モードで `restUrl` メンバーを呼び出すには、アプリでマニフェスト内に **ReadItem** アクセス許可を指定する必要があります。

新規作成モードでは、[`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback)メソッドを呼び出してから、`restUrl`メンバーを使用する必要があります。アプリには、`saveAsync`メソッドを呼び出す **ReadWriteItem** アクセス許可が必要です。

##### <a name="type"></a>種類:

*   文字列

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.5 |
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

### <a name="methods"></a>メソッド

####  <a name="addhandlerasynceventtype-handler-options-callback"></a>addHandlerAsync(eventType, handler, [options], [callback])

サポートされているイベントのイベント ハンドラーを追加します。

現在サポートされている唯一のイベントの種類は `Office.EventType.ItemChanged` です。これはユーザーが新しいアイテムを選択したときに呼び出されます。このイベントは、ピン留め可能な作業ウィンドウを実装するアドインで使用され、現在選択されているアイテムに基づいて作業ウィンドウ UI をアドインで更新できるようにします。

##### <a name="parameters"></a>パラメータ :

| 名前 | 種類 | 属性 | 説明 |
|---|---|---|---|
| `eventType` | [Office.EventType](office.md#eventtype-string) || ハンドラを呼び出す必要のあるイベント。 |
| `handler` | 関数 || イベントを処理する関数。この関数は、オブジェクト リテラルである単一パラメータを受け入れる必要があります。パラメータの `type` プロパティは、`addHandlerAsync` に渡される `eventType` パラメータと一致します。 |
| `options` | オブジェクト | &lt;任意&gt; | 次のプロパティのうち 1 つ以上を含むオブジェクト リテラルです。 |
| `options.asyncContext` | オブジェクト | &lt;任意&gt; | 開発者は、コールバック メソッドでアクセスしたい任意のオブジェクトを提供できます。 |
| `callback` | 関数| &lt;任意&gt;|メソッドが完了すると、`callback` パラメータに渡された関数が、単一パラメータ `asyncResult` で呼び出されます。これは、[`AsyncResult`](/javascript/api/office/office.asyncresult) オブジェクトです。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.5 |
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem |
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="example"></a>例

```
Office.initialize = function (reason) {
  $(document).ready(function () {
    Office.context.mailbox.addHandlerAsync(Office.EventType.ItemChanged, loadNewItem, function (result) {
      if (result.status === Office.AsyncResultStatus.Failed) {
        // Handle error
      }
    });
  });
};

function loadNewItem(eventArgs) {
  // Load the properties of the newly selected item
  loadProps(Office.context.mailbox.item);
};
```

####  <a name="converttoewsiditemid-restversion--string"></a>convertToEwsId(itemId, restVersion) → {String}

REST 用に書式設定された項目 ID を EWS 形式に変換します。

> [!NOTE]
> このメソッドは、Outlook for iOS または Outlook for Android ではサポートされていません。

REST API ([Outlook Mail API](https://docs.microsoft.com/previous-versions/office/office-365-api/api/version-2.0/mail-rest-operations) や [Microsoft Graph](http://graph.microsoft.io/) など) 経由で取得された項目 ID は、Exchange Web サービス (EWS) で使用される形式とは異なる形式を使用します。`convertToEwsId` メソッドは、REST 形式の ID を EWS 用の適切な形式に変換します。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 説明|
|---|---|---|
|`itemId`| 文字列|Outlook REST API 用に書式設定された項目 ID|
|`restVersion`| [Office.MailboxEnums.RestVersion](/javascript/api/outlook_1_6/office.mailboxenums.restversion)|項目 ID の取得に使用された Outlook REST API のバージョンを示す値。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.3|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| 制限あり|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="returns"></a>戻り値 :

種類: 文字列

##### <a name="example"></a>例

```
// Get an item's ID from a REST API
var restId = 'AAMkAGVlOTZjNTM3LW...';

// Treat restId as coming from the v2.0 version of the
// Outlook Mail API
var ewsId = Office.context.mailbox.convertToEwsId(restId, Office.MailboxEnums.RestVersion.v2_0);
```

####  <a name="converttolocalclienttimetimevalue--localclienttimejavascriptapioutlook16officelocalclienttime"></a>convertToLocalClientTime(timeValue) → {[LocalClientTime](/javascript/api/outlook_1_6/office.LocalClientTime)}

クライアントの現地時間の時間情報が含まれている辞書を取得します。

Outlook 用メール アプリや Outlook Web App で使う日付と時刻は、異なるタイム ゾーンを使うことができます。Outlook では、クライアント コンピューターのタイム ゾーンを使います。Outlook Web App では、Exchange 管理センター (EAC) で設定されたタイム ゾーンを使います。ユーザー インターフェイスに表示される値が、常にユーザーが期待するタイム ゾーンと一致するように日付と時刻の値を処理する必要があります。

Outlook でメール アプリが実行されている場合、`convertToLocalClientTime` メソッドは、クライアント コンピューターのタイム ゾーンに設定された値で辞書オブジェクトを返します。Outlook Web Apps でメール アプリが実行されている場合、`convertToLocalClientTime` メソッドは、EAC で指定されたタイム ゾーンに設定された値で辞書オブジェクトを返します。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 説明|
|---|---|---|
|`timeValue`| 日付|Date オブジェクト|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0以降|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="returns"></a>戻り値 :

種類:[LocalClientTime](/javascript/api/outlook_1_6/office.LocalClientTime)

####  <a name="converttorestiditemid-restversion--string"></a>convertToRestId(itemId, restVersion) → {String}

EWS 用に書式設定された項目 ID を REST 形式に変換します。

> [!NOTE]
> このメソッドは、Outlook for iOS または Outlook for Android ではサポートされていません。

EWS 経由または `itemId` プロパティ経由で取得される項目 ID では、REST API ([Outlook Mail API](https://docs.microsoft.com/previous-versions/office/office-365-api/api/version-2.0/mail-rest-operations) または [Microsoft Graph](http://graph.microsoft.io/) など) で使用される形式とは異なる形式を使用します。`convertToRestId` メソッドは、EWS 形式の ID を REST 用の適切な形式に変換します。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 説明|
|---|---|---|
|`itemId`| 文字列|Exchange Web サービス (EWS) 用に書式設定された項目 ID|
|`restVersion`| [Office.MailboxEnums.RestVersion](/javascript/api/outlook_1_6/office.mailboxenums.restversion)|変換後の ID とともに使用される Outlook REST API のバージョンを示す値。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.3|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| 制限あり|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="returns"></a>戻り値 :

種類: 文字列

##### <a name="example"></a>例

```
// Get the currently selected item's ID
var ewsId = Office.context.mailbox.item.itemId;

// Convert to a REST ID for the v2.0 version of the
// Outlook Mail API
var restId = Office.context.mailbox.convertToRestId(ewsId, Office.MailboxEnums.RestVersion.v2_0);
```

####  <a name="converttoutcclienttimeinput--date"></a>convertToUtcClientTime(input) → {Date}

時間情報が含まれている辞書から Date オブジェクトを取得します。

`convertToUtcClientTime` メソッドは、ローカルの日付と時刻が含まれる辞書を、ローカルの日付と時刻の正しい値をもつ Date オブジェクトに変換します。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 説明|
|---|---|---|
|`input`| [LocalClientTime](/javascript/api/outlook_1_6/office.LocalClientTime)|変換するローカル時刻の値。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0以降|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="returns"></a>戻り値 :

時間が UTC で表現された Date オブジェクト。

<dl class="param-type">

<dt>種類</dt>

<dd>日付</dd>

</dl>

####  <a name="displayappointmentformitemid"></a>displayAppointmentForm(itemId)

既存の予定表の予定を表示します。

> [!NOTE]
> このメソッドは、Outlook for iOS または Outlook for Android ではサポートされていません。

`displayAppointmentForm` メソッドは、デスクトップ上の新しいウィンドウまたはモバイル デバイス上のダイアログ ボックスで、既存の予定表の予定を開きます。

Outlook for Mac では、このメソッドを使用して、定期的に繰り返される予定の一部ではない単発の予定、または定期的に繰り替えされる予定の元の予定を表示できます。ただし、一連の予定のインスタンスは表示できません。これは、Outlook for Mac では、定期的に繰り返されるインスタンスのプロパティ  (項目 ID を含む) にアクセスできないためです。

Outlook Web App では、このメソッドで、指定されたフォームの本文が 32 KB 以下の文字数の場合に、そのフォームを開きます。

指定した項目識別子が既存の予定を識別しない場合には、クライアント コンピュータまたはデバイスで空白のウィンドウが開き、エラー メッセージは返されません。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 説明|
|---|---|---|
|`itemId`| 文字列|既存の予定表の予定の Exchange Web サービス (EWS) 識別子。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0以降|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="example"></a>例

```
Office.context.mailbox.displayAppointmentForm(appointmentId);
```

####  <a name="displaymessageformitemid"></a>displayMessageForm(itemId)

既存のメッセージを表示します。

> [!NOTE]
> このメソッドは、Outlook for iOS または Outlook for Android ではサポートされていません。

`displayMessageForm` メソッドは、デスクトップ上の新しいウィンドウまたはモバイル デバイス上のダイアログ ボックスで既存のメッセージを開きます。

Outlook Web App では、このメソッドは、指定されたフォームの本文が 32 KB 以下の文字数の場合に、そのフォームを開きます。

指定した項目識別子が既存のメッセージを識別しない場合には、クラアント コンピュータでメッセージは表示されず、エラー メッセージは返されません。

予定を表す `itemId` が含まれる `displayMessageForm` を使用しないでください。`displayAppointmentForm` メソッドを使用して既存の予定を表示し、`displayNewAppointmentForm` を使用して新しい予定を作成するフォームを表示します。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 説明|
|---|---|---|
|`itemId`| 文字列|既存のメッセージの Exchange Web サービス(EWS) 識別子。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0以降|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="example"></a>例

```
Office.context.mailbox.displayMessageForm(messageId);
```

#### <a name="displaynewappointmentformparameters"></a>displayNewAppointmentForm(parameters)

新しい予定表の予定を作成するためのフォームを表示します。

> [!NOTE]
> このメソッドは、Outlook for iOS または Outlook for Android ではサポートされていません。

`displayNewAppointmentForm` メソッドを使用すると、ユーザーが新しい予定または会議を作成できるフォームが開きます。パラメータを指定すると、予定のフォーム フィールドにパラメータの内容が自動的に入力されます。

Outlook Web App および OWA for Devices では、このメソッドは出席者フィールドが含まれるフォームを常に表示します。入力因数として出席者を指定しない場合には、このメソッドは [**保存**] ボタンのあるフォームを表示します。出席者を指定した場合には、フォームにはその出席者と [**送信**] ボタンが含まれます。

Outlook リッチ クライアントおよび Outlook RT では、`requiredAttendees`、`optionalAttendees` または `resources` パラメータに出席者またはリソースを指定した場合、このメソッドは [**送信**] ボタンがある会議フォームを表示します。受信者を指定しない場合には、このメソッドは [**保存して閉じる**] ボタンがある予定フォームを表示します。

パラメータのいずれかが指定されたサイズ制限を超えた場合、または不明なパラメータ名が指定された場合には、例外がスローされます。

##### <a name="parameters"></a>パラメータ :

> [!NOTE]
> すべてのパラメータは省略可能です。

|名前| 種類| 説明|
|---|---|---|
| `parameters` | オブジェクト | 新しい予定を記述するパラメータの辞書。 |
| `parameters.requiredAttendees` | 配列。&lt;文字列&gt; | 配列。&lt;[EmailAddressDetails](/javascript/api/outlook_1_6/office.emailaddressdetails)&gt; | 予定への各必須出席者の電子メール アドレスを含む文字列の配列、または出席者の `EmailAddressDetails` オブジェクトを含む配列。この配列は、最大 100 エントリまでに制限されています。 |
| `parameters.optionalAttendees` | 配列。&lt;文字列&gt; | 配列。&lt;[EmailAddressDetails](/javascript/api/outlook_1_6/office.emailaddressdetails)&gt; | 予定への各任意出席者の電子メール アドレスを含む文字列の配列、または出席者の `EmailAddressDetails` オブジェクトを含む配列。この配列は、最大 100 エントリまでに制限されています。 |
| `parameters.start` | 日付 | 予定の開始日時を指定する `Date` オブジェクト。 |
| `parameters.end` | 日付 | 予定の終了日時を指定する `Date` オブジェクト。 |
| `parameters.location` | 文字列 | 予定の場所を含む文字列。文字列は最大 255 文字までに制限されています。 |
| `parameters.resources` | 配列。&lt; 文字列&gt; | 予定に必要なリソースを含む文字列の配列。配列は最大 100 エントリまでに制限されています。 |
| `parameters.subject` | 文字列 | 予定の件名を含む文字列。文字列は最大 255 文字までに制限されています。 |
| `parameters.body` | 文字列 | 予定の本文。本文の内容は、最大サイズが 32 KB までに制限されています。 |

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0以降|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 読み取り|

##### <a name="example"></a>例

```
var start = new Date();
var end = new Date();
end.setHours(start.getHours() + 1);

Office.context.mailbox.displayNewAppointmentForm(
  {
    requiredAttendees: ['bob@contoso.com'],
    optionalAttendees: ['sam@contoso.com'],
    start: start,
    end: end,
    location: 'Home',
    resources: ['projector@contoso.com'],
    subject: 'meeting',
    body: 'Hello World!'
  });
```

#### <a name="displaynewmessageformparameters"></a>displayNewMessageForm(parameters)

新しいメッセージを作成するためのフォームを表示します。

`displayNewMessageForm` メソッドは、ユーザーが新しいメッセージを作成できるフォームを開きます。 パラメータを指定すると、メッセージ フォーム フィールドにはパラメータのコンテンツが自動的に入力されます。

パラメータのいずれかが指定されたサイズ制限を超えた場合、または不明なパラメータ名が指定された場合には、例外がスローされます。

##### <a name="parameters"></a>パラメータ :

> [!NOTE]
> すべてのパラメータは省略可能です。

|名前| 種類| 説明|
|---|---|---|
| `parameters` | オブジェクト | 新しいメッセージを記述するパラメータの辞書。 |
| `parameters.toRecipients` | 配列。&lt;文字列&gt; | 配列。&lt;[EmailAddressDetails](/javascript/api/outlook_1_6/office.emailaddressdetails)&gt; | 電子メール アドレスを含む文字列の配列、または To 行の各受信者の `EmailAddressDetails` オブジェクトを含む配列。 配列の上限は 100 エントリです。 |
| `parameters.ccRecipients` | 配列。&lt;文字列&gt; | 配列。&lt;[EmailAddressDetails](/javascript/api/outlook_1_6/office.emailaddressdetails)&gt; | 電子メール アドレスを含む文字列の配列、または Cc 行の各受信者の `EmailAddressDetails` オブジェクトを含む配列。 配列の上限は 100 エントリです。 |
| `parameters.bccRecipients` | 配列。&lt;文字列&gt; | 配列。&lt;[EmailAddressDetails](/javascript/api/outlook_1_6/office.emailaddressdetails)&gt; | 電子メール アドレスを含む文字列の配列、または Bcc 行の各受信者の `EmailAddressDetails` オブジェクトを含む配列。 配列の上限は 100 エントリです。 |
| `parameters.subject` | 文字列 | メッセージの件名を含む文字列。 文字列は最大 255 文字に制限されます。 |
| `parameters.htmlBody` | 文字列 | メッセージの HTML 本文。 本文の内容は、最大サイズが 32 KB に制限されます。 |
| `parameters.attachments` | 配列。&lt;オブジェクト&gt; | 添付ファイルまたは添付アイテムである JSON オブジェクトの配列。 |
| `parameters.attachments.type` | 文字列 | 添付ファイルの種類を示します。添付ファイルの場合は`file`、添付項目の場合は`item`でなければなりません。 |
| `parameters.attachments.name` | 文字列 | 添付ファイル名を含む文字列で、255 文字以内で入力が可能です。|
| `parameters.attachments.url` | 文字列 | `type`が`file`に設定されている場合にのみ使用されます。ファイルの場所の URIです。 |
| `parameters.attachments.isInline` | ブール値 | `type`が`file`に設定されている場合にのみ使用されます。`true`の場合、添付ファイルがインラインでメッセージ本文に表示され、添付ファイル一覧に表示されないことを示します。 |
| `parameters.attachments.itemId` | 文字列 | `type` が `item` に設定されている場合にのみ使用されます。 新しいメッセージに添付する、既存の電子メールの EWS 項目の id です。 最長 100 文字の文字列です。 |


##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.6 |
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 読み取り|

##### <a name="example"></a>例

```
Office.context.mailbox.displayNewMessageForm(
  {
    toRecipients: Office.context.mailbox.item.to, // Copy the To line from current item
    ccRecipients: ['sam@contoso.com'],
    subject: 'Outlook add-ins are cool!',
    htmlBody: 'Hello <b>World</b>!<br/><img src="cid:image.png"></i>',
    attachments: [
      {
        type: 'file',
        name: 'image.png',
        url: 'http://contoso.com/image.png',
        isInline: true
      }
    ]
  });
```

#### <a name="getcallbacktokenasyncoptions-callback"></a>getCallbackTokenAsync([options], callback)

REST API または Exchange Web サービスを呼び出すために使用するトークンを含む文字列を取得します。

`getCallbackTokenAsync` メソッドは、非同期の呼び出しを行なって、ユーザーのメールボックスをホストする Exchange Server から opaque トークンを取得します。コールバック トークンの有効期間は 5 分です。

> [!NOTE]
> 可能な場合は常に、アドインでは Exchange Web サービスの代わりに REST API を使用することをお勧めします。 

**REST トークン**

REST トークンが要求された場合 (`options.isRest = true`) には、作成されたトークンは Exchange Web サービスの呼び出しを認証するためには機能しません。このトークンは、アドインがマニフェストで [`ReadWriteMailbox`](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions#readwritemailbox-permission) アクセス許可を指定しない限り、現在の項目およびその添付ファイルへの読み取り専用の範囲に制限されます。`ReadWriteMailbox` アクセス許可が指定された場合には、作成されるトークンは、メールを送信する機能など、メール、予定表、連絡先への読み取り/書き込みアクセスを付与します。

アドインでは、`restUrl`プロパティを使用して、REST API 呼び出しを行うときに使用する正しい URL を決定する必要があります。

**EWS トークン**

EWS トークンが要求された場合(`options.isRest = false`) には、作成されるトークンは REST API の呼び出しを認証するためには機能しません。このトークンは、現在の項目にアクセスできる範囲に制限されます。

アドインでは、`ewsUrl` プロパティを使用して、EWS 呼び出しを行うときに使用する正しい URL を決定する必要があります。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 属性| 説明|
|---|---|---|---|
| `options` | オブジェクト | &lt;オプション&gt; | 次のプロパティのうち 1 つ以上を含むオブジェクト リテラルです。 |
| `options.isRest` | ブール値 |  &lt;任意&gt; | 提供されたトークンを Outlook REST API または Exchange Web サービスに使用するかどうかを決定します。既定値は、`false`です。 |
| `options.asyncContext` | オブジェクト |  &lt;任意&gt; | 非同期メソッドに渡される状態データです。 |
|`callback`| 関数||メソッドが完了すると、`callback` パラメータに渡された関数が、単一パラメータ `asyncResult` で呼び出されます。このパラメータは、[`AsyncResult`](/javascript/api/office/office.asyncresult) オブジェクトです。トークンは、`asyncResult.value` プロパティで文字列として提供されます。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.5 |
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 新規作成と閲覧|

##### <a name="example"></a>例

```js
function getCallbackToken() {
  var options = {
    isRest: true,
    asyncContext: { message: 'Hello World!' }
  };

  Office.context.mailbox.getCallbackTokenAsync(options, cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

#### <a name="getcallbacktokenasynccallback-usercontext"></a>getCallbackTokenAsync(callback, [userContext])

Exchange Server から添付ファイルやアイテムを取得するために使用するトークンを含む文字列を取得します。

`getCallbackTokenAsync` メソッドは、非同期の呼び出しを行なって、ユーザーのメールボックスをホストする Exchange Server から opaque トークンを取得します。コールバック トークンの有効期間は 5 分です。

このトークンと、添付ファイル識別子または項目識別子は、サードパーティーのシステムに渡すことができます。サードパーティーのシステムでは、添付ファイルまたは項目を返すための Exchange Web サービス (EWS) の [GetAttachment](https://docs.microsoft.com/exchange/client-developer/web-service-reference/getattachment-operation) または [GetItem](https://docs.microsoft.com/exchange/client-developer/web-service-reference/getitem-operation) 操作を呼び出すのに、トークンをベアラー承認トークンとして使用します。たとえば、リモート サービスを作成して[選択した項目から添付ファイルを取得](https://docs.microsoft.com/outlook/add-ins/get-attachments-of-an-outlook-item)することができます。

アプリでは、閲覧モードで `getCallbackTokenAsync` メソッドを呼び出すために、 **ReadItem** アクセス許可をアプリのマニフェストで指定する必要があります。

新規作成モードでは、[`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) メソッドを呼び出して、`getCallbackTokenAsync` メソッドに渡すための項目識別子を取得する必要があります。アプリには、`saveAsync` メソッドを呼び出すために **ReadWriteItem** アクセス許可が必要です。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 属性| 説明|
|---|---|---|---|
|`callback`| 関数||メソッドが完了すると、`callback` パラメータに渡された関数が、単一パラメータ `asyncResult` で呼び出されます。このパラメータは、[`AsyncResult`](/javascript/api/office/office.asyncresult) オブジェクトです。トークンは、`asyncResult.value` プロパティで文字列として提供されます。|
|`userContext`| オブジェクト| &lt;任意&gt;|非同期メソッドに渡される状態データです。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.3|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 新規作成と閲覧|

##### <a name="example"></a>例

```js
function getCallbackToken() {
  Office.context.mailbox.getCallbackTokenAsync(cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

####  <a name="getuseridentitytokenasynccallback-usercontext"></a>getUserIdentityTokenAsync(callback, [userContext])

ユーザーと Office アドインを識別するトークンを取得します。

`getUserIdentityTokenAsync` メソッドは、[アドインとユーザーをサードパーティのシステムで識別して認証](https://docs.microsoft.com/outlook/add-ins/authentication)するのに使用できるトークンを返します。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 属性| 説明|
|---|---|---|---|
|`callback`| 関数||メソッドが完了すると、`callback` パラメータに渡された関数が、単一パラメータ `asyncResult` で呼び出されます。これは、[`AsyncResult`](/javascript/api/office/office.asyncresult) オブジェクトです。<br/><br/>トークンは、`asyncResult.value`プロパティで文字列として提供されます。|
|`userContext`| オブジェクト| &lt;任意&gt;|非同期メソッドに渡される状態データです。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0以降|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="example"></a>例

```js
function getIdentityToken() {
  Office.context.mailbox.getUserIdentityTokenAsync(cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

####  <a name="makeewsrequestasyncdata-callback-usercontext"></a>makeEwsRequestAsync(data, callback, [userContext])

ユーザーのメールボックスをホストしている Exchange Server上の Exchange Web サービス (EWS) のサービスに対して非同期の要求を行います。

> [!NOTE]
> このメソッドは、次のシナリオではサポートされていません。
> - Outlook for iOS または Outlook for Android で
> - アドインが Gmail のメールボックスにロードされる場合
> 
> これらの場合、アドインではユーザーのメールボックスにアクセスするために、代わりに [REST API を使用する](https://docs.microsoft.com/outlook/add-ins/use-rest-api)必要があります。

`makeEwsRequestAsync` メソッドは、アドインの代わりに Exchange に EWS 要求を送信します。 サポートされている EWS 操作の一覧については、 「[ Outlook アドインから Web サービスを呼び出す](https://docs.microsoft.com/outlook/add-ins/web-services#ews-operations-that-add-ins-support)」を参照してください。

`makeEwsRequestAsync` メソッドで、フォルダー関連アイテムを要求することはできません。

XML 要求では、UTF-8 エンコードを指定する必要があります。

```
<?xml version="1.0" encoding="utf-8"?>
```

アドインには、`makeEwsRequestAsync` メソッドを使用するために **ReadWriteMailbox** アクセス許可が必要です。**ReadWriteMailbox** アクセス許可と、`makeEwsRequestAsync` メソッドで呼び出すことのできる EWS 操作の使用の詳細については、「[ユーザーのメールボックスへのメール アドイン アクセスのアクセス許可を指定する](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)」を参照してください。

> [!NOTE]
> サーバー管理者は、クライアント アクセス サーバー の EWS ディレクトリ上で `OAuthAuthentication` を true に設定して、`makeEwsRequestAsync` メソッドで EWS 要求を行えるようにする必要があります。

##### <a name="version-differences"></a>バージョンの相違点

バージョン 15.0.4535.1004 より前のバージョンの Outlook で実行しているメール アプリで `makeEwsRequestAsync` メソッドを使用する場合には、エンコード値を `ISO-8859-1` に設定する必要があります。

```
<?xml version="1.0" encoding="iso-8859-1"?>
```

メール アプリが Outlook on the web で実行されている場合には、エンコード値を設定する必要はありません。メールボックスを使用してメール アプリが Outlook で実行されているのか、Outlook on the web で実行されているのかを判断する必要があります。mailbox.diagnostics.hostVersion プロパティを使用すれば、どのバージョンの Outlook が実行されているのかがわかります。

##### <a name="parameters"></a>パラメータ :

|名前| 種類| 属性| 説明|
|---|---|---|---|
|`data`| 文字列||EWS 要求。|
|`callback`| 関数||メソッドが完了すると、`callback` パラメータで渡された関数が、単一パラメータ `asyncResult` で呼び出されます。このパラメータは、[`AsyncResult`](/javascript/api/office/office.asyncresult) オブジェクトです。<br/><br/>EWS 呼び出しの XML 結果は、`asyncResult.value` プロパティで文字列として提供されます。 結果のサイズが 1 MB を超えている場合、エラー メッセージが返されます。|
|`userContext`| オブジェクト| &lt;任意&gt;|非同期メソッドに渡される状態データです。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0以降|
|[最小限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadWriteMailbox|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 作成または読み取り|

##### <a name="example"></a>例

次の例は、`makeEwsRequestAsync` を呼び出し、`GetItem` 操作を使って項目の件名を取得します。

```js
function getSubjectRequest(id) {
   // Return a GetItem operation request for the subject of the specified item.
   var request =
    '<?xml version="1.0" encoding="utf-8"?>' +
    '<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"' +
    '               xmlns:xsd="http://www.w3.org/2001/XMLSchema"' +
    '               xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"' +
    '               xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types">' +
    '  <soap:Header>' +
    '    <RequestServerVersion Version="Exchange2013" xmlns="http://schemas.microsoft.com/exchange/services/2006/types" soap:mustUnderstand="0" />' +
    '  </soap:Header>' +
    '  <soap:Body>' +
    '    <GetItem xmlns="http://schemas.microsoft.com/exchange/services/2006/messages">' +
    '      <ItemShape>' +
    '        <t:BaseShape>IdOnly</t:BaseShape>' +
    '        <t:AdditionalProperties>' +
    '            <t:FieldURI FieldURI="item:Subject"/>' +
    '        </t:AdditionalProperties>' +
    '      </ItemShape>' +
    '      <ItemIds><t:ItemId Id="' + id + '"/></ItemIds>' +
    '    </GetItem>' +
    '  </soap:Body>' +
    '</soap:Envelope>';

   return request;
}

function sendRequest() {
   // Create a local variable that contains the mailbox.
   Office.context.mailbox.makeEwsRequestAsync(
    getSubjectRequest(mailbox.item.itemId), callback);
}

function callback(asyncResult)  {
   var result = asyncResult.value;
   var context = asyncResult.asyncContext;

   // Process the returned response here.
}
```