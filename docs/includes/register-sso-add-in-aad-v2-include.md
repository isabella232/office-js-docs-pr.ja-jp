

1. [Azure ポータル - アプリの登録](https://go.microsoft.com/fwlink/?linkid=2083908)ページに移動してアプリを登録します。

1. Microsoft 365 テナントに対して ***管理者*** の資格情報を使用してサインインします。 たとえば、MyName@contoso.onmicrosoft.com です。

1. **[新規登録]** を選択します。 **[アプリケーションを登録]** ページで、次のように値を設定します。

    * **名前**を **$ADD-IN-NAME$** に設定します。
    * **[サポートされているアカウントの種類]** を **[任意の組織のディレクトリ内のアカウントと個人用の Microsoft アカウント (例: Skype、 Xbox、Outlook.com)]** に設定します。
    * **[リダイレクト URI]** を空のままにします。
    * **[登録]** を選択します。

1. **$ADD-IN-NAME$** ページで、**アプリケーション (クライアント) ID**と**ディレクトリ (テナント) ID**の値をコピーして保存します。 以降の手順では、それらの両方を使用します。

    > [!NOTE]
    > この ID は、Office クライアントアプリケーション (PowerPoint、Word、Excel など) などの他のアプリケーションがアプリケーションへの承認されたアクセスをシークするときの、"対象ユーザー" の値です。 また、そのアプリケーションが Microsoft Graph への承認されたアクセスを求めるときには、このアプリケーションの「クライアント ID」になります。

1. **[管理]** で **[証明書とシークレット]** を選択します。 **[新しいクライアント シークレット]** ボタンを選択します。 **[説明]** に値を入力してから、**[有効期限]** に適切なオプションを選択し、**[追加]** を選択します。 *クライアント シークレットの値をすぐにコピーして、後の手順で必要になるため、先に進む前にアプリケーションIDと一緒に保存*してください。

1. **[管理]** の下の **[API の公開]** を選択します。 **[設定]** リンクを選択して、「api://$App ID GUID$」の形式でアプリケーション ID URIを生成します。 ダブル スラッシュと GUID の間に **$FQDN-WITHOUT-PROTOCOL$** (末尾にスラッシュ "/" を付けて) を挿入します。 全体の ID は `api://$FQDN-WITHOUT-PROTOCOL$/$App ID GUID$` の形式になります。例: `api://localhost:6789/c6c1f32b-5e55-4997-881a-753cc1d563b7`。

    > [!NOTE]
    > この時点で「アプリケーション ID の URI は、HTTPS、API、URN MS APPX で始まる有効な URI である必要があります。スラッシュで終わってはいけません。」という 不正確なエラーが発生する可能性があります。 ID が規定の条件を満たしている場合は、エラーを無視して変更を保存してください。

    > [!NOTE]
    > ドメインを所有しているにもかかわらず、そのドメインが既に所有されているというエラーが表示される場合は、「[クイック スタート: カスタム ドメイン名を Azure Active Directory に追加する](/azure/active-directory/add-custom-domain)」の手順に従って登録し、この手順を繰り返します。 このエラーは、Microsoft 365 テナントの管理者の資格情報を使用してサインインしていない場合にも発生する可能性があります。 手順 2 を参照してください。 サインアウトして、管理者の資格情報を使用して再度サインインし、手順 3 からプロセスを繰り返します。)

1. **[Scope の追加]** ボタンをクリックします。 開いたパネルで、**[スコープ名]** として `access_as_user` を入力します。

1. **[同意できるのはだれですか?]** を **[管理者とユーザー]** に設定します。

1. ユーザーが `access_as_user` 現在のユーザーと同じ権限で Office クライアントアプリケーションでアドインの Web api を使用できるようにするには、[管理者] と [ユーザーの同意] を構成するためのフィールドに必要な値を入力します。 提案:

    - **管理者の同意のタイトル:** Office はユーザーとして機能できます。
    - **管理者の同意の説明:** 現在のユーザーと同じ権限で Office がアドインの Web API を呼び出すことを可能にします。
    - **ユーザーの同意のタイトル:** Office は自分として機能できます。
    - **管理者の同意の説明:** 自分と同じ権限で Office がアドインの Web API を呼び出すことを可能にします。

1. **[状態]** が **[有効]** に設定されていることを確認してください。

1. **[スコープの追加]** を選択します。

    > [!NOTE]
    > テキスト フィールドのすぐ下に表示される **[スコープ名]** のドメイン部分は、たとえば `api://localhost:6789/c6c1f32b-5e55-4997-881a-753cc1d563b7/access_as_user` のように手順で設定された **[アプリケーション ID URI]** と自動的に一致し、最後に `/access_as_user` が追加されます。

1. **[承認済みのクライアント アプリケーション]** セクションで、アドインの Web アプリケーションに対して承認するアプリケーションを特定します。 次のそれぞれの ID を事前承認する必要があります。
  
    * `d3590ed6-52b3-4102-aeff-aad2292ab01c` (Microsoft Office)
    * `ea5a67f6-b6f3-4338-b240-c655ddc3cc8e` (Microsoft Office)
    * `57fb890c-0dab-4253-a5e0-7188c88b2bb4` (Office on the web)
    * `08e18876-6177-487e-b8b5-cf950c1e598c` (Office on the web)
    * `bc59ab01-8403-45c6-8796-ac3ef710b3e3` (Outlook on the web)

    ID ごとに、次の手順を実行します。

      a. **[クライアント アプリケーションの追加]** ボタンを選択し、表示されたパネルで **[クライアント ID]** をそれぞれの GUID に設定して `api://$FQDN-WITHOUT-PROTOCOL$/$App ID GUID$/access_as_user` のチェック ボックスをオンにします。

      b. **[アプリケーションの追加]** を選択します。

1. **[管理]** の下の **[認証]** を選択します。 **[リダイレクト URI]** セクションの **[種類]** ドロップダウンで **[Web]** を選択し、**[リダイレクト URI]** の値を `https://$FQDN-WITHOUT-PROTOCOL$` に設定します。

1. フォームの最上部で **[保存]** を選択します。

1. **[管理]** の下の **[API アクセス許可]** を選択し、**[アクセス許可の追加]** を選択します。 開いたパネルで、**[Microsoft Graph]** を選択してから **[委任されたアクセス許可]** を選択します。

1. アドインに必要な権限を検索するには、**[アクセス許可を選択]** の検索ボックスを使用します。 次に例を示します。

    * Files.Read.All
    * offline_access
    * openid
    * profile

    > [!NOTE]
    > `User.Read` アクセス許可は既定でリストされています。 必要でないアクセス許可は依頼しない方がよいため、アドインが実際に必要でない場合は、このアクセス許可のボックスのチェックをオフにしておくことをお勧めします。

1. 表示された各権限のチェック ボックスをオンにします (各権限を選択しても、権限は一覧に表示されたままにはなりません)。 アドインに必要な権限を選択したら、パネルの下部にある **[アクセス許可を追加する]** ボタンをクリックします。
