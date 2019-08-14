---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania opartego na formularzach'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 75db96a621d7863ef445efb24814111b34da6960
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971835"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania opartego na formularzach

## <a name="applies-to"></a>Dotyczy:

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>Podsumowanie

Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji opartej na oświadczeniach ASP.NET Web Forms, która korzysta z uwierzytelniania formularzy. Zawiera również instrukcje dotyczące testowania aplikacji w celu sprawdzenia, czy oświadczenia są prezentowane, gdy użytkownik loguje się przy użyciu uwierzytelniania formularzy.

## <a name="contents"></a>Spis treści

- Cele

- Omówienie

- Zestawienie czynności

- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms

- Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy

- Krok 3 — Przetestowanie rozwiązania

## <a name="objectives"></a>Cele

- Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby oświadczeń przy użyciu uwierzytelniania formularzy

- Przetestuj aplikację ASP.NET Web Forms, aby sprawdzić, czy działa prawidłowo

## <a name="overview"></a>Omówienie

W programie .NET 4,5, WIF i Autoryzacja oparta na oświadczeniach została uwzględniona jako integralna część struktury. Wcześniej, jeśli chcesz uzyskać oświadczenia od użytkownika ASP.NET, musisz zainstalować WIF, a następnie rzutować interfejsy na obiekty Principal, takie jak `Thread.CurrentPrincipal` lub. `HttpContext.Current.User` Teraz oświadczenia są automatycznie obsługiwane przez te obiekty główne.

Uwierzytelnianie formularzy zostało korzystne z uwzględnieniem WIF w programie .NET 4,5, ponieważ wszyscy użytkownicy uwierzytelnieni przez formularze automatycznie mają skojarzone z nimi oświadczenia. Możesz zacząć korzystać z tych oświadczeń natychmiast w aplikacji ASP.NET, która korzysta z uwierzytelniania formularzy, jak pokazano na tej liście.

## <a name="summary-of-steps"></a>Zestawienie czynności

- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms

- Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy

- Krok 3 — Przetestowanie rozwiązania

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms

W tym kroku utworzysz nową aplikację ASP.NET Web Forms.

### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET

1. Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.

2. W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.

3. W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy

W tym kroku dodasz wpis konfiguracyjny do pliku konfiguracji *Web. config* i edytujesz domyślny plik *. aspx* , aby wyświetlić informacje dotyczące oświadczeń dla konta.

### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy

1. W pliku *default. aspx* Zastąp istniejący znacznik następującym:

    ```aspx
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
        <p>
            This page displays the claims associated with a Forms authenticated user.
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

    Ten krok powoduje dodanie kontrolki GridView do *domyślnej strony. aspx* , która zostanie uzupełniona o oświadczenia pobrane z uwierzytelniania formularzy.

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

                if (claimsPrincipal != null)
                {
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                    this.ClaimsGridView.DataBind();
                }
            }
        }
    }
    ```

    Powyższy kod będzie wyświetlał oświadczenia dotyczące uwierzytelnionego użytkownika, w tym użytkowników zidentyfikowanych przez uwierzytelnianie formularzy.

## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania

W tym kroku nastąpi przetestowanie aplikacji ASP.NET Web Forms i sprawdzenie, czy oświadczenia są wyświetlane, gdy użytkownik loguje się przy użyciu uwierzytelniania formularzy.

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Aby przetestować aplikację formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację. Powinna zostać wyświetlona *wartość default. aspx*, która zawiera linki **register** i **log** in w prawym górnym rogu strony. Kliknij pozycję **zarejestruj**.

2. Na stronie **Rejestr** Utwórz konto użytkownika, a następnie kliknij przycisk **zarejestruj**. Twoje konto zostanie utworzone przy użyciu uwierzytelniania formularzy, a użytkownik zostanie automatycznie zalogowany.

3. Po przekierowaniu do strony głównej powinna zostać wyświetlona tabela poniżej nagłówka **oświadczeń** , która zawiera informacje o wystawcy, **OriginalIssuer**, **Typ**, **wartość**i element **ValueType** oświadczenia dotyczące koncie.
