---
title: 'Instrukcje: Tworzenie aplikacji programu ASP.NET obsługującej oświadczenia, za pomocą uwierzytelniania opartego na formularzach'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: ecaf1de0b806d5568d81fac2ddb2b39b697135ab
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354755"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Instrukcje: Tworzenie aplikacji programu ASP.NET obsługującej oświadczenia, za pomocą uwierzytelniania opartego na formularzach

## <a name="applies-to"></a>Dotyczy:

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>Podsumowanie

Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji formularzy sieci Web programu ASP.NET obsługującej oświadczenia korzystającej z uwierzytelniania formularzy. On również instrukcje testowania aplikacji pozwalające sprawdzić, czy są prezentowane oświadczenia, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.

## <a name="contents"></a>Spis treści

- Cele

- Omówienie

- Zestawienie czynności

- Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms

- Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy

- Krok 3 — Przetestowanie rozwiązania

## <a name="objectives"></a>Cele

- Skonfigurować aplikację ASP.NET Web Forms pod kątem oświadczeń za pomocą uwierzytelniania formularzy

- Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa prawidłowo

## <a name="overview"></a>Omówienie

W .NET 4.5 WIF i jego autoryzacji opartej na oświadczeniach zostały uwzględnione w ramach Framework. Wcześniej, jeśli chce oświadczeń użytkownika ASP.NET należało do zainstalowania programu WIF, i następnie rzutowania interfejsy z podmiotem zabezpieczeń obiektów takich jak `Thread.CurrentPrincipal` lub `HttpContext.Current.User`. Obecnie oświadczeń są obsługiwane automatycznie przez te jednostki obiektów.

Uwierzytelnianie formularzy skorzystał z włączenia programu WIF w .NET 4.5, ponieważ wszyscy użytkownicy uwierzytelnieni przez formularze automatycznie oświadczenia skojarzone z nimi. Możesz rozpocząć korzystanie z tych oświadczeń bezpośrednio w aplikacji ASP.NET, która korzysta z uwierzytelniania formularzy, tak jak pokazano w tym instruktażu.

## <a name="summary-of-steps"></a>Zestawienie czynności

- Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms

- Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy

- Krok 3 — Przetestowanie rozwiązania

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms

W tym kroku utworzysz nową aplikację ASP.NET Web Forms.

#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację platformy ASP.NET

1. Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.

2. W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.

3. W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy

W tym kroku dodasz wpis konfiguracyjny do *Web.config* pliku konfiguracji i Edytuj *Default.aspx* plik, aby wyświetlić oświadczenia informacji o koncie.

#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Aby skonfigurować aplikację ASP.NET dla oświadczeń za pomocą uwierzytelniania formularzy

1. W *Default.aspx* pliku, Zastąp istniejący kod znaczników następującym kodem:

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

    Ten krok powoduje dodanie kontrolki widoku siatki do Twojej *Default.aspx* strony, który zostanie wypełniony oświadczenia jest pobierana z uwierzytelniania formularzy.

2. Zapisz *Default.aspx* pliku, a następnie otwórz jego pliku związanego z kodem o nazwie *Default.aspx.cs*. Zastąp istniejący kod następujących czynności:

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

    Powyższy kod wyświetli oświadczenia dotyczące uwierzytelnionego użytkownika, w tym użytkowników identyfikowanych na podstawie uwierzytelniania formularzy.

## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania

W tym kroku zostanie testowanie aplikacji ASP.NET Web Forms i sprawdź, czy są prezentowane oświadczenia, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Aby przetestować aplikację ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy

1. Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Powinna pojawić się *Default.aspx*, który ma **zarejestrować** i **Zaloguj się** łącza w prawym górnym rogu strony. Kliknij przycisk **zarejestrować**.

2. Na **zarejestrować** strony, Utwórz konto użytkownika, a następnie kliknij przycisk **zarejestrować**. Twoje konto zostanie utworzone za pomocą uwierzytelniania formularzy, a użytkownik zostanie automatycznie zalogowany.

3. Po nastąpiło przekierowanie do strony głównej, powinien zostać wyświetlony tabelę poniżej **Your oświadczeń** nagłówek, który zawiera **wystawcy**, **Wystawca_oryginalny**, **Typu**, **wartość**, i **ValueType** oświadczeń informacji o Twoim koncie.
