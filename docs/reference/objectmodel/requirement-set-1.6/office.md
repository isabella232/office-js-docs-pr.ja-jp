---
title: Office 名前空間-要件セット1.6
description: メールボックス API 要件セット1.6 を使用した Outlook アドインで使用可能な Office 名前空間メンバー。
ms.date: 03/18/2020
localization_priority: Normal
ms.openlocfilehash: 97b866a11ad96dbbbebdde6c5ed46c67406441fd
ms.sourcegitcommit: 83f9a2fdff81ca421cd23feea103b9b60895cab4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2020
ms.locfileid: "47431445"
---
# <a name="office-mailbox-requirement-set-16"></a>Office (メールボックス要件セット 1.6)

Office 名前空間は、すべての Office アプリケーションのアドインで使用される共有インターフェイスを提供します。この一覧は、Outlook のアドインで使うインターフェイスのみを記載しています。Office 名前空間の完全な一覧については、「[共通 API](/javascript/api/office)」を参照してください。

##### <a name="requirements"></a>Requirements

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](../../requirement-sets/outlook-api-requirement-sets.md)| 1.1|
|[適用可能な Outlook のモード](../../../outlook/outlook-add-ins-overview.md#extension-points)| 新規作成または閲覧|

##### <a name="properties"></a>プロパティ

| プロパティ | モード | 戻り値の種類 | 最小値<br>要件セット |
|---|---|---|:---:|
| [context](office.context.md) | 作成<br>読み取り | [Context](/javascript/api/office/office.context?view=outlook-js-1.6&preserve-view=true) | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |

##### <a name="enumerations"></a>列挙型

| 列挙体 | モード | 戻り値の種類 | 最小値<br>要件セット |
|---|---|---|:---:|
| [AsyncResultStatus](#asyncresultstatus-string) | 作成<br>読み取り | 文字列 | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [CoercionType](#coerciontype-string) | 作成<br>読み取り | 文字列 | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [EventType](#eventtype-string) | 作成<br>読み取り | 文字列 | [1.5](../requirement-set-1.5/outlook-requirement-set-1.5.md) |
| [SourceProperty](#sourceproperty-string) | 作成<br>読み取り | 文字列 | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |

### <a name="namespaces"></a>名前空間

[MailboxEnums](/javascript/api/outlook/office.mailboxenums.attachmentcontentformat?view=outlook-js-1.6&preserve-view=true):、、、、、など、多数の Outlook 固有の列挙を含み `ItemType` `EntityType` `AttachmentType` `RecipientType` `ResponseType` `ItemNotificationMessageType` ます。

## <a name="enumeration-details"></a>列挙の詳細

#### <a name="asyncresultstatus-string"></a>AsyncResultStatus: String

非同期呼び出しの結果を指定します。

##### <a name="type"></a>型

*   String

##### <a name="properties"></a>プロパティ:

|名前| 種類| 説明|
|---|---|---|
|`Succeeded`| 文字列|呼び出しが成功しました。|
|`Failed`| String|呼び出しが失敗しました。|

##### <a name="requirements"></a>Requirements

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](../../requirement-sets/outlook-api-requirement-sets.md)| 1.1|
|[適用可能な Outlook のモード](../../../outlook/outlook-add-ins-overview.md#extension-points)| 新規作成または閲覧|

<br>

---
---

#### <a name="coerciontype-string"></a>CoercionType: String

呼び出されたメソッドによって返される、または設定されるデータを強制的に変換する方法を指定します。

##### <a name="type"></a>型

*   String

##### <a name="properties"></a>プロパティ:

|名前| 種類| 説明|
|---|---|---|
|`Html`| 文字列|HTML 形式で返されるデータを要求します。|
|`Text`| String|テキスト形式で返されるデータを要求します。|

##### <a name="requirements"></a>Requirements

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](../../requirement-sets/outlook-api-requirement-sets.md)| 1.1|
|[適用可能な Outlook のモード](../../../outlook/outlook-add-ins-overview.md#extension-points)| 新規作成または閲覧|

<br>

---
---

#### <a name="eventtype-string"></a>EventType: String

イベント ハンドラーに関連付けられているイベントを指定します。

##### <a name="type"></a>型

*   String

##### <a name="properties"></a>プロパティ:

| 名前 | 種類 | 説明 | 最小要件セット |
|---|---|---|:---:|
|`ItemChanged`| 文字列 | 作業ウィンドウが固定されている間、別の Outlook アイテムが選択され、表示することができます。 | 1.5 |

##### <a name="requirements"></a>Requirements

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](../../requirement-sets/outlook-api-requirement-sets.md)| 1.5 |
|[適用可能な Outlook のモード](../../../outlook/outlook-add-ins-overview.md#extension-points)| 新規作成または閲覧 |

<br>

---
---

#### <a name="sourceproperty-string"></a>SourceProperty: String

呼び出されたメソッドによって返されるデータのソースを指定します。

##### <a name="type"></a>型

*   String

##### <a name="properties"></a>プロパティ:

|名前| 種類| 説明|
|---|---|---|
|`Body`| 文字列|データのソースは、メッセージの本文です。|
|`Subject`| String|データのソースは、メッセージの件名です。|

##### <a name="requirements"></a>Requirements

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](../../requirement-sets/outlook-api-requirement-sets.md)| 1.1|
|[適用可能な Outlook のモード](../../../outlook/outlook-add-ins-overview.md#extension-points)| 新規作成または閲覧|
