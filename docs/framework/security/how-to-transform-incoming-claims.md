---
title: "Porady: Przekształcanie oświadczeń przychodzących"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: bcf0e640e6b6b45ddb87070c7d6df2fa6dadc834
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-incoming-claims"></a>Porady: Przekształcanie oświadczeń przychodzących
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® formularzy sieci Web  
  
## <a name="summary"></a>Podsumowanie  
 Porada ten zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji obsługującej oświadczenia formularzy sieci Web ASP.NET i przekształcanie oświadczeń przychodzących. Umożliwia także instrukcje dotyczące testowania aplikacji, aby zweryfikować, że oświadczenia po przekształceniu są dostarczane, gdy aplikacja jest uruchamiana.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste  
  
-   Krok 2 — przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania oświadczeń wdrożenie  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
-   Skonfigurować aplikację ASP.NET Web Forms dla uwierzytelniania opartego na oświadczeniach  
  
-   Oświadczenia przychodzące przez dodanie oświadczenia roli administratora  
  
-   Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa poprawnie  
  
## <a name="overview"></a>Omówienie  
 WIF udostępnia klasę o nazwie <xref:System.Security.Claims.ClaimsAuthenticationManager> , umożliwia użytkownikom na modyfikowanie oświadczeń, zanim zostaną przedstawione do jednostki uzależnionej aplikacji firm (RP). <xref:System.Security.Claims.ClaimsAuthenticationManager> Jest przydatne w przypadku separacji między uwierzytelniania i źródłowy kod aplikacji. W poniższym przykładzie pokazano, jak dodać roli do oświadczeń z przychodzącego <xref:System.Security.Claims.ClaimsPrincipal> , co może być wymagane przez planu odzyskiwania.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste  
  
-   Krok 2 — przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania oświadczeń wdrożenie  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste  
 W tym kroku utworzysz nową aplikację ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET  
  
1.  Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.  
  
2.  W programie Visual Studio, kliknij przycisk **pliku**, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
4.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
5.  Kliknij prawym przyciskiem myszy **TestApp** projektu w obszarze **Eksploratora rozwiązań**, a następnie wybierz pozycję **tożsamościami i dostępem**.  
  
6.  **Tożsamościami i dostępem** zostanie wyświetlone okno. W obszarze **dostawców**, wybierz pozycję **testowania aplikacji z lokalnej usługi STS programowanie**, następnie kliknij przycisk **Zastosuj**.  
  
7.  W *Default.aspx* pliku, Zastąp istniejące znaczników następującym kodem, a następnie zapisz plik:  
  
    ```  
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
  
8.  Otwórz plik CodeBehind o nazwie *Default.aspx.cs*. Zastąp istniejący kod poniżej, następnie zapisz ten plik:  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Krok 2 — przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania oświadczeń wdrożenie  
 W tym kroku zostanie zastąpione domyślna funkcjonalność w <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę, aby dodać rolę administratora do przychodzącego podmiotu zabezpieczeń.  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Aby zaimplementować przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania oświadczeń  
  
1.  W programie Visual Studio, kliknij prawym przyciskiem myszy na rozwiązanie, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** wybierz **biblioteki klas** z **Visual C#** szablony list, wprowadź `ClaimsTransformation`, a następnie naciśnij klawisz **OK**. Nowy projekt zostanie utworzony w folderze rozwiązania.  
  
3.  Kliknij prawym przyciskiem myszy **odwołania** w obszarze **ClaimsTransformation** projektu, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
4.  W **Menedżera odwołań** wybierz **System.IdentityModel**, a następnie kliknij przycisk **OK**.  
  
5.  Otwórz **Class1.cs**, lub jeśli nie istnieje, kliknij prawym przyciskiem myszy **ClaimsTransformation**, kliknij przycisk **Dodaj**, następnie kliknij przycisk **klasy...**  
  
6.  Dodaj następujący kod do pliku kodu przy użyciu dyrektyw:  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  Dodaj następujące klasy i metody w pliku kodu.  
  
    > [!WARNING]
    >  Następujący kod jest tylko w celach demonstracyjnych Upewnij się, że Sprawdź swoje uprawnienia zamierzonego w kodzie produkcyjnym.  
  
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
  
8.  Zapisz plik i kompilacji **ClaimsTransformation** projektu.  
  
9. W Twojej **TestApp** projektu ASP.NET, kliknij prawym przyciskiem myszy na odwołania, a następnie kliknij **Dodaj odwołanie**.  
  
10. W **Menedżera odwołań** wybierz **rozwiązania** z menu po lewej stronie wybierz **ClaimsTransformation** z wypełnione opcje, a następnie kliknij przycisk  **OK**.  
  
11. W folderze głównym **Web.config** pliku, przejdź do  **\<system.identityModel >** wpisu. W ramach  **\<identityConfiguration >** elementów, Dodaj następujący wiersz i Zapisz plik:  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku zostanie testowania aplikacji formularzy sieci Web ASP.NET i sprawdź, że oświadczenia są dostarczane, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Aby przetestować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania formularzy  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Powinna pojawić się *Default.aspx*.  
  
2.  Na *Default.aspx* strony, powinna zostać wyświetlona tabela poniżej **Your oświadczeń** nagłówek, który zawiera **wystawcy**, **Wystawca_oryginalny**, **Typu**, **wartość**, i **ValueType** oświadczeń informacje o Twoim koncie. Ostatni wiersz powinny być prezentowane w następujący sposób:  
  
    ||||||  
    |-|-|-|-|-|  
    |URZĄD LOKALNY|URZĄD LOKALNY|http://schemas.microsoft.com/ws/2008/06/identity/claims/role|Administrator|http://www.w3.org/2001/XMLSchema#String|
