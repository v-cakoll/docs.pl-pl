---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji formularzy internetowych ASP.NET za pomocą programu WIF'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 74f15c3ac6e5192ce3565579d515198d3b7e39f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769596"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Instrukcje: Tworzenie obsługującej oświadczenia aplikacji formularzy internetowych ASP.NET za pomocą programu WIF
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web Forms  
  
## <a name="summary"></a>Podsumowanie  
 Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji formularzy sieci Web programu ASP.NET obsługującej oświadczenia. On również instrukcje testowania prostą aplikację formularzy sieci Web programu ASP.NET obsługującej oświadczenia dla pomyślnego wdrożenia uwierzytelniania federacyjnego. Niniejszy instruktaż nie zawiera szczegółowych instrukcji tworzenia Usługa tokenu zabezpieczającego (STS), a przyjęto założenie, że zostały już skonfigurowane usługi tokenu Zabezpieczającego.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Zestawienie czynności  
  
-   Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms  
  
-   Krok 2 — Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla uwierzytelniania opartego na oświadczeniach  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
-   Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla uwierzytelniania opartego na oświadczeniach  
  
-   Testowanie pomyślne obsługującej oświadczenia aplikacji formularzy sieci Web ASP.NET  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms  
  
-   Krok 2 — Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla uwierzytelniania federacyjnego  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms  
 W tym kroku utworzysz nową aplikację ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację platformy ASP.NET  
  
1. Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.  
  
2. W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.  
  
3. W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>Krok 2 — Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla uwierzytelniania opartego na oświadczeniach  
 W tym kroku dodasz wpisy konfiguracji *Web.config* pliku konfiguracji aplikacji ASP.NET Web Forms się obsługujących oświadczenia.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>Aby skonfigurować aplikację ASP.NET do uwierzytelniania opartego na oświadczeniach  
  
1. Dodaj następujące wpisy konfiguracji w sekcji, aby *Web.config* plik konfiguracyjny natychmiast po  **\<konfiguracji >** otwarcia elementu:  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. Dodaj  **\<lokalizacja >** elementu, który umożliwia dostęp do metadanych Federacji aplikacji:  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3. Dodaj następujące wpisy konfiguracji w ramach  **\<system.web >** elementy, aby odmówić użytkownikom, Wyłącz uwierzytelnianie natywnych i włączanie programu WIF zarządzać uwierzytelnianiem.  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. Dodaj  **\<system.webServer >** element, który definiuje modułów dla uwierzytelniania federacyjnego. Należy pamiętać, że *PublicKeyToken* atrybut musi być taka sama jak *PublicKeyToken* atrybutu dla  **\<configSections >** wpisy dodano wcześniej:  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. Dodaj następujące Windows Identity Foundation powiązane wpisy konfiguracji i upewnij się, że adres URL aplikacji ASP.NET i numer portu pasuje do wartości w  **\<audienceUris >** wpisu **obszaru**  atrybutu  **\<wsFederation >** elementu, a **odpowiedzi** atrybutu  **\<wsFederation >** elementu. Ponadto upewnij się, że **wystawcy** pasuje do wartości adresu URL Usługa tokenu zabezpieczającego (STS).  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6. Dodaj odwołanie do <xref:System.IdentityModel> zestawu.  
  
7. Skompiluj rozwiązanie, aby upewnić się, że nie ma żadnych błędów.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku przetestujesz aplikację ASP.NET Web Forms skonfigurowany do uwierzytelniania opartego na oświadczeniach. Aby wykonać podstawowy test, należy dodać kod, który przedstawia oświadczenia w tokenie, wystawiony przez Usługa tokenu zabezpieczającego (STS).  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>Aby przetestować aplikację formularza sieci Web platformy ASP.NET dla uwierzytelniania opartego na oświadczeniach  
  
1. Otwórz **Default.aspx** plik **TestApp** projektu i zastąp jego znaczników istniejący następującym kodem:  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2. Zapisz **Default.aspx**, a następnie otwórz jego kod związany z pliku o nazwie **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** może być ukryty pod **Default.aspx** w Eksploratorze rozwiązań. Jeśli **Default.aspx.cs** nie jest widoczny, rozwiń węzeł **Default.aspx** , klikając trójkąta obok niej.  
  
3. Zastąp istniejący kod w **Page_Load** metody **Default.aspx.cs** następującym kodem:  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4. Zapisz **Default.aspx.cs**i Skompiluj rozwiązanie.  
  
5. Uruchom rozwiązanie, naciskając klawisz **F5** klucza.  
  
6. Powinno zostać wyświetlone ze stroną, które zostaną wyświetlone oświadczenia w tokenie, który został wystawiony przez usługę tokenu zabezpieczającego.
