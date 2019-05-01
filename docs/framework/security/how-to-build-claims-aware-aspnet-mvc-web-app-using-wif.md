---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji internetowej MVC ASP.NET za pomocą programu WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 04861b8c3f2673a5cd093be1351928b1da487147
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940520"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Instrukcje: Tworzenie obsługującej oświadczenia aplikacji internetowej MVC ASP.NET za pomocą programu WIF
## <a name="applies-to"></a>Dotyczy:  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® MVC  
  
## <a name="summary"></a>Podsumowanie  
 Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostego obsługującej oświadczenia aplikacji sieci web platformy ASP.NET MVC. Zawiera również instrukcje dotyczące testowania prostą aplikację sieci web obsługującej oświadczenia platformy ASP.NET MVC w dla pomyślnego wdrożenia opartego na oświadczeniach uwierzytelniania. Niniejszy instruktaż nie zawiera szczegółowych instrukcji tworzenia Usługa tokenu zabezpieczającego (STS), a przyjęto założenie, że zostały już skonfigurowane usługi tokenu Zabezpieczającego.  
  
## <a name="contents"></a>Spis treści  
  
- Cele  
  
- Zestawienie czynności  
  
- Krok 1 — utworzenie aplikacji proste platformy ASP.NET MVC  
  
- Krok 2 — Konfigurowanie aplikacji platformy ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
- Krok 3 — Przetestowanie rozwiązania  
  
- Powiązane elementy  
  
## <a name="objectives"></a>Cele  
  
- Konfigurowanie aplikacji sieci web platformy ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
- Testowanie pomyślne obsługującej oświadczenia aplikacji sieci web platformy ASP.NET MVC  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
- Krok 1 — utworzenie aplikacji proste platformy ASP.NET MVC  
  
- Krok 2 — Konfigurowanie aplikacji platformy ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
- Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>Krok 1 — utworzenie aplikacji proste platformy ASP.NET MVC  
 W tym kroku utworzysz nową aplikację ASP.NET MVC.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Aby utworzyć prostą aplikację platformy ASP.NET MVC  
  
1. Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.  
  
2. W **nowy projekt** okna, kliknij przycisk **aplikacji sieci Web programu ASP.NET MVC 3**.  
  
3. W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
4. W **nowego projektu programu ASP.NET MVC 3** okno dialogowe, wybierz opcję **aplikacji internetowej** spośród dostępnych szablonów, upewnij się, **aparat widoku** ustawiono **Razor**, a następnie kliknij przycisk **OK**.  
  
5. Po otwarciu nowego projektu, kliknij prawym przyciskiem myszy **TestApp** projektu w **Eksploratora rozwiązań** i wybierz **właściwości** opcji.  
  
6. Na stronie właściwości projektu, kliknąć **Web** karcie po lewej stronie, a następnie upewnij się, że **użycia lokalnego serwera sieci Web usług IIS** opcja jest zaznaczona.  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>Krok 2 — Konfigurowanie aplikacji platformy ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
 W tym kroku dodasz wpisy konfiguracji *Web.config* pliku konfiguracji aplikacji sieci web platformy ASP.NET MVC, aby obsługujących oświadczenia.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>Aby skonfigurować aplikację ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
1. Dodaj następujące definicje konfiguracji w sekcji, aby *Web.config* pliku konfiguracji. Te definiują sekcji konfiguracji wymaganych przez program Windows Identity Foundation. Dodaj definicje natychmiast po  **\<konfiguracji >** otwarcia elementu:  
  
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
  
4. Dodaj następujące Windows Identity Foundation powiązane wpisy konfiguracji i upewnij się, że adres URL aplikacji ASP.NET i numer portu pasuje do wartości w  **\<audienceUris >** wpisu **obszaru**  atrybutu  **\<wsFederation >** elementu, a **odpowiedzi** atrybutu  **\<wsFederation >** elementu. Ponadto upewnij się, że **wystawcy** pasuje do wartości adresu URL Usługa tokenu zabezpieczającego (STS).  
  
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
  
6. Skompiluj rozwiązanie, aby upewnić się, że ma błędów.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku przetestujesz aplikację sieci web platformy ASP.NET MVC, skonfigurowany do uwierzytelniania opartego na oświadczeniach. Aby wykonać podstawowy test należy dodać prosty kod, który przedstawia oświadczenia w tokenie, wystawiony przez Usługa tokenu zabezpieczającego (STS).  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Aby przetestować aplikację ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
1. W **Eksploratora rozwiązań**, rozwiń węzeł **kontrolerów** folder i Otwórz *HomeController.cs* plik w edytorze. Dodaj następujący kod do **indeksu** metody:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. W **Eksploratora rozwiązań** rozwiń **widoków** i następnie **Home** folderów i Otwórz *Index.cshtml* plik w edytorze. Usunąć jej zawartość i Dodaj następujący kod:  
  
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
  
3. Uruchom rozwiązanie, naciskając klawisz **F5** klucza.  
  
4. Powinno zostać wyświetlone ze stroną, które zostaną wyświetlone oświadczenia w tokenie, który został wystawiony przez usługę tokenu zabezpieczającego.  
  
## <a name="related-items"></a>Powiązane elementy  
  
- [Instrukcje: Tworzenie aplikacji formularzy sieci Web programu ASP.NET obsługującej oświadczenia za pomocą programu WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
