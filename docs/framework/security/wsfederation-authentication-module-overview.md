---
title: Omówienie modułu uwierzytelniania WSFederation
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
ms.openlocfilehash: f4dc63272c47dc0cd9eaa15986e4369d9d689b64
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592367"
---
# <a name="wsfederation-authentication-module-overview"></a>Omówienie modułu uwierzytelniania WSFederation
Windows Identity Foundation (WIF) obejmuje obsługę uwierzytelniania federacyjnego w aplikacjach ASP.NET, za pośrednictwem modułu uwierzytelniania WS-Federated (WS-Rozproszona). Ten temat pomoże zrozumieć, jak federacyjnego działania uwierzytelniania i jak z niej korzystać.  
  
### <a name="overview-of-federated-authentication"></a>Przegląd uwierzytelniania federacyjnego  
 Uwierzytelnianie federacyjne umożliwia usługa tokenu zabezpieczającego (STS) w jednej domenie zaufania, aby podać informacje uwierzytelniania do usługi STS w innej domenie zaufania, gdy istnieje relacja zaufania między tymi dwiema domenami. Na przykład jest wyświetlany na poniższej ilustracji:  
  
 ![Diagram przedstawiający Scenariusz uwierzytelniania federacyjnego.](./media/wsfederation-authentication-module-overview/federated-authentication.gif)  
  
1. Klient w domenie zaufania firmy Fabrikam wysyła żądanie do aplikacji w domenie Contoso zaufania jednostki uzależnionej strona (RP).  
  
2. Jednostki Uzależnionej przekierowuje klienta do usługi STS w domenie zaufania firmy Contoso. Ta usługa STS nie ma informacji o kliencie.  
  
3. Usługa tokenu Zabezpieczającego firmy Contoso przekierowuje klienta do usługi STS w domenie zaufania firmy Fabrikam, za pomocą którego zaufania domeny Contoso ma relację zaufania.  
  
4. Fabrikam STS weryfikuje tożsamość klienta i wystawia token zabezpieczający do usługi STS firmy Contoso.  
  
5. Usługa tokenu Zabezpieczającego firmy Contoso używa tokenu firmy Fabrikam, aby utworzyć swój własny token, który może być używany przez jednostkę Uzależnioną i wysyła je do jednostki Uzależnionej.  
  
6. Jednostki Uzależnionej wyodrębnia klienta oświadczenia w tokenie zabezpieczającym i sprawia, że decyzji o autoryzacji.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>Za pomocą modułu uwierzytelnianie Sfederowane za pomocą platformy ASP.NET  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WS-Rozproszona) jest moduł HTTP, które umożliwia dodanie federacyjnego uwierzytelniania [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji. Uwierzytelnianie federacyjne umożliwia logiki uwierzytelniania są obsługiwane przez usługę STS i pozwala skupić się na pisaniu logiki biznesowej.  
  
 Możesz skonfigurować Rozproszona WS, aby określić usługi STS, do których powinno zostać przekierowane nieuwierzytelnionych żądań. Program WIF umożliwia uwierzytelnianie użytkowników na dwa sposoby:  
  
1. Przekierowanie pasywnym: Gdy nieuwierzytelniony użytkownik próbuje uzyskać dostęp do chronionego zasobu, i chcesz po prostu przekierowywać je do usługi STS, bez konieczności strony logowania, to właściwe podejście. Usługa STS weryfikuje tożsamość użytkownika i wystawia token zabezpieczający, który zawiera odpowiednie oświadczenia dla tego użytkownika. Ta opcja wymaga usługi WS-Rozproszona mają zostać dodane w potoku moduły HTTP. Narzędzie tożsamości i dostępu dla programu Visual Studio 2012 umożliwia modyfikowanie pliku konfiguracji aplikacji do używania protokołu WS-Rozproszona i utworzyć Federację z usługą STS. Aby uzyskać więcej informacji, zobacz [narzędzie tożsamości i dostępu dla programu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2. Możesz wywołać <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> metody lub <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> metody z kodu powiązanego do strony logowania w aplikacji jednostki Uzależnionej.  
  
 W pasywnym przekierowanie cała komunikacja odbywa się za pośrednictwem odpowiedzi/przekierowanie z klienta (zazwyczaj przeglądarki). Rozproszona WS można dodać do potoku HTTP aplikacji, których ona obserwuje dla nieuwierzytelniony użytkownik zażąda i przekierowuje użytkowników do usługi STS określisz.  
  
 Rozproszona WS wywołuje również kilka zdarzeń, które można dostosować swoje funkcje w [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji.  
  
### <a name="how-the-ws-fam-works"></a>Jak działa Rozproszona WS  
 Rozproszona WS jest zaimplementowana w <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> klasy. Zazwyczaj dodajesz Rozproszona WS potoku HTTP usługi [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacja jednostki Uzależnionej. Gdy nieuwierzytelniony użytkownik próbuje uzyskać dostęp do chronionego zasobu, jednostkę Uzależnioną zwraca odpowiedź HTTP "401 Odmowa autoryzacji". Rozproszona WS przechwytuje odpowiedź zamiast umożliwiając klientowi otrzymasz go, a następnie go przekierowuje użytkownika do określonej usługi STS. Usługa STS wystawia token zabezpieczający, który Rozproszona WS ponownie przechwytuje. Rozproszona WS używa tokenu do utworzenia wystąpienia <xref:System.Security.Claims.ClaimsPrincipal> dla tego uwierzytelnionego użytkownika, które umożliwia regularne [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] mechanizmów autoryzacji do działania.  
  
 Ponieważ HTTP jest bezstanowy, potrzebujemy sposób, aby uniknąć powtarzania całego tego procesu, ilekroć dany użytkownik próbuje uzyskać dostęp do innego zasobu chronionego. Jest to miejsce <xref:System.IdentityModel.Services.SessionAuthenticationModule> pochodzą. Gdy Usługa STS wystawia token zabezpieczający dla użytkownika, <xref:System.IdentityModel.Services.SessionAuthenticationModule> również tworzy token zabezpieczający sesji dla użytkownika i umieszcza go w pliku cookie. Podczas kolejnych żądań <xref:System.IdentityModel.Services.SessionAuthenticationModule> przechwytuje ten plik cookie i używa ich do rekonstrukcji użytkownika <xref:System.Security.Claims.ClaimsPrincipal>.  
  
 Na poniższym diagramie przedstawiono ogólny przepływ informacji w przypadku przekierowania pasywnym. Żądanie jest automatycznie przekierowywane za pośrednictwem usługi STS, aby ustanowić poświadczeń bez strony logowania:  
  
 ![Diagram przedstawiający Zaloguj się przy użyciu przekierowania pasywnym.](./media/wsfederation-authentication-module-overview/sign-in-using-passive-redirect.gif)  
  
 Na poniższym diagramie przedstawiono bardziej szczegółowo na co się stanie po użytkownik został uwierzytelniony do usługi STS i ich tokeny zabezpieczające są przetwarzane przez <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>:  
  
 ![Czas do przetwarzania tokenu przy użyciu przekierowania pasywnym](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Na poniższym diagramie przedstawiono bardziej szczegółowo na co się stanie, gdy tokeny zabezpieczające użytkownika mają zostać zserializowane do plików cookie i są przechwytywane przez <xref:System.IdentityModel.Services.SessionAuthenticationModule>:  
  
 ![Schemat czasu SAM przedstawiający logowanie&#45;przy użyciu kontrolki](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Zdarzenia  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule>, a ich klasy nadrzędnej <xref:System.IdentityModel.Services.HttpModuleBase>, wywoływanie zdarzeń na różnych etapach cyklu przetwarzania żądania HTTP. Może obsługiwać te zdarzenia w `global.asax` pliku swoje [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji.  
  
- Infrastruktury ASP.NET wywołuje moduł <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metoda można zainicjować modułu.  
  
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> Zdarzenie jest zgłaszane w przypadku infrastruktury ASP.NET wywołuje <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metoda po raz pierwszy na jeden z modułów aplikacji, które wynikają z <xref:System.IdentityModel.Services.HttpModuleBase>. Ta metoda uzyskuje dostęp do statycznego <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwość, która powoduje, że konfiguracja, należy załadować z pliku Web.config. To zdarzenie jest inicjowane tylko przy pierwszym uzyskaniu dostępu do tej właściwości. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> Obiekt, który jest inicjowany z konfiguracji jest możliwy za pośrednictwem <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> właściwość w obsłudze zdarzeń. To zdarzenie służy do modyfikowania konfiguracji przed jej zastosowaniem do wszystkich modułów. Możesz dodać program obsługi dla tego zdarzenia w przypadku metody Application_Start:  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Zastępuje każdy moduł <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> i <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> metody abstrakcyjne. Pierwsza z tych metod dodaje programy obsługi zdarzeń potoku platformy ASP.NET, które mają znaczenie w odniesieniu do modułu. W większości przypadków wystarczy modułu domyślną implementację. Drugi z tych metod inicjuje właściwości modułu z jego <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> właściwości. (Jest kopii konfiguracji, który został wcześniej załadowany). Należy przesłonić tę metodę drugi, jeśli chcesz obsługiwać inicjowanie nowe właściwości z konfiguracji w klasach, które wynikają z <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> lub <xref:System.IdentityModel.Services.SessionAuthenticationModule>. W takiej sytuacji będzie trzeba będzie również dziedziczyć obiekty odpowiedniej konfiguracji w celu obsługi właściwości konfiguracji dodano; na przykład z <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>, lub <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
- Rozproszona WS zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> zdarzenie, kiedy przechwytuje on token zabezpieczający, który został wystawiony przez usługę STS.  
  
- Rozproszona WS zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> zdarzenie po jego zweryfikowaniu.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> Zgłasza <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> zdarzenia podczas tworzenia tokenu zabezpieczenia sesji dla użytkownika.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> Zgłasza <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> zdarzenie, kiedy przechwytuje on kolejne żądania z pliku cookie, który zawiera token zabezpieczający sesji.  
  
- Zanim Rozproszona WS przekierowuje użytkownika do wystawcy, zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> zdarzeń. Żądanie logowania usługi WS-Federation jest dostępna za pośrednictwem <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> właściwość <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> przekazany w zdarzeniu. Można zmodyfikować żądanie przed wysłaniem ten z wystawcą.  
  
- Rozproszona WS zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> zdarzenie, kiedy plik cookie są pomyślnie zapisywane, a użytkownik jest zalogowany.  
  
- Rozproszona WS zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> zdarzeń jeden raz w każdym sesji jako sesji jest zamykana w dół dla każdego użytkownika. Nie jest inicjowane, jeśli sesja jest zamknięty po stronie klienta (na przykład poprzez usunięcie pliku cookie sesji). W środowisku logowania jednokrotnego usługi STS IP mogą poprosić o każdej jednostki Uzależnionej, aby się wylogować, zbyt. To spowoduje również zgłosić to zdarzenie, za pomocą <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> równa `true`.  
  
> [!NOTE]
>  Nie należy używać <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwości podczas wszystkie zdarzenia wygenerowane przez <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> lub <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Jest to spowodowane <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> ustawiono po zakończeniu procesu uwierzytelniania, podczas gdy zdarzenia są wywoływane podczas procesu uwierzytelniania.  
  
### <a name="configuration-of-federated-authentication"></a>Konfiguracja uwierzytelniania federacyjnego  
 Rozproszona WS i SZYMON są konfigurowane za pośrednictwem [ \<federationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu. [ \<WsFederation >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) element podrzędny określa domyślne wartości dla właściwości Rozproszona WS; takie jak <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> właściwości i <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> właściwości. (Te wartości można zmienić na podstawie danego żądania przez zapewnienie obsługi niektóre zdarzenia usługi WS-Rozproszona; na przykład <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) Program obsługi plików cookie, który jest używany przez Menedżera kont zabezpieczeń są konfigurowane za pomocą [ \<cookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) elementu podrzędnego. Program WIF oferuje domyślny plik cookie program obsługi zaimplementowane w <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasy, która ma jego rozmiar fragmentu ustawiana za pośrednictwem [ \<chunkedCookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) elementu. `<federationConfiguration>` Odwołania do elementu <xref:System.IdentityModel.Configuration.IdentityConfiguration>, który udostępnia konfigurację dla innych składników programu WIF, używane w aplikacji, taką jak <xref:System.Security.Claims.ClaimsAuthenticationManager> i <xref:System.Security.Claims.ClaimsAuthorizationManager>. Konfiguracja tożsamości można odwoływać się jawnie określając nazwane [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element `identityConfigurationName` atrybutu `<federationConfiguration>` elementu. Jeśli konfiguracja tożsamości nie odwołuje się jawnie, będzie używany domyślnej konfiguracji tożsamości.  
  
 Następujący kod XML przedstawia konfigurację programu ASP.NET, jednostki uzależnionej aplikacji innej firmy (RP). <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> i <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> sekcji konfiguracji zostaną dodane w ramach `<configSections>` elementu. SAM i WS-Rozproszona są dodawane do moduły HTTP w ramach `<system.webServer>` / `<modules>` elementu. Na koniec składników WIF są skonfigurowane w ramach `<system.identityModel>` / `<identityConfiguration>` i `<system.identityModel.services>` / `<federationConfiguration>` elementów. Ta konfiguracja określa obsługi plik cookie z podziałem jest domyślny program obsługi plików cookie i nie jest typem obsługi plików cookie określona w `<cookieHandler>` elementu.  
  
> [!WARNING]
>  W poniższym przykładzie zarówno `requireHttps` atrybutu `<wsFederation>` elementu i `requireSsl` atrybutu `<cookieHandler>` elementu są `false`. Przedstawia informacje o potencjalnym zagrożeniem dla bezpieczeństwa. W środowisku produkcyjnym, należy ustawić obie te wartości `true`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- [\<federationConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
