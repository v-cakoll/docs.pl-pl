---
title: "Porady: Tworzenie aplikacji obsługującej oświadczenia ASP.NET przy użyciu uwierzytelniania opartego na formularzach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 987157bc3663330d9c610c1016787890e9dc6137
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Porady: Tworzenie aplikacji obsługującej oświadczenia ASP.NET przy użyciu uwierzytelniania opartego na formularzach
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® formularzy sieci Web  
  
## <a name="summary"></a>Podsumowanie  
 Ta porada zawiera szczegółowe procedury krok po kroku dotyczące tworzenia proste obsługujący oświadczenia aplikacji formularzy sieci Web ASP.NET, która korzysta z uwierzytelniania formularzy. Umożliwia także instrukcje dotyczące testowania aplikacji, aby zweryfikować, że oświadczenia są dostarczane, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste  
  
-   Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
-   Skonfigurować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania formularzy  
  
-   Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa poprawnie  
  
## <a name="overview"></a>Omówienie  
 W programie .NET 4.5 WIF i jego autoryzacji opartej na oświadczeniach zostały uwzględnione w ramach struktury. Wcześniej, jeśli chce oświadczenia przez użytkownika ASP.NET, możesz były wymagane do zainstalowania programu WIF, a następnie rzutowania interfejsy do podmiotu zabezpieczeń obiekty takie jak `Thread.CurrentPrincipal` lub `HttpContext.Current.User`. Teraz oświadczenia są obsługiwane automatycznie przez głównych tych obiektów.  
  
 Uwierzytelnianie formularzy uzyskał WIF jego włączenia w programie .NET 4.5, ponieważ wszyscy użytkownicy uwierzytelnieni przez formularze automatycznie oświadczeń skojarzonych z nimi. Aby rozpocząć, przy użyciu tych oświadczeń bezpośrednio w aplikacji ASP.NET, która korzysta z uwierzytelniania formularzy, jak pokazano to instrukcje.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste  
  
-   Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste  
 W tym kroku utworzysz nową aplikację ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET  
  
1.  Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.  
  
2.  W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy  
 W tym kroku spowoduje dodanie pozycji konfiguracji, aby *Web.config* pliku konfiguracji i edytowanie *Default.aspx* plik, aby wyświetlić oświadczeń informacji o koncie.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy  
  
1.  W *Default.aspx* pliku, Zastąp istniejące znaczników następującym kodem:  
  
    ```  
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
  
     Ten krok powoduje dodanie kontrolce GridView do Twojej *Default.aspx* strona, która zostanie wypełniona oświadczenia jest pobierana z uwierzytelniania formularzy.  
  
2.  Zapisz *Default.aspx* pliku, a następnie otwórz jego plik CodeBehind o nazwie *Default.aspx.cs*. Zastąp istniejący kod poniżej:  
  
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
  
     Powyższy kod zostaną wyświetlone oświadczenia dotyczące uwierzytelnionego użytkownika, w tym użytkowników identyfikowanych na podstawie uwierzytelniania formularzy.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku zostanie testowania aplikacji formularzy sieci Web ASP.NET i sprawdź, że oświadczenia są dostarczane, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Aby przetestować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania formularzy  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Powinna pojawić się *Default.aspx*, który ma **zarejestrować** i **Zaloguj się za** łącza w górnym rogu strony. Kliknij przycisk **zarejestrować**.  
  
2.  Na **zarejestrować** , Utwórz konto użytkownika, a następnie kliknij przycisk **zarejestrować**. Twoje konto zostanie utworzone przy użyciu uwierzytelniania formularzy, a użytkownik zostanie automatycznie zarejestrowany.  
  
3.  Po nastąpiło przekierowanie do strony głównej, powinna zostać wyświetlona tabela poniżej **Your oświadczeń** nagłówek, który zawiera **wystawcy**, **Wystawca_oryginalny**, **Typu**, **wartość**, i **ValueType** oświadczeń informacje o Twoim koncie.
