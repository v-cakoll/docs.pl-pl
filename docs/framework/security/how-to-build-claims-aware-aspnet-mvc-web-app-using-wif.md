---
title: 'Porady: Tworzenie aplikacji sieci Web obsługujący oświadczenia platformy ASP.NET MVC za pomocą WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 146724f31e1d09f09f94d102366539dc79ddfe02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Porady: Tworzenie aplikacji sieci Web obsługujący oświadczenia platformy ASP.NET MVC za pomocą WIF
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® MVC  
  
## <a name="summary"></a>Podsumowanie  
 To instrukcje zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji sieci web platformy ASP.NET MVC obsługujący oświadczenia. Zawiera również instrukcje dotyczące testowania prostą aplikację sieci web obsługujący oświadczenia ASP.NET MVC w dla pomyślnego wykonania uwierzytelniania opartego na oświadczeniach. Ta porada nie ma szczegółowe instrukcje dotyczące tworzenia tokenu usługi zabezpieczenia (STS) i przyjęto założenie, że zostały już skonfigurowane usługi tokenu Zabezpieczającego.  
  
## <a name="contents"></a>Spis treści  
  
-   Cele  
  
-   Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji proste ASP.NET MVC  
  
-   Krok 2: Konfigurowanie aplikacji ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
-   Elementy pokrewne  
  
## <a name="objectives"></a>Cele  
  
-   Konfigurowanie aplikacji sieci web platformy ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
-   Testowanie pomyślne obsługujący oświadczenia aplikacji sieci web platformy ASP.NET MVC  
  
## <a name="summary-of-steps"></a>Zestawienie czynności  
  
-   Krok 1: tworzenie aplikacji proste ASP.NET MVC  
  
-   Krok 2: Konfigurowanie aplikacji ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
-   Krok 3 — Przetestowanie rozwiązania  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>Krok 1: tworzenie aplikacji proste ASP.NET MVC  
 W tym kroku utworzysz nową aplikację ASP.NET MVC.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Aby utworzyć prostą aplikację platformy ASP.NET MVC  
  
1.  Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.  
  
2.  W **nowy projekt** okna, kliknij przycisk **aplikacji sieci Web programu ASP.NET MVC 3**.  
  
3.  W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.  
  
4.  W **nowy projekt programu ASP.NET MVC 3** okno dialogowe, wybierz opcję **aplikacji internetowej** spośród dostępnych szablonów, upewnij się, **aparat widoku** ustawiono **Razor**, a następnie kliknij przycisk **OK**.  
  
5.  Gdy zostanie otwarty nowy projekt, kliknij prawym przyciskiem myszy **TestApp** projektu w **Eksploratora rozwiązań** i wybierz **właściwości** opcji.  
  
6.  Na stronie właściwości projektu, kliknij na **Web** karcie po lewej stronie i upewnij się, że **użycia lokalnego serwera sieci Web usług IIS** opcja jest zaznaczona.  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>Krok 2: Konfigurowanie aplikacji ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
 W tym kroku zostanie dodania wpisów konfiguracji do *Web.config* pliku konfiguracji aplikacji sieci web platformy ASP.NET MVC, aby była obsługujący oświadczenia.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>Aby skonfigurować aplikację ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
1.  Dodaj następujące definicje sekcji konfiguracji do *Web.config* pliku konfiguracji. Zdefiniuj tych sekcji konfiguracyjnych wymaganych przez środowisko Windows Identity Foundation. Dodawanie definicji natychmiast po  **\<konfiguracji >** otwarcia elementu:  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  Dodaj  **\<lokalizacji >** elementu, który umożliwia dostęp do metadanych Federacji aplikacji:  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  Dodaj następujące pozycje konfiguracji w ramach  **\<system.web >** elementy, aby uniemożliwić użytkownikom, Wyłącz uwierzytelnianie macierzystego i Włącz WIF zarządzać uwierzytelnianiem.  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  Dodaj następujące Windows Identity Foundation powiązane pozycje konfiguracji i upewnij się, że adres URL aplikacji platformy ASP.NET i numer portu pasują do wartości w  **\<audienceUris >** wpisu, **obszaru**  atrybutu  **\<wsFederation >** elementu i **odpowiedzi** atrybutu  **\<wsFederation >** elementu. Ponadto upewnij się, że **wystawcy** wartość pasuje do adresu URL zabezpieczeń usługi tokenów (STS).  
  
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
  
5.  Dodaj odwołanie do <xref:System.IdentityModel> zestawu.  
  
6.  Skompiluj rozwiązanie, aby upewnij się, że ma błędów.  
  
## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania  
 W tym kroku zostanie testów aplikacji sieci web platformy ASP.NET MVC skonfigurowany do uwierzytelniania opartego na oświadczeniach. Aby wykonać podstawowy test doda prostego kodu, który wyświetla oświadczenia w tokenie wystawiony przez zabezpieczenia usługi tokenów (STS).  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Aby przetestować aplikację ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **kontrolerów** folderu i Otwórz *HomeController.cs* plik w edytorze. Dodaj następujący kod do **indeksu** metody:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  W **Eksploratora rozwiązań** rozwiń **widoków** , a następnie **Home** folderów i Otwórz *Index.cshtml* plik w edytorze. Usuń jej zawartości i Dodaj następujący kod:  
  
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
  
3.  Uruchom rozwiązanie, naciskając klawisz **F5** klucza.  
  
4.  Powinna pojawić na stronie zostaną wyświetlone oświadczenia w tokenie, który został wystawiony przez usługi tokenu zabezpieczającego.  
  
## <a name="related-items"></a>Elementy pokrewne  
  
-   [Instrukcje: tworzenie obsługującej oświadczenia aplikacji formularzy internetowych ASP.NET za pomocą programu WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
