---
title: Omówienie modułu uwierzytelniania WSFederation
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: abfd211629c3c77c87cbefbc27c6b18ab6872977
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wsfederation-authentication-module-overview"></a>Omówienie modułu uwierzytelniania WSFederation
Windows Identity Foundation (WIF) obejmuje obsługę uwierzytelniania federacyjnego w aplikacjach ASP.NET za pośrednictwem modułu uwierzytelniania WS-Federated (WS-FARMA). Ten temat pomoże Ci zrozumieć sposób federacyjnych działania uwierzytelniania i jak z niego korzystać.  
  
### <a name="overview-of-federated-authentication"></a>Omówienie uwierzytelniania federacyjnego  
 Uwierzytelnianie Sfederowane umożliwia zabezpieczeń tokenu usługi (STS) w jednej domenie zaufania zapewnienie informacji o uwierzytelnianiu usługi tokenu Zabezpieczającego w innej domenie zaufania, gdy istnieje relacja zaufania między tymi dwiema domenami. Na przykład przedstawiono na poniższej ilustracji.  
  
 ![Scenariusz uwierzytelniania federacyjnego](../../../docs/framework/security/media/federatedauthentication.gif "FederatedAuthentication")  
  
1.  Klient w domenie zaufania firmy Fabrikam wysyła żądanie do aplikacji w domenie Contoso zaufania jednostki uzależnionej strony (RP).  
  
2.  RP przekierowuje klienta do usługi tokenu Zabezpieczającego w relacji zaufania domeny Contoso. Tej usługi STS nie ma informacji o kliencie.  
  
3.  Usługa tokenu Zabezpieczającego firmy Contoso przekierowuje klienta do usługi tokenu Zabezpieczającego w domenie zaufania firmy Fabrikam, z którym zaufania domeny Contoso ma relację zaufania.  
  
4.  Usługa tokenu Zabezpieczającego firmy Fabrikam weryfikuje tożsamości klienta i wystawia token zabezpieczający Contoso STS.  
  
5.  Usługa tokenu Zabezpieczającego firmy Contoso używa tokenu Fabrikam do utworzenia własnego tokenu, które mogą być używane przez planu odzyskiwania i wysyła je do planu odzyskiwania.  
  
6.  RP wyodrębnia oświadczeń klienta z tokenu zabezpieczeń i sprawia, że decyzję dotyczącą autoryzacji.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>Program ASP.NET przy użyciu modułu uwierzytelniania federacyjnego  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WS-FARMA) jest moduł protokołu HTTP, które umożliwia dodanie uwierzytelniania federacyjnego do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji. Uwierzytelnianie Sfederowane umożliwia logika uwierzytelniania są obsługiwane przez usługę STS i pozwala skupić się na temat pisania logiki biznesowej.  
  
 Możesz skonfigurować WS-FARMA, aby określić STS, do których mają być przekierowywane nieuwierzytelnione żądania. WIF umożliwia uwierzytelnianie użytkowników na dwa sposoby:  
  
1.  Przekierowanie pasywnym: gdy nieuwierzytelniony użytkownik próbuje uzyskać dostęp do chronionych zasobów i chcesz po prostu przekierowanie do usługi tokenu Zabezpieczającego bez konieczności strony logowania, a następnie jest prawo podejście. Usługa tokenu Zabezpieczającego weryfikuje tożsamość użytkownika i wystawia token zabezpieczający, który zawiera oświadczenia właściwe dla tego użytkownika. Ta opcja wymaga protokołu WS-FARMA do dodania w potoku moduły HTTP. Tożsamość i narzędzie dostępu do programu Visual Studio 2012 służy do modyfikowania pliku konfiguracji aplikacji do użycia protokołu WS-FARMA i możliwości utworzenia federacji z usługi tokenu Zabezpieczającego. Aby uzyskać więcej informacji, zobacz [tożsamości i dostępu do narzędzi dla programu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2.  Możesz wywołać <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> metody lub <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> metody z kodu powiązanego do strony logowania w aplikacji planu odzyskiwania.  
  
 W pasywnym przekierowania cała komunikacja odbywa się za pośrednictwem odpowiedzi/przekierowanie z klienta (zazwyczaj przeglądarki). FARMA WS można dodać do potoku HTTP aplikacji, w którym go oczekuje dla nieuwierzytelniony użytkownik zażąda i przekierowuje użytkowników do usługi STS określisz.  
  
 FARMA WS zgłasza również kilka zdarzeń, które pozwalają dostosować jego funkcjonalność w [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji.  
  
### <a name="how-the-ws-fam-works"></a>Jak działa FARMA WS  
 FARMA WS jest zaimplementowana w <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> klasy. Zazwyczaj dodaje się FARMA WS do potoku HTTP z Twojej [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] RP aplikacji. Gdy nieuwierzytelniony użytkownik próbuje uzyskać dostęp do chronionych zasobów, RP zwraca odpowiedź HTTP "401 Odmowa autoryzacji". FARMA WS przechwytuje tej odpowiedzi zamiast zezwalać otrzymywanie go, a następnie go przekierowuje użytkownika do określonej usługi STS. Usługa tokenu Zabezpieczającego wystawia token zabezpieczający, który ponownie przechwytuje WS-FARMA. FARMA WS używa tokenu do utworzenia wystąpienia <xref:System.Security.Claims.ClaimsPrincipal> dla tego uwierzytelnionego użytkownika, co pozwala regular [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] mechanizmów autoryzacji do działania.  
  
 Ponieważ HTTP jest bezstanowych, potrzebujemy sposób, aby uniknąć powtarzania całego tego procesu za każdym razem, gdy użytkownik spróbuje uzyskać dostęp do innego zasobu chronionego. Jest to, gdy <xref:System.IdentityModel.Services.SessionAuthenticationModule> polega na. Gdy usługa tokenu Zabezpieczającego wystawia token zabezpieczający dla użytkownika, <xref:System.IdentityModel.Services.SessionAuthenticationModule> również tworzy tokenu zabezpieczającego sesji użytkownika i umieszczenie go w pliku cookie. W kolejnych żądań <xref:System.IdentityModel.Services.SessionAuthenticationModule> przechwytuje ten plik cookie i używa go do rekonstrukcji użytkownika <xref:System.Security.Claims.ClaimsPrincipal>.  
  
 Na poniższym diagramie przedstawiono ogólny przepływ informacji w przypadku przekierowania pasywnych. Żądanie jest automatycznie przekierowywane za pośrednictwem usługi STS ustanowienie poświadczenia bez strony logowania:  
  
 ![Diagram czasowa znaku&#45;się przy użyciu przekierowania pasywnym](../../../docs/framework/security/media/signinusingpassiveredirect.gif "SignInUsingPassiveRedirect")  
  
 Na poniższym diagramie przedstawiono bardziej szczegółowo na co się dzieje, gdy użytkownik został uwierzytelniony za pomocą usługi STS i ich tokeny zabezpieczające są przetwarzane przez <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>:  
  
 ![Czasy do przetwarzania tokenu przy użyciu przekierowania pasywnym](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Na poniższym diagramie przedstawiono bardziej szczegółowo na co się dzieje, gdy tokeny zabezpieczające użytkownika ma zostać zserializowane do plików cookie i są przechwytywane przez <xref:System.IdentityModel.Services.SessionAuthenticationModule>:  
  
 ![SAM chronometrażu diagram przedstawiający znak&#45;za pomocą formantów](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Zdarzenia  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule>i ich klasy nadrzędnej <xref:System.IdentityModel.Services.HttpModuleBase>, wywoływanie zdarzeń na różnych etapach przetwarzania żądania HTTP. Można obsługiwać te zdarzenia w `global.asax` pliku z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji.  
  
-   Infrastruktury ASP.NET wywołuje modułu <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metody można zainicjować modułu.  
  
-   <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> Zdarzenie jest zgłaszane, gdy wywołuje infrastruktury ASP.NET <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metody po raz pierwszy na jeden z modułów aplikacji, które pochodzą z <xref:System.IdentityModel.Services.HttpModuleBase>. Ta metoda uzyskuje dostęp do statycznych <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwość, która powoduje, że konfiguracja załadować z pliku Web.config. To zdarzenie jest wywoływane tylko po raz pierwszy uzyskać dostępu do tej właściwości. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> Obiekt, który został zainicjowany z konfiguracji jest możliwy za pośrednictwem <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> właściwości w obsłudze zdarzeń. To zdarzenie służy do modyfikowania konfiguracji przed jej zastosowaniem do żadnych modułów. Można dodać obsługi dla tego zdarzenia w metody Application_Start:  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Każdy moduł zastępuje <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> i <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> metody abstrakcyjnej. Pierwsza z tych metod dodaje obsługę zdarzeń potoku platformy ASP.NET, które mogą być przydatne do modułu. W większości przypadków wystarczy modułu domyślną implementację. Drugi z tych metod inicjuje właściwości modułu z jego <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> właściwości. (Jest to kopia konfiguracji, który został wcześniej załadowany). Należy przesłonić tę metodę drugiego, jeśli mają być obsługiwane w klasach pochodzących od inicjowania nowe właściwości z konfiguracji <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> lub <xref:System.IdentityModel.Services.SessionAuthenticationModule>. W takich przypadkach również konieczne będzie dziedziczyć odpowiednia konfiguracja obiekty obsługują właściwości konfiguracji dodano; na przykład z <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>, lub <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
-   FARMA WS zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> zdarzenie, gdy jego przechwytuje tokenu zabezpieczającego, które zostały wystawione przez usługę STS.  
  
-   FARMA WS zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> zdarzenia po został zweryfikowany tokenu.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> Zgłasza <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> zdarzeń podczas tworzenia tokenu zabezpieczającego sesji użytkownika.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> Zgłasza <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> zdarzenie, gdy przechwytuje on kolejne żądania z pliku cookie, który zawiera token zabezpieczający sesji.  
  
-   Przed FARMA WS przekierowuje użytkownika do wystawcy, zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> zdarzeń. WS-Federation żądania logowania jest dostępna za pośrednictwem <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> właściwość <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> przekazany w zdarzeniu. Można zmodyfikować żądanie przed wysłaniem to wystawcy.  
  
-   FARMA WS zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> zdarzenie, gdy plik cookie jest pomyślnie zapisane i użytkownik jest zalogowany.  
  
-   FARMA WS zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> zdarzeń jeden raz w każdym sesji jako sesja zostaje zamknięte w dół dla każdego użytkownika. Nie jest wywoływane, gdy sesja jest zamknięte po stronie klienta (na przykład przez usunięcie pliku cookie sesji). W środowisku logowania jednokrotnego usługi STS protokołu IP mogą żądać każdego planu odzyskiwania, aby się wylogować, zbyt. To spowoduje również zgłosić to zdarzenie, z <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> ustawioną `true`.  
  
> [!NOTE]
>  Nie należy używać <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwości podczas wszystkie zdarzenia wygenerowane przez <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> lub <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Jest to spowodowane <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> jest ustawiany po procesie uwierzytelniania, gdy zdarzenia są wywoływane podczas procesu uwierzytelniania.  
  
### <a name="configuration-of-federated-authentication"></a>Konfiguracja uwierzytelniania federacyjnego  
 FARMA WS i SAM są skonfigurowane za pomocą [ \<federationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu. [ \<WsFederation >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) element podrzędny konfiguruje domyślne wartości dla właściwości WS-FARMA; takich jak <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> właściwości i <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> właściwości. (Te wartości można zmieniać na podstawie danego żądania przez zapewnienie obsługi dla niektórych zdarzeń usługi WS-FARMA; na przykład <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) Program obsługi plików cookie, który jest używany przez Menedżera kont zabezpieczeń są konfigurowane za pomocą [ \<cookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) element podrzędny. WIF udostępnia domyślny plik cookie program obsługi w <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy, która może mieć rozmiaru fragmentu ustawiana za pośrednictwem [ \<chunkedCookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) elementu. `<federationConfiguration>` Odwołania do elementu <xref:System.IdentityModel.Configuration.IdentityConfiguration>, który udostępnia konfigurację dla innych składników WIF używane w aplikacji, takich jak <xref:System.Security.Claims.ClaimsAuthenticationManager> i <xref:System.Security.Claims.ClaimsAuthorizationManager>. Konfiguracja tożsamości odwołania mogą dotyczyć jawnie określając nazwane [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element `identityConfigurationName` atrybutu `<federationConfiguration>` elementu. Jeśli konfiguracja tożsamości nie jest wywoływane jawnie, będzie używany domyślnej konfiguracji tożsamości.  
  
 Następujący kod XML zawiera konfigurację programu ASP.NET jednostki uzależnionej (RP) aplikacji. <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> i <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> sekcji konfiguracji są dodawane w obszarze `<configSections>` elementu. SAM i WS-FARMA są dodawane do modułów HTTP w obszarze `<system.webServer>` / `<modules>` elementu. Na koniec składników WIF są skonfigurowane w obszarze `<system.identityModel>` / `<identityConfiguration>` i `<system.identityModel.services>` / `<federationConfiguration>` elementów. Ta konfiguracja określa obsługi podzielony plik cookie jest domyślny program obsługi plików cookie i nie jest typem obsługi plików cookie określona w `<cookieHandler>` elementu.  
  
> [!WARNING]
>  W poniższym przykładzie zarówno `requireHttps` atrybutu `<wsFederation>` elementu i `requireSsl` atrybutu `<cookieHandler>` są elementu `false`. Stanowi to potencjalne zagrożenie bezpieczeństwa. W środowisku produkcyjnym, należy ustawić obie te wartości `true`.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  ...  
  
  <system.webServer>  
    <modules>  
      <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
    </modules>  
  </system.webServer>  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost:50969/" />  
      </audienceUris>  
      <certificateValidation certificateValidationMode="None" />  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
        <trustedIssuers>  
          <add thumbprint="9B74CB2F320F7AAFC156E1252270B1DC01EF40D0" name="LocalSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
    </identityConfiguration>  
  </system.identityModel>  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:15839/wsFederationSTS/Issue" realm="http://localhost:50969/" reply="http://localhost:50969/" requireHttps="false" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 [\<federationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
