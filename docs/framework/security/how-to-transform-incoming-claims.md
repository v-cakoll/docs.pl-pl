---
title: 'Instrukcje: Przekształcanie oświadczeń przychodzących'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: ce99b97007bf7608856345d6da87cd9e422d2266
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041479"
---
# <a name="how-to-transform-incoming-claims"></a>Instrukcje: Przekształcanie oświadczeń przychodzących

## <a name="applies-to"></a>Dotyczy:

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>Podsumowanie

Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji opartej na oświadczeniach ASP.NET Web Forms i przekształcania oświadczeń przychodzących. Zawiera również instrukcje dotyczące testowania aplikacji, aby sprawdzić, czy po uruchomieniu aplikacji są prezentowane przekształcone oświadczenia.

## <a name="contents"></a>Spis treści

- Cele

- Omówienie

- Zestawienie czynności

- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms

- Krok 2 — implementowanie transformacji oświadczeń przy użyciu niestandardowego ClaimsAuthenticationManager

- Krok 3 — Przetestowanie rozwiązania

## <a name="objectives"></a>Cele

- Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach

- Przekształć oświadczenia przychodzące przez dodanie oświadczenia roli administratora

- Przetestuj aplikację ASP.NET Web Forms, aby sprawdzić, czy działa prawidłowo

## <a name="overview"></a>Omówienie

WIF uwidacznia klasę o nazwie <xref:System.Security.Claims.ClaimsAuthenticationManager> , która umożliwia użytkownikom modyfikowanie oświadczeń przed wyświetleniem ich w aplikacji jednostki uzależnionej (RP). <xref:System.Security.Claims.ClaimsAuthenticationManager> Jest to przydatne w przypadku rozdzielenia problemów między uwierzytelnianiem a podstawowym kodem aplikacji. W poniższym przykładzie pokazano, jak dodać rolę do oświadczeń w przychodzących <xref:System.Security.Claims.ClaimsPrincipal> , które mogą być wymagane przez RP.

## <a name="summary-of-steps"></a>Zestawienie czynności

- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms

- Krok 2 — implementowanie transformacji oświadczeń przy użyciu niestandardowego ClaimsAuthenticationManager

- Krok 3 — Przetestowanie rozwiązania

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms

W tym kroku utworzysz nową aplikację ASP.NET Web Forms.

#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET

1. Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.

2. W programie Visual Studio kliknij pozycję **plik**, kliknij pozycję **Nowy**, a następnie kliknij pozycję **projekt**.

3. W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.

4. W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.

5. Kliknij prawym przyciskiem myszy projekt **TestApp** w obszarze **Eksplorator rozwiązań**, a następnie wybierz pozycję **tożsamość i dostęp**.

6. Zostanie wyświetlone okno **tożsamość i dostęp** . W obszarze **dostawcy**wybierz pozycję **Testuj aplikację przy użyciu lokalnej usługi STS**, a następnie kliknij przycisk **Zastosuj**.

7. W pliku *default. aspx* Zastąp istniejący znacznik następującym zapisem, a następnie Zapisz plik:

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
          <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

8. Otwórz plik związany z kodem o nazwie *default.aspx.cs*. Zastąp istniejący kod następującym kodem, a następnie Zapisz plik:

    ```csharp
    using System;
    using System.Web.UI;
    using System.Security.Claims;

    namespace TestApp
    {
        public partial class _Default : Page
        {
            protected void Page_Load(object sender, EventArgs e)
            {
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                this.ClaimsGridView.DataBind();
            }
        }
    }
    ```

## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Krok 2 — implementowanie transformacji oświadczeń przy użyciu niestandardowego ClaimsAuthenticationManager

W tym kroku zastąpisz funkcję domyślną w <xref:System.Security.Claims.ClaimsAuthenticationManager> klasie w celu dodania roli administratora do przychodzącego podmiotu zabezpieczeń.

#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Aby zaimplementować transformację oświadczeń przy użyciu niestandardowego ClaimsAuthenticationManager

1. W programie Visual Studio kliknij prawym przyciskiem myszy na rozwiązaniu, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.

2. W oknie **Dodaj nowy projekt** wybierz pozycję **Biblioteka klas** z listy Szablony  **C# wizualizacji** , `ClaimsTransformation`a następnie naciśnij przycisk **OK**. Nowy projekt zostanie utworzony w folderze rozwiązania.

3. Kliknij prawym przyciskiem myszy pozycję **odwołania** w projekcie **ClaimsTransformation** , a następnie kliknij pozycję **Dodaj odwołanie**.

4. W oknie **Menedżer odwołań** wybierz pozycję **System. IdentityModel**, a następnie kliknij przycisk **OK**.

5. Otwórz **Class1.cs**lub jeśli nie istnieje, kliknij prawym przyciskiem myszy pozycję **ClaimsTransformation**, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Klasa...**

6. Dodaj następujące dyrektywy using do pliku kodu:

    ```csharp
    using System.Security.Claims;
    using System.Security.Principal;
    ```

7. Dodaj do pliku kodu następującą klasę i metodę.

    > [!WARNING]
    > Poniższy kod służy tylko do celów demonstracyjnych. Upewnij się, że masz pewność, że zamierzone uprawnienia są sprawdzane w kodzie produkcyjnym.

    ```csharp
    public class ClaimsTransformationModule : ClaimsAuthenticationManager
    {
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)
        {
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)
            {
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));
            }

            return incomingPrincipal;
        }
    }
    ```

8. Zapisz plik i skompiluj projekt **ClaimsTransformation** .

9. W projekcie **TestApp** ASP.NET kliknij prawym przyciskiem myszy pozycję odwołania, a następnie kliknij pozycję **Dodaj odwołanie**.

10. W oknie **Menedżer odwołań** wybierz pozycję **rozwiązanie** z menu po lewej stronie, wybierz pozycję **ClaimsTransformation** z opcji wypełnionych, a następnie kliknij przycisk **OK**.

11. W głównym pliku **Web. config** przejdź do  **\<wpisu > System. IdentityModel** . W IdentityConfiguration elementy > Dodaj następujący wiersz i Zapisz plik:  **\<**

    ```xml
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />
    ```

## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania

W tym kroku nastąpi przetestowanie aplikacji ASP.NET Web Forms i sprawdzenie, czy oświadczenia są wyświetlane, gdy użytkownik loguje się przy użyciu uwierzytelniania formularzy.

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Aby przetestować aplikację formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację. Powinna zostać wyświetlona *wartość default. aspx*.

2. Na stronie *default. aspx* powinna zostać wyświetlona tabela poniżej nagłówka **oświadczeń** , która zawiera informacje o wystawce **, OriginalIssuer**, **typie**, **wartości**i **ValueType** oświadczenia dotyczące Twojego konta. Ostatni wiersz powinien być przedstawiony w następujący sposób:

    ||||||
    |-|-|-|-|-|
    |URZĄD LOKALNY|URZĄD LOKALNY|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|Administrator|<https://www.w3.org/2001/XMLSchema#string>|
