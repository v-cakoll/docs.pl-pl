---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania systemu Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 48b1b4715e9e2613757a981ba692d84ad06a1ec6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940546"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania systemu Windows
## <a name="applies-to"></a>Dotyczy:  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® Web Forms  
  
## <a name="summary"></a>Podsumowanie  
 Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji formularzy sieci Web programu ASP.NET obsługującej oświadczenia korzystającej z uwierzytelniania Windows. On również instrukcje testowania aplikacji pozwalające sprawdzić, czy są prezentowane oświadczenia, gdy użytkownik loguje się przy użyciu uwierzytelniania Windows.  
  
## <a name="contents"></a>Spis treści  
  
- Cele  
  
- Omówienie  
  
- Zestawienie czynności  
  
- Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms  
  
- Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia przy użyciu uwierzytelniania Windows  
  
- Krok 3 — Przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
- Skonfigurować aplikację ASP.NET Web Forms pod kątem oświadczeń przy użyciu uwierzytelniania Windows  
  
- Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa prawidłowo  
  
## <a name="overview"></a>Omówienie  
 W .NET 4.5 WIF i jego autoryzacji opartej na oświadczeniach zostały uwzględnione w ramach Framework. Wcześniej, jeśli chce oświadczeń użytkownika ASP.NET należało do zainstalowania programu WIF, i następnie rzutowania interfejsy z podmiotem zabezpieczeń obiektów takich jak `Thread.CurrentPrincipal` lub `HttpContext.Current.User`. Obecnie oświadczeń są obsługiwane automatycznie przez te jednostki obiektów.  
  
 Uwierzytelnianie Windows skorzystał z włączenia programu WIF w .NET 4.5, ponieważ wszyscy użytkownicy uwierzytelnieni poświadczenia Windows automatycznie oświadczenia skojarzone z nimi. Możesz rozpocząć korzystanie z tych oświadczeń bezpośrednio w aplikacji ASP.NET, która korzysta z uwierzytelniania Windows, tak jak pokazano w tym instruktażu.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
- Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms  
  
- Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia przy użyciu uwierzytelniania Windows  
  
- Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms  
 W tym kroku utworzysz nową aplikację ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację platformy ASP.NET  
  
1. Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.  
  
2. W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3. W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
4. Po **TestApp** został utworzony projekt, kliknij go w **Eksploratora rozwiązań**. Właściwości projektu, pojawi się w **właściwości** okienku poniżej **Eksploratora rozwiązań**. Ustaw **uwierzytelniania Windows** właściwości **włączone**.  
  
    > [!WARNING]
    >  Uwierzytelnianie Windows jest domyślnie wyłączona, w nowej aplikacji ASP.NET, więc musisz ręcznie włączyć ją.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia przy użyciu uwierzytelniania Windows  
 W tym kroku dodasz wpis konfiguracyjny do *Web.config* konfiguracji plik i Modyfikuj *Default.aspx* plik, aby wyświetlić oświadczenia informacji o koncie.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania Windows  
  
1. W **TestApp** projektu *Default.aspx* pliku, Zastąp istniejący kod znaczników następującym kodem:  
  
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
  
     Ten krok powoduje dodanie kontrolki widoku siatki do Twojej *Default.aspx* strony, który zostanie wypełniony oświadczenia jest pobierana z uwierzytelniania Windows.  
  
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
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     Powyższy kod wyświetli oświadczenia dotyczące uwierzytelnionego użytkownika.  
  
3. Aby zmienić typ uwierzytelniania aplikacji, należy zmodyfikować  **\<uwierzytelniania >** bloku  **\<system.web >** sekcji katalog główny projektu  *Plik Web.config* plik zawiera tylko następujący wpis konfiguracji:  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4. Na koniec zmodyfikuj  **\<autoryzacji >** bloku  **\<system.web >** sekcji tego samego *Web.config* plik, aby wymusić uwierzytelnianie:  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku zostanie testowanie aplikacji ASP.NET Web Forms i sprawdź, czy są prezentowane oświadczenia, gdy użytkownik loguje się przy użyciu uwierzytelniania Windows.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Aby przetestować aplikację ASP.NET Web Forms oświadczenia przy użyciu uwierzytelniania Windows  
  
1. Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Powinna pojawić się *Default.aspx*, i nazwę konta Windows (łącznie z nazwą domeny) już powinna zostać wyświetlona jako użytkownik uwierzytelniony w prawym górnym rogu strony. Zawartość strony powinna zawierać tabelę wypełnione oświadczeń pobierane z konta usługi Windows.
