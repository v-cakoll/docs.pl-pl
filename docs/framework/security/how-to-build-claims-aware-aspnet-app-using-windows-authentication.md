---
title: 'Porady: Tworzenie aplikacji ASP.NET obsługujący oświadczenia za pomocą uwierzytelniania systemu Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a5dbec2e92d32e45bc0271de04f8c6403f67f90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Porady: Tworzenie aplikacji ASP.NET obsługujący oświadczenia za pomocą uwierzytelniania systemu Windows
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® formularzy sieci Web  
  
## <a name="summary"></a>Podsumowanie  
 Porada ten zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostego obsługujący oświadczenia aplikacji formularzy sieci Web ASP.NET, która używa uwierzytelniania systemu Windows. Umożliwia także instrukcje dotyczące testowania aplikacji, aby zweryfikować, że oświadczenia są dostarczane, gdy użytkownik loguje się przy użyciu uwierzytelniania systemu Windows.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste  
  
-   Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
-   Skonfigurować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania systemu Windows  
  
-   Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa poprawnie  
  
## <a name="overview"></a>Omówienie  
 W programie .NET 4.5 WIF i jego autoryzacji opartej na oświadczeniach zostały uwzględnione w ramach struktury. Wcześniej, jeśli chce oświadczenia przez użytkownika ASP.NET, możesz były wymagane do zainstalowania programu WIF, a następnie rzutowania interfejsy do podmiotu zabezpieczeń obiekty takie jak `Thread.CurrentPrincipal` lub `HttpContext.Current.User`. Teraz oświadczenia są obsługiwane automatycznie przez głównych tych obiektów.  
  
 Uwierzytelnianie systemu Windows uzyskał WIF jego włączenia w programie .NET 4.5, ponieważ wszyscy użytkownicy, uwierzytelniane przez poświadczenia systemu Windows automatycznie mają oświadczeń skojarzonych z nimi. Aby rozpocząć, przy użyciu tych oświadczeń bezpośrednio w aplikacji ASP.NET, która używa uwierzytelniania systemu Windows, jak pokazano to instrukcje.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste  
  
-   Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste  
 W tym kroku utworzysz nową aplikację ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET  
  
1.  Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.  
  
2.  W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
4.  Po **TestApp** projekt został utworzony, kliknij go w **Eksploratora rozwiązań**. Właściwości projektu będą wyświetlane w **właściwości** poniżej okienku **Eksploratora rozwiązań**. Ustaw **uwierzytelniania systemu Windows** właściwości **włączone**.  
  
    > [!WARNING]
    >  Uwierzytelnianie systemu Windows jest domyślnie wyłączona w nowej aplikacji ASP.NET, dlatego należy ręcznie włączyć ją.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows  
 W tym kroku spowoduje dodanie pozycji konfiguracji, aby *Web.config* konfiguracji plik i zmodyfikuj *Default.aspx* plik, aby wyświetlić oświadczeń informacji o koncie.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows  
  
1.  W **TestApp** projektu *Default.aspx* pliku, Zastąp istniejące znaczników następującym kodem:  
  
    ```  
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
  
     Ten krok powoduje dodanie kontrolce GridView do Twojej *Default.aspx* strona, która zostanie wypełniona oświadczenia jest pobierana z uwierzytelniania systemu Windows.  
  
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
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     Powyższy kod zostaną wyświetlone oświadczenia dotyczące uwierzytelnionego użytkownika.  
  
3.  Aby zmienić typ uwierzytelniania aplikacji, należy zmodyfikować  **\<uwierzytelniania >** blok w  **\<system.web >** sekcji głównego projektu  *Plik Web.config* pliku co zawierają one tylko następujący wpis konfiguracji:  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  Na koniec zmodyfikuj  **\<autoryzacji >** blok w  **\<system.web >** sekcji tego samego *Web.config* pliku, aby wymusić uwierzytelniania:  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku zostanie testowania aplikacji formularzy sieci Web ASP.NET i sprawdź, że oświadczenia są dostarczane, gdy użytkownik zaloguje się za pomocą uwierzytelniania systemu Windows.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Aby przetestować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania systemu Windows  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Powinna pojawić się *Default.aspx*, a nazwa konta systemu Windows (łącznie z nazwą domeny) już powinny się wyświetlać jako użytkownik uwierzytelniony w górnym rogu strony. Zawartość strony ma powinna zawierać tabelę wypełnione oświadczeń pobierane z konta systemu Windows.
