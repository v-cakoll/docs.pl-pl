---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania systemu Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 34d6c7916b3035e9896b1dd9d7c7d8b3e7b0fcfc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040994"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania systemu Windows

## <a name="applies-to"></a>Dotyczy:

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>Podsumowanie

Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji opartej na oświadczeniach ASP.NET Web Forms, która używa uwierzytelniania systemu Windows. Zawiera również instrukcje dotyczące testowania aplikacji w celu sprawdzenia, czy oświadczenia są prezentowane, gdy użytkownik loguje się przy użyciu uwierzytelniania systemu Windows.

## <a name="contents"></a>Spis treści

- Cele

- Omówienie

- Zestawienie czynności

- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms

- Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows

- Krok 3 — Przetestowanie rozwiązania

## <a name="objectives"></a>Cele

- Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows

- Przetestuj aplikację ASP.NET Web Forms, aby sprawdzić, czy działa prawidłowo

## <a name="overview"></a>Omówienie

W programie .NET 4,5, WIF i Autoryzacja oparta na oświadczeniach została uwzględniona jako integralna część struktury. Wcześniej, jeśli chcesz uzyskać oświadczenia od użytkownika ASP.NET, musisz zainstalować WIF, a następnie rzutować interfejsy na obiekty Principal, takie jak `Thread.CurrentPrincipal` lub. `HttpContext.Current.User` Teraz oświadczenia są automatycznie obsługiwane przez te obiekty główne.

Uwierzytelnianie systemu Windows skorzystało z WIF w programie .NET 4,5, ponieważ wszyscy użytkownicy uwierzytelnieni przez poświadczenia systemu Windows automatycznie mają skojarzone z nimi oświadczenia. Możesz zacząć korzystać z tych oświadczeń natychmiast w aplikacji ASP.NET, która używa uwierzytelniania systemu Windows, jak pokazano na tej liście.

## <a name="summary-of-steps"></a>Zestawienie czynności

- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms

- Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows

- Krok 3 — Przetestowanie rozwiązania

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms

W tym kroku utworzysz nową aplikację ASP.NET Web Forms.

### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET

1. Uruchom program Visual Studio, a następnie kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.

2. W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.

3. W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.

4. Po utworzeniu projektu **TestApp** kliknij go w **Eksplorator rozwiązań**. Właściwości projektu zostaną wyświetlone w okienku **Właściwości** poniżej **Eksplorator rozwiązań**. Ustaw właściwość **uwierzytelnianie systemu Windows** na **włączone**.

    > [!WARNING]
    > Uwierzytelnianie systemu Windows jest domyślnie wyłączone w nowych aplikacjach ASP.NET, więc należy je włączyć ręcznie.

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows

W tym kroku dodasz wpis konfiguracyjny do pliku konfiguracji *Web. config* i zmodyfikujesz domyślny plik *. aspx* , aby wyświetlić informacje dotyczące oświadczeń dla konta.

### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows

1. W pliku *default. aspx* projektu **TestApp** Zastąp istniejący znacznik następującym:

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
        <p>
            This page displays the claims associated with a Windows authenticated user.
        </p>
        <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

    Ten krok powoduje dodanie kontrolki GridView do *domyślnej strony. aspx* , która zostanie uzupełniona o oświadczenia pobrane z uwierzytelniania systemu Windows.

2. Zapisz plik *default. aspx* , a następnie otwórz jego plik związany z kodem o nazwie *default.aspx.cs*. Zastąp istniejący kod następującym:

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

    Powyższy kod będzie wyświetlał oświadczenia dotyczące uwierzytelnionego użytkownika.

3. Aby zmienić typ uwierzytelniania aplikacji, należy zmodyfikować  **\<blok > uwierzytelniania** w sekcji  **\<> System. Web** w głównym pliku *Web. config* projektu, tak aby zawierał tylko następujące elementy: wpis konfiguracji:

    ```xml
    <authentication mode="Windows" />
    ```

4. Na koniec zmodyfikuj  **\<blok > autoryzacji** w  **\<sekcji > System. Web** w tym samym pliku *Web. config* , aby wymusić uwierzytelnianie:

    ```xml
    <authorization>
        <deny users="?" />
    </authorization>
    ```

## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania

W tym kroku nastąpi przetestowanie aplikacji ASP.NET Web Forms i sprawdzenie, czy oświadczenia są wyświetlane, gdy użytkownik loguje się przy użyciu uwierzytelniania systemu Windows.

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Aby przetestować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania systemu Windows

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację. Powinna zostać wyświetlona *wartość default. aspx*, a nazwa konta systemu Windows (w tym nazwa domeny) powinna już być wyświetlana jako uwierzytelniony użytkownik w prawym górnym rogu strony. Zawartość strony powinna zawierać tabelę wypełnioną przez oświadczenia pobrane z konta systemu Windows.
