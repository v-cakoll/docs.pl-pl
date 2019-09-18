---
title: Omówienie modułu uwierzytelniania WSFederation
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
ms.openlocfilehash: 26cd022ded8dddcfcf695c89b3cf4b90d3ceb2ef
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044935"
---
# <a name="wsfederation-authentication-module-overview"></a>Omówienie modułu uwierzytelniania WSFederation
Windows Identity Foundation (WIF) obejmuje obsługę uwierzytelniania federacyjnego w aplikacjach ASP.NET za pomocą modułu uwierzytelniania WS-Federation (WS-Farma). Ten temat pomoże Ci zrozumieć, jak działa uwierzytelnianie federacyjne i jak z niego korzystać.  
  
### <a name="overview-of-federated-authentication"></a>Omówienie uwierzytelniania federacyjnego  
 Uwierzytelnianie federacyjne pozwala usłudze tokenu zabezpieczającego (STS) w jednej domenie zaufania na udostępnianie informacji uwierzytelniania do usługi STS w innej domenie zaufania, gdy istnieje relacja zaufania między tymi dwiema domenami. Przykład ten przedstawiono na poniższej ilustracji:  
  
 ![Diagram przedstawiający scenariusz uwierzytelniania federacyjnego.](./media/wsfederation-authentication-module-overview/federated-authentication.gif)  
  
1. Klient w domenie zaufania Fabrikam wysyła żądanie do aplikacji jednostki uzależnionej (RP) w domenie zaufania contoso.  
  
2. Element RP przekierowuje klienta do usługi STS w domenie zaufania contoso. Ta usługa STS nie ma informacji o kliencie.  
  
3. Program contoso STS przekierowuje klienta do usługi STS w domenie zaufania firmy Fabrikam, z którą domena zaufania Contoso ma relację zaufania.  
  
4. Firma Fabrikam STS weryfikuje tożsamość klienta i wystawia token zabezpieczający w usłudze STS firmy Contoso.  
  
5. Firma Contoso wykorzysta token firmy Fabrikam, aby utworzyć własny token, który może być używany przez RP, i wysyła go do jednostki UZALEŻNIONej.  
  
6. RP wyodrębni oświadczenia klienta z tokenu zabezpieczającego i podejmuje decyzję o autoryzacji.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>Używanie modułu uwierzytelniania federacyjnego z ASP.NET  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WS-Farma) jest modułem HTTP, który umożliwia dodawanie uwierzytelniania federacyjnego do aplikacji ASP.NET. Uwierzytelnianie federacyjne umożliwia obsługę logiki uwierzytelniania przez usługę STS i pozwala skupić się na tworzeniu logiki biznesowej.  
  
 Należy skonfigurować usługę WS-Farma, aby określić usługę STS, do której mają być przekierowywane żądania nieuwierzytelnione. WIF umożliwia uwierzytelnianie użytkownika na dwa sposoby:  
  
1. Przekierowanie pasywne: Gdy nieuwierzytelniony użytkownik próbuje uzyskać dostęp do chronionego zasobu i chcesz po prostu przekierować je do usługi STS bez konieczności korzystania ze strony logowania, to jest to odpowiednie podejście. Usługa STS weryfikuje tożsamość użytkownika i wystawia token zabezpieczający, który zawiera odpowiednie oświadczenia dla tego użytkownika. Ta opcja wymaga dodania protokołu WS-Farma w potoku modułów HTTP. Za pomocą narzędzia Identity and Access Tool dla programu Visual Studio 2012 można zmodyfikować plik konfiguracji aplikacji w taki sposób, aby korzystał z protokołu WS-Farma i sfederować z usługą STS. Aby uzyskać więcej informacji, zobacz [Narzędzie tożsamości i dostępu dla programu Visual Studio 2012](identity-and-access-tool-for-vs.md).  
  
2. Można wywołać <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> metodę <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> lub metodę z kodu powiązanego ze stroną logowania w aplikacji RP.  
  
 W przypadku przekierowania pasywnego cała komunikacja odbywa się za pośrednictwem odpowiedzi/przekierowania z klienta (zazwyczaj jest to przeglądarka). Można dodać usługę WS-Farma do potoku HTTP aplikacji, gdzie obserwuje nieuwierzytelnione żądania użytkowników i przekierowuje użytkowników do określonej usługi STS.  
  
 Usługa WS-Farma wywołuje również kilka zdarzeń, które umożliwiają dostosowanie jej funkcji w aplikacji ASP.NET.  
  
### <a name="how-the-ws-fam-works"></a>Jak działa usługa WS-Farma  
 Usługa WS-Farma jest zaimplementowana <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> w klasie. Zazwyczaj należy dodać element WS-Farma do potoku HTTP aplikacji ASP.NET RP. Gdy nieuwierzytelniony użytkownik próbuje uzyskać dostęp do chronionego zasobu, jednostka UZALEŻNIONa zwróci odpowiedź HTTP "odmowa autoryzacji" 401. Usługa WS-Farma przechwytuje tę odpowiedź zamiast zezwalać klientowi na ich odbieranie, przekierowuje użytkownika do określonego programu STS. Usługa STS wystawia token zabezpieczający, który ponownie przechwytuje WS-Farma. Usługa WS-Farma używa tokenu do tworzenia wystąpienia <xref:System.Security.Claims.ClaimsPrincipal> dla uwierzytelnionego użytkownika, który umożliwia regularne .NET Framework mechanizmów autoryzacji.  
  
 Ponieważ protokół HTTP jest bezstanowy, musimy mieć możliwość uniknięcia powtarzania całego procesu za każdym razem, gdy użytkownik próbuje uzyskać dostęp do innego chronionego zasobu. Jest to miejsce, <xref:System.IdentityModel.Services.SessionAuthenticationModule> w którym się znajduje. Gdy usługa STS wystawia token zabezpieczający dla użytkownika, <xref:System.IdentityModel.Services.SessionAuthenticationModule> program tworzy również token zabezpieczający sesji dla użytkownika i umieszcza go w pliku cookie. W przypadku <xref:System.IdentityModel.Services.SessionAuthenticationModule> kolejnych żądań przechwytuje ten plik cookie i używa go do odbudowy <xref:System.Security.Claims.ClaimsPrincipal>użytkownika.  
  
 Na poniższym diagramie przedstawiono ogólny przepływ informacji w przypadku pasywnego przekierowania. Żądanie jest automatycznie przekierowywane za pośrednictwem usługi STS w celu ustanowienia poświadczeń bez strony logowania:  
  
 ![Diagram przedstawiający Logowanie przy użyciu przekierowania pasywnego.](./media/wsfederation-authentication-module-overview/sign-in-using-passive-redirect.gif)  
  
 Na poniższym diagramie przedstawiono szczegółowe informacje na temat tego, co się dzieje, gdy użytkownik został uwierzytelniony do usługi STS, a ich tokeny zabezpieczające są przetwarzane przez <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>:  
  
 ![Czas przetwarzania tokenu przy użyciu przekierowania pasywnego](./media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Na poniższym diagramie przedstawiono szczegółowe informacje na temat tego, co się dzieje, gdy tokeny zabezpieczające użytkownika zostały zserializowane do plików cookie i <xref:System.IdentityModel.Services.SessionAuthenticationModule>są przechwytywane przez:  
  
 ![Diagram chronometrażu sam przedstawiający logowanie&#45;przy użyciu kontrolek](./media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Zdarzenia  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule>, i ich <xref:System.IdentityModel.Services.HttpModuleBase>klasy nadrzędnej, powodują wygenerowanie zdarzeń na różnych etapach przetwarzania żądania HTTP. Te zdarzenia można obsłużyć w `global.asax` pliku aplikacji ASP.NET.  
  
- Infrastruktura ASP.NET wywołuje <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> metodę modułu w celu zainicjowania modułu.  
  
- Zdarzenie jest zgłaszane, gdy infrastruktura ASP.NET <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> wywołuje metodę po raz pierwszy na jednej z modułów aplikacji, które pochodzą z <xref:System.IdentityModel.Services.HttpModuleBase>. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> Ta metoda uzyskuje dostęp do <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> właściwości statycznej, która powoduje, że konfiguracja zostanie załadowana z pliku Web. config. To zdarzenie jest wywoływane tylko podczas pierwszego uzyskiwania dostępu do tej właściwości. Do obiektu, który jest zainicjowany z konfiguracji, <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> można uzyskać dostęp za pośrednictwem właściwości w programie obsługi zdarzeń. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> To zdarzenie służy do modyfikowania konfiguracji przed jej zastosowaniem do dowolnych modułów. Można dodać procedurę obsługi dla tego zdarzenia w metodzie Application_Start:  
  
    ```csharp
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Każdy moduł zastępuje <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> metody i <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> abstrakcyjne. Pierwszy z tych metod dodaje programy obsługi dla zdarzeń potoku ASP.NET, które są istotne dla modułu. W większości przypadków wystarcza domyślna implementacja modułu. Druga z tych metod inicjuje właściwości modułu z jego <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> właściwością. (Jest to kopia konfiguracji, która została załadowana wcześniej). Może być konieczne przesłonięcie tej drugiej metody, jeśli chcesz obsługiwać inicjalizację nowych właściwości z konfiguracji w klasach, które pochodzą z <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> lub <xref:System.IdentityModel.Services.SessionAuthenticationModule>. W takich przypadkach należy również utworzyć z odpowiednich obiektów konfiguracji, aby zapewnić obsługę dodanych właściwości konfiguracji; na przykład z <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>, lub <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
- Usługa WS-Farma zgłasza zdarzenie <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> , gdy przechwytuje token zabezpieczający, który został wystawiony przez usługę STS.  
  
- Usługa WS-Farma zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> zdarzenie po zweryfikowaniu tokenu.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> Wywołujezdarzeniepodczastworzeniatokenu<xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> zabezpieczeń sesji dla użytkownika.  
  
- <xref:System.IdentityModel.Services.SessionAuthenticationModule> Wywołujezdarzenie,gdyprzechwytujekolejneżądaniazplikiemcookiezawierającym<xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> token zabezpieczeń sesji.  
  
- Zanim Usługa WS-Farma przekierowuje użytkownika do wystawcy, zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> zdarzenie. Żądanie logowania za pomocą protokołu WS-Federation jest dostępne przez <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> Właściwość <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> przekazaną w zdarzeniu. Możesz zmodyfikować żądanie przed wysłaniem go do wystawcy.  
  
- Usługa WS-Farma zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> zdarzenie, gdy plik cookie został pomyślnie zapisany i użytkownik jest zalogowany.  
  
- Usługa WS-Farma zgłasza <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> zdarzenie jeden raz na sesję, ponieważ trwa zamykanie sesji dla każdego użytkownika. Nie zostanie zgłoszony, jeśli sesja zostanie zamknięta na stronie klienta (na przykład przez usunięcie pliku cookie sesji). W środowisku logowania jednokrotnego protokół IP-STS może również zażądać, aby każdy element RP mógł się wylogować. Spowoduje to również podwyższenie tego zdarzenia <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> , z `true`ustawioną na.  
  
> [!NOTE]
> Nie należy używać <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwości w żadnym zdarzeniu wywoływanym przez <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> lub <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Jest to spowodowane <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> tym, że jest ustawiony po zakończeniu procesu uwierzytelniania, podczas gdy zdarzenia są wywoływane podczas procesu uwierzytelniania.  
  
### <a name="configuration-of-federated-authentication"></a>Konfiguracja uwierzytelniania federacyjnego  
 Usługi WS-Farma i sam są konfigurowane za pomocą [ \<elementu federationConfiguration >](../configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) . Element podrzędny <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> wsFederation > konfiguruje domyślne wartości właściwości WS-Farma, takich jak właściwość i właściwość. [ \<](../configure-apps/file-schema/windows-identity-foundation/wsfederation.md) (Te wartości można zmienić w zależności od żądania, dostarczając programy obsługi dla niektórych zdarzeń WS-Farma, na przykład <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) Program obsługi plików cookie używany przez sam jest konfigurowany za pomocą [ \<](../configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) elementu podrzędnego cookieHandler >. WIF udostępnia domyślny program obsługi plików cookie zaimplementowany w <xref:System.IdentityModel.Services.ChunkedCookieHandler> klasie, która może mieć rozmiar fragmentu ustawiony [ \<](../configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) za pomocą elementu chunkedCookieHandler >. Element odwołuje się <xref:System.IdentityModel.Configuration.IdentityConfiguration>do, który zapewnia konfigurację dla innych składników WIF używanych w <xref:System.Security.Claims.ClaimsAuthenticationManager> aplikacji, <xref:System.Security.Claims.ClaimsAuthorizationManager>takich jak i. `<federationConfiguration>` Konfigurację tożsamości można odwoływać jawnie, określając nazwę `identityConfigurationName` `<federationConfiguration>` [ \<elementu IdentityConfiguration >](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) w atrybucie elementu. Jeśli konfiguracja tożsamości nie jest jawnie przywoływana, zostanie użyta domyślna konfiguracja tożsamości.  
  
 W poniższym kodzie XML przedstawiono konfigurację aplikacji jednostki uzależnionej ASP.NET (RP). Sekcje konfiguracji <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> i są dodawane do elementu.`<configSections>` <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> Elementy sam i WS-Farma są dodawane do modułów HTTP w ramach `<system.webServer>` / elementu. `<modules>` Na koniec składniki WIF są `<system.identityModel>` konfigurowane pod / `<identityConfiguration>` elementami i `<system.identityModel.services>` / .`<federationConfiguration>` Ta konfiguracja określa procedurę obsługi plików cookie fragmentarycznego, ponieważ jest to domyślna procedura obsługi plików cookie, a w `<cookieHandler>` elemencie nie określono typu procedury obsługi plików cookie.  
  
> [!WARNING]
> W poniższym przykładzie zarówno `requireHttps` atrybut `<wsFederation>` elementu, `<cookieHandler>` jak i `requireSsl` atrybut elementu są `false`. Stanowi to potencjalne zagrożenie dla bezpieczeństwa. W środowisku produkcyjnym należy ustawić `true`obie te wartości.  
  
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
- [\<federationConfiguration>](../configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
