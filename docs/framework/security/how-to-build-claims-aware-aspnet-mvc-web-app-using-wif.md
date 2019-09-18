---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji internetowej MVC ASP.NET za pomocą programu WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045445"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Instrukcje: Tworzenie obsługującej oświadczenia aplikacji internetowej MVC ASP.NET za pomocą programu WIF
## <a name="applies-to"></a>Dotyczy:  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® MVC  
  
## <a name="summary"></a>Podsumowanie  
 Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji sieci Web ASP.NET MVC z obsługą oświadczeń. Zawiera również instrukcje dotyczące testowania prostej aplikacji sieci Web ASP.NET MVC z obsługą oświadczeń w celu pomyślnego wdrożenia uwierzytelniania opartego na oświadczeniach. Ta instrukcja nie zawiera szczegółowych instrukcji dotyczących tworzenia usługi tokenu zabezpieczającego (STS) i zakłada, że już skonfigurowano usługę STS.  
  
## <a name="contents"></a>Spis treści  
  
- Cele  
  
- Zestawienie czynności  
  
- Krok 1 — Tworzenie prostej aplikacji ASP.NET MVC  
  
- Krok 2 — Konfigurowanie aplikacji ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach  
  
- Krok 3 — Przetestowanie rozwiązania  
  
- Elementy pokrewne  
  
## <a name="objectives"></a>Cele  
  
- Konfigurowanie aplikacji sieci Web ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach  
  
- Testowanie pomyślnej aplikacji sieci Web ASP.NET MVC z obsługą oświadczeń  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
- Krok 1 — Tworzenie prostej aplikacji ASP.NET MVC  
  
- Krok 2 — Konfigurowanie aplikacji ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach  
  
- Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>Krok 1 — Tworzenie prostej aplikacji ASP.NET MVC  
 W tym kroku zostanie utworzona nowa aplikacja ASP.NET MVC.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Aby utworzyć prostą aplikację ASP.NET MVC  
  
1. Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.  
  
2. W oknie **Nowy projekt** kliknij pozycję **ASP.NET aplikacji sieci Web MVC 3**.  
  
3. W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.  
  
4. W oknie dialogowym **Nowy projekt ASP.NET MVC 3** wybierz pozycję **aplikacja internetowa** z dostępnych szablonów, upewnij się, że jest ustawiony **aparat widoku** **Razor**, a następnie kliknij przycisk **OK**.  
  
5. Gdy zostanie otwarty nowy projekt, kliknij prawym przyciskiem myszy projekt **TestApp** w **Eksplorator rozwiązań** i wybierz opcję **Właściwości** .  
  
6. Na stronie właściwości projektu kliknij kartę **Sieć Web** po lewej stronie i upewnij się, że wybrano opcję **Użyj lokalnego serwera sieci Web usług IIS** .  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>Krok 2 — Konfigurowanie aplikacji ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach  
 W tym kroku dodasz wpisy konfiguracyjne do pliku konfiguracyjnego *Web. config* aplikacji sieci Web ASP.NET MVC, aby zapewnić obsługę oświadczeń.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>Aby skonfigurować aplikację ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach  
  
1. Dodaj następujące definicje sekcji konfiguracji do pliku konfiguracyjnego *Web. config* . Definiują sekcje konfiguracyjne wymagane przez program Windows Identity Foundation. Dodaj definicje bezpośrednio po  **\<elemencie Configuration >** otwierającym:  
  
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
  
4. Dodaj następujące wpisy konfiguracji powiązane z usługą Windows Identity Foundation i upewnij się, że adres URL i numer portu aplikacji ASP.NET są zgodne z wartościami we  **\<wpisie audienceUris >** , atrybut obszaru  **\<wsFederation >** element i atrybut odpowiedzi elementu wsFederation >.  **\<** Upewnij się również, że wartość **wystawcy** mieści się w adresie URL usługi tokenu zabezpieczającego (STS).  
  
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
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5. Dodaj odwołanie do <xref:System.IdentityModel> zestawu.  
  
6. Skompiluj rozwiązanie, aby upewnić się, że wystąpiły błędy.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku przetestujesz aplikację sieci Web ASP.NET MVC skonfigurowaną pod kątem uwierzytelniania opartego na oświadczeniach. Aby przeprowadzić podstawowy test, należy dodać prosty kod, który wyświetla oświadczenia w tokenie wystawionym przez usługę tokenu zabezpieczającego (STS).  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Aby przetestować aplikację ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach  
  
1. W **Eksplorator rozwiązań**rozwiń folder **controllers** i Otwórz plik *HomeController.cs* w edytorze. Dodaj następujący kod do metody **index** :  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. W **Eksplorator rozwiązań** rozwiń **Widok widoki** , a następnie folder Foldery **Główne** i Otwórz plik *index. cshtml* w edytorze. Usuń jego zawartość i Dodaj następujące znaczniki:  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3. Uruchom rozwiązanie, naciskając klawisz **F5** .  
  
4. Powinna zostać wyświetlona strona zawierająca oświadczenia w tokenie, który został wystawiony przez usługę tokenu zabezpieczającego.  
  
## <a name="related-items"></a>Elementy pokrewne  
  
- [Instrukcje: Tworzenie aplikacji opartych na oświadczeniach ASP.NET Web Forms przy użyciu WIF](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
