---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji formularzy internetowych ASP.NET za pomocą programu WIF'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 82b0649a7324987581cc3c97570a0fc42ffdf6d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941298"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Instrukcje: Tworzenie obsługującej oświadczenia aplikacji formularzy internetowych ASP.NET za pomocą programu WIF
## <a name="applies-to"></a>Dotyczy:  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® Web Forms  
  
## <a name="summary"></a>Podsumowanie  
 Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostych aplikacji opartych na oświadczeniach ASP.NET Web Forms. Zawiera również instrukcje dotyczące testowania prostej aplikacji opartej na oświadczeniach ASP.NET Web Forms w celu pomyślnego wdrożenia uwierzytelniania federacyjnego. Ta instrukcja nie zawiera szczegółowych instrukcji dotyczących tworzenia usługi tokenu zabezpieczającego (STS) i zakłada, że już skonfigurowano usługę STS.  
  
## <a name="contents"></a>Spis treści  
  
- Cele  
  
- Zestawienie czynności  
  
- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms  
  
- Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach  
  
- Krok 3 — Przetestowanie rozwiązania  
  
## <a name="objectives"></a>Cele  
  
- Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach  
  
- Testowanie pomyślnej aplikacji formularzy sieci Web ASP.NET obsługujących oświadczenia  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
- Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms  
  
- Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania federacyjnego  
  
- Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms  
 W tym kroku utworzysz nową aplikację ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Aby utworzyć prostą aplikację ASP.NET  
  
1. Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.  
  
2. W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.  
  
3. W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach  
 W tym kroku dodasz wpisy konfiguracyjne do pliku konfiguracyjnego *Web. config* aplikacji ASP.NET Web Forms, aby zapewnić obsługę oświadczeń.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>Aby skonfigurować aplikację ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach  
  
1. Dodaj następujące wpisy sekcji konfiguracji do pliku konfiguracyjnego *Web. config* bezpośrednio po  **\<elemencie Configuration >** otwierającym:  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. Dodaj **lokalizację > elementu, który umożliwia dostęp do metadanych federacji aplikacji: \<**  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3. Dodaj następujące wpisy konfiguracji w  **\<elementach system. Web >** , aby odmówić użytkowników, wyłączyć uwierzytelnianie natywne i włączyć WIF do zarządzania uwierzytelnianiem.  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. Dodaj element System. WebServer >, który definiuje moduły uwierzytelniania federacyjnego.  **\<** Należy zauważyć, że atrybut *PublicKeyToken* musi być taki sam jak  **\<** atrybut PublicKeyToken dla wpisów configSections > dodane wcześniej:  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. Dodaj następujące wpisy konfiguracji powiązane z usługą Windows Identity Foundation i upewnij się, że adres URL i numer portu aplikacji ASP.NET są zgodne z wartościami we  **\<wpisie audienceUris >** , atrybut obszaru  **\<wsFederation >** element i atrybut odpowiedzi elementu wsFederation >.  **\<** Upewnij się również, że wartość wystawcy mieści się w adresie URL usługi tokenu zabezpieczającego (STS).  
  
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
 W tym kroku zostanie przetestowana aplikacja formularzy sieci Web ASP.NET skonfigurowana pod kątem uwierzytelniania opartego na oświadczeniach. Aby przeprowadzić podstawowy test, należy dodać kod, który będzie wyświetlał oświadczenia w tokenie wystawionym przez usługę tokenu zabezpieczającego (STS).  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>Aby przetestować aplikację formularza sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach  
  
1. Otwórz plik **default. aspx** w projekcie **TestApp** i Zastąp istniejący znacznik następującym znacznikiem:  
  
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
  
2. Zapisz plik **default. aspx**, a następnie otwórz jego kod w pliku o nazwie **default.aspx.cs**.  
  
    > [!NOTE]
    > **Default.aspx.cs** może być ukryty poniżej **default. aspx** w Eksplorator rozwiązań. Jeśli **default.aspx.cs** nie jest widoczny, rozwiń plik **default. aspx** , klikając trójkąt obok niego.  
  
3. Zastąp istniejący kod w metodzie **Page_Load** **default.aspx.cs** następującym kodem:  
  
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
  
4. Zapisz **default.aspx.cs**i skompiluj rozwiązanie.  
  
5. Uruchom rozwiązanie, naciskając klawisz **F5** .  
  
6. Powinna zostać wyświetlona strona zawierająca oświadczenia w tokenie, który został wystawiony przez usługę tokenu zabezpieczającego.
