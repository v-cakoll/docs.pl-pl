---
title: 'Instrukcje: Przekształcanie oświadczeń przychodzących'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: 8673b4520d9727ae1aa78ef0bc9f435defb02598
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032338"
---
# <a name="how-to-transform-incoming-claims"></a>Instrukcje: Przekształcanie oświadczeń przychodzących
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® formularzy sieci Web  
  
## <a name="summary"></a>Podsumowanie  
 Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji formularzy sieci Web programu ASP.NET obsługujących oświadczenia i przekształcanie oświadczeń przychodzących. On również instrukcje testowania aplikacji, aby zweryfikować, że oświadczenia po przekształceniu są dostarczane, gdy aplikacja jest uruchomiona.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Omówienie  
  
-   Zestawienie czynności  
  
-   Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms  
  
-   Krok 2 — Implementowanie oświadczeń przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
-   Skonfigurować aplikację ASP.NET Web Forms pod kątem uwierzytelniania opartego na oświadczeniach  
  
-   Przekształcanie oświadczeń przychodzących przez dodanie oświadczenie roli administratora  
  
-   Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa prawidłowo  
  
## <a name="overview"></a>Omówienie  
 Program WIF przedstawia klasę o nazwie <xref:System.Security.Claims.ClaimsAuthenticationManager> umożliwiającej użytkownikom na modyfikowanie oświadczeń, zanim zostaną one zaprezentowane na aplikację jednostki uzależnionej (RP). <xref:System.Security.Claims.ClaimsAuthenticationManager> Jest przydatne w przypadku separacji między uwierzytelniania i odpowiedni kod aplikacji. W poniższym przykładzie przedstawiono sposób dodawania roli do roszczeń w przychodzącej <xref:System.Security.Claims.ClaimsPrincipal> , może być wymagane przez jednostkę Uzależnioną.  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms  
  
-   Krok 2 — Implementowanie oświadczeń przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms  
 W tym kroku utworzysz nową aplikację ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację platformy ASP.NET  
  
1.  Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.  
  
2.  W programie Visual Studio, kliknij przycisk **pliku**, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.  
  
3.  W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
4.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
5.  Kliknij prawym przyciskiem myszy **TestApp** projekt **Eksploratora rozwiązań**, a następnie wybierz **tożsamościami i dostępem**.  
  
6.  **Tożsamościami i dostępem** zostanie wyświetlone okno. W obszarze **dostawców**, wybierz opcję **testować swoją aplikację za pomocą lokalnej deweloperskiej usługi STS**, następnie kliknij przycisk **Zastosuj**.  
  
7.  W *Default.aspx* pliku, Zastąp istniejący kod znaczników następującym kodem, a następnie zapisz plik:  
  
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
  
8.  Otwórz plik związany z kodem o nazwie *Default.aspx.cs*. Zastąp istniejący kod następującym kodem i Zapisz plik:  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Krok 2 — Implementowanie oświadczeń przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania  
 W tym kroku spowoduje przesłonięcie funkcje domyślne w <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy, aby dodać rolę administratora do jednostki przychodzącego.  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Aby zaimplementować przekształcania oświadczeń przy użyciu niestandardowych ClaimsAuthenticationManager  
  
1.  W programie Visual Studio, kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **Dodaj nowy projekt** wybierz **biblioteki klas** z **Visual C#** szablony list, wprowadź `ClaimsTransformation`, a następnie naciśnij klawisz **OK**. Nowy projekt zostanie utworzony w folderze rozwiązania.  
  
3.  Kliknij prawym przyciskiem myszy **odwołania** w obszarze **ClaimsTransformation** projektu, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
4.  W **Menadżer odwołań** wybierz **System.IdentityModel**, a następnie kliknij przycisk **OK**.  
  
5.  Otwórz **Class1.cs**, lub jeśli nie istnieje, kliknij prawym przyciskiem myszy **ClaimsTransformation**, kliknij przycisk **Dodaj**, następnie kliknij przycisk **klasy...**  
  
6.  Dodaj następujące dyrektywy using do pliku kodu:  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  Dodaj następujące klasy i metody w pliku kodu.  
  
    > [!WARNING]
    >  Poniższy kod jest wyłącznie demonstracyjny; Upewnij się, aby zweryfikować swoje uprawnienia zamierzone, w kodzie produkcyjnym.  
  
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
  
8.  Zapisz plik i skompiluj **ClaimsTransformation** projektu.  
  
9. W swojej **TestApp** projektu ASP.NET, kliknij prawym przyciskiem myszy na odwołań, a następnie kliknij **Dodaj odwołanie**.  
  
10. W **Menadżer odwołań** wybierz **rozwiązania** z menu po lewej stronie wybierz **ClaimsTransformation** z wypełnione opcje, a następnie kliknij przycisk  **OK**.  
  
11. W katalogu głównym **Web.config** pliku, przejdź do folderu  **\<system.identityModel >** wpisu. W ramach  **\<identityConfiguration >** elementów, Dodaj następujący wiersz i Zapisz plik:  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku zostanie testowanie aplikacji ASP.NET Web Forms i sprawdź, czy są prezentowane oświadczenia, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Aby przetestować aplikację ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Powinna pojawić się *Default.aspx*.  
  
2.  Na *Default.aspx* strony powinna zostać wyświetlona tabela poniżej **Your oświadczeń** nagłówek, który zawiera **wystawcy**, **Wystawca_oryginalny**, **Typu**, **wartość**, i **ValueType** oświadczeń informacji o Twoim koncie. Ostatni wiersz powinno zostać wyświetlone w następujący sposób:  
  
    ||||||  
    |-|-|-|-|-|  
    |URZĄD LOKALNY|URZĄD LOKALNY|http://schemas.microsoft.com/ws/2008/06/identity/claims/role|Administrator|http://www.w3.org/2001/XMLSchema#string|
