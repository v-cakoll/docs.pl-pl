---
title: Wskazówki dotyczące migrowania aplikacji utworzony za pomocą programu WIF 3.5 do wersji WIF 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
caps.latest.revision: ''
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 87443a83b80440a30e942b30bd98cce09816f25f
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>Wskazówki dotyczące migrowania aplikacji utworzony za pomocą programu WIF 3.5 do wersji WIF 4.5
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF) 3.5 and 4.5.  
  
## <a name="overview"></a>Omówienie  
 Windows Identity Foundation (WIF) pierwotnie został wydany w przedziale czasu .NET 3.5 z dodatkiem SP1. Ta wersja programu WIF nazywa się WIF 3.5. Został wydany jako oddzielne środowiska uruchomieniowego i zestawu SDK, co oznaczało, że każdy komputer, na którym uruchomiono aplikację z obsługą WIF musiała mieć zainstalowane środowisko uruchomieniowe WIF i deweloperzy należało pobrać i zainstalować WIF zestawu SDK można pobrać szablony programu Visual Studio i narzędzi, które włączone programowanie aplikacji obsługujących WIF. Począwszy od platformy .NET 4.5, WIF zostało pełni zintegrowane programu .NET Framework. Oddzielne środowiska uruchomieniowego nie są już potrzebne, i narzędzi WIF można zainstalować w programie Visual Studio 2012 za pomocą Menedżera rozszerzeń programu Visual Studio. Ta wersja programu WIF nazywa się WIF 4.5.  
  
 Integracja programu WIF programu .NET wymuszone kilka zmian na powierzchni interfejsu API WIF. WIF 4.5 obejmuje nowych przestrzeni nazw, niektóre zmiany do elementów konfiguracji i nowych narzędzi dla programu Visual Studio. Ten temat zawiera wskazówki, które umożliwia ułatwiające migrację aplikacji utworzony za pomocą WIF 3.5 WIF 4.5. Może istnieć scenariusze, w których należy uruchomić starszych aplikacji utworzony za pomocą WIF 3.5 na komputerach z systemem Windows 8 lub Windows Server 2012. Ten temat zawiera również wskazówki dotyczące sposobu włączania WIF 3.5 dla tych systemów operacyjnych.  
  
## <a name="changes-required-for-wif-45"></a>Zmiany wymagane dla WIF 4.5  
 W tej sekcji opisano zmiany, które są wymagane do migracji aplikacji WIF 3.5, do wersji WIF 4.5.  
  
### <a name="assembly-and-namespace-changes"></a>Zestaw i Namespace zmiany  
 W WIF 3.5 wszystkie klasy WIF zostały zawarte w `Microsoft.IdentityModel` zestawu (microsoft.identitymicrosoft.identitymodel.dll). W wersji WIF 4.5 klasy WIF zostały rozdzielone między następujące zestawy: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll) i `System.ServiceModel` (System.ServiceModel.dll ).  
  
 Klasy WIF 3.5 zostały zawarte w jednym z `Microsoft.IdentityModel` przestrzeni nazw, na przykład `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web`i tak dalej. W wersji WIF 4.5 klasy WIF teraz są rozkładane między [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) przestrzeni nazw, <xref:System.Security.Claims?displayProperty=nameWithType> przestrzeni nazw i <xref:System.ServiceModel.Security?displayProperty=nameWithType> przestrzeni nazw. Oprócz tego reorganizacji niektóre klasy WIF 3.5 zostały usunięte w wersji WIF 4.5.  
  
 W poniższej tabeli przedstawiono niektóre ważniejsze przestrzenie nazw WIF 4.5 i rodzaj klasy, które zawierają. Aby uzyskać bardziej szczegółowe informacje dotyczące sposobu mapowania przestrzeni nazw między WIF 3.5 i WIF 4.5 i obszary nazw i klasy, które zostały usunięte w wersji WIF 4.5 informacje, zobacz [Namespace mapowanie między WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
|WIF 4.5 Namespace|Opis|  
|-----------------------|-----------------|  
|<xref:System.IdentityModel?displayProperty=nameWithType>|Zawiera klasy reprezentujące transformacje plików cookie, usługi tokenu zabezpieczeń i specjalnych czytników słownika XML. Zawiera klasy z następujących przestrzeni nazw WIF 3.5: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`, i `Microsoft.IdentityModel.Threading`.|  
|<xref:System.Security.Claims?displayProperty=nameWithType>|Zawiera klasy reprezentujące oświadczeń, tożsamości opartego na oświadczeniach podmiotów oświadczeń i pozostałych artefaktów modelu tożsamości oświadczeń. Zawiera klasy z `Microsoft.IdentityModel.Claims` przestrzeni nazw.|  
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Zawiera klasy reprezentujące tokeny zabezpieczające, obsługi tokenu zabezpieczeń i innych artefaktów tokenu zabezpieczeń. Zawiera klasy z następujących przestrzeni nazw WIF 3.5: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`, i `Microsoft.IdentityModel.Tokens.Saml2`.|  
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Zawiera klasy, które są używane w scenariuszach, pasywnym (WS-Federation). Zawiera klasy z `Microsoft.IdentityModel.Web` przestrzeni nazw.|  
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|Klasy reprezentujące WCF kontrakty, kanały, hosty usługi i pozostałych artefaktów, które są używane w scenariuszach (WS-Trust) active są dostępne w tej przestrzeni nazw. W WIF 3.5 tych klas były w `Microsoft.IdentityModel.Protocols.WSTrust` przestrzeni nazw.|  
  
> [!IMPORTANT]
>  Następujące `System.IdentityModel` przestrzenie nazw zawiera klasy, które implementują modelu tożsamości opartego na oświadczeniach WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Nie należy używać klas w tych trzech obszarach nazw podczas tworzenia rozwiązań opartych na WIF.  
  
### <a name="changes-due-to-net-integration"></a>Zmian z powodu integracja .NET  
 WIF jest teraz zintegrowany programu .NET Framework. Większość klas .NET tożsamości i nazwę główną teraz pochodzi od <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. Wyniki w wersji WIF 4.5 następujące zmiany:  
  
-   Klasy WIF, które reprezentują oświadczeń, tożsamości i podmiotów teraz istnieje w <xref:System.Security.Claims?displayProperty=nameWithType> przestrzeni nazw.  
  
    > [!IMPORTANT]
    >  <xref:System.IdentityModel.Claims?displayProperty=nameWithType> Przestrzeń nazw zawiera klasy reprezentujące artefaktów w modelu tożsamości opartego na oświadczeniach WCF. Wiele z tych klas mają nazwy, które są takie same jak klasy WIF; na przykład `Claims`. Nie należy używać tych klas, podczas tworzenia rozwiązań opartych na WIF.  
  
-   Klasy .NET tożsamości i nazwę główną teraz pochodzi bezpośrednio z <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, które reprezentują tożsamości opartego na oświadczeniach i podmiotów zabezpieczeń. Z tego powodu interfejsy WIF 3.5 `IClaimsIdentity` i `IClaimsPrincipal` nie są już potrzebne i nie są dostępne w wersji WIF 4.5.  
  
-   Because.NET tożsamości i nazwę główną klas takich jak <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> i <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> teraz pochodzi od <xref:System.Security.Claims.ClaimsIdentity> i <xref:System.Security.Claims.ClaimsPrincipal>, mają wbudowane funkcje oświadczeń. Dla tego przyczyny, oświadczenia dotyczące tożsamości i głównych klas takich jak `WindowsClaimsIdentity` i `WindowsClaimsPrincipal` , które były obecne w WIF 3.5 nie są już potrzebne i nie istnieją w wersji WIF 4.5.  
  
### <a name="other-changes-to-wif-functionality"></a>Inne zmiany w funkcjonalności WIF  
 Oprócz zmiany przestrzeni nazw i zmian z powodu Integracja z platformą .NET występują następujące ogólne zmiany WIF funkcji w wersji WIF 4.5.  
  
-   `Microsoft.IdentityModel.ExceptionMapper` Klasy, która realizować funkcje, która umożliwiała Mapowanie wyjątków do określonych błędach SOAP, zostaną usunięte.  
  
-   Wyjątek znacznie ją ograniczono.  
  
-   Wiele klas, które zdefiniowano lub protokołu WS-* określonych stałe zostały usunięte; na przykład `Microsoft.IdentityModel.WSAddressing10Constants` klasy, która jest zdefiniowana stałe związane z protokołu WS-Addressing 1.0.  
  
-   Oświadczenia do usługi tokenu systemu Windows (c2wts) i jego skojarzonych klas w `Microsoft.IdentityModel.WindowsTokenService` przestrzeni nazw są usuwane.  
  
### <a name="wif-configuration-changes"></a>Zmiany konfiguracji WIF  
 Wiele zmian w pliku konfiguracyjnym zostać spowodowane aktualizacji przestrzeni nazw w wersji WIF 4.5. Rozważmy na przykład następujący wpis WIF 3.5 w `<httpModules>` sekcji, aby dodać WS-Federation Menedżer uwierzytelniania do aplikacji:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />  
```  
  
 Ten wpis został zaktualizowany w wersji WIF 4.5 w celu uwzględnienia nowych przestrzeni nazw i wersja zestawu:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>  
```  
  
 Poniższa lista wylicza najważniejszych zmian w pliku konfiguracji dla wersji WIF 4.5.  
  
-   `<microsoft.identityModel>` Sekcja jest teraz [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) sekcji.  
  
-   `<service>` Element jest teraz [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.  
  
-   Nowa sekcja [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), został dodany do określenia ustawień, które kontrolują zachowanie w scenariuszach, pasywnym (WS-Federation).  
  
-   [ \<FederationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu i jego elementy podrzędne zostały przeniesione z `<service>` element WIF 3.5 do nowego `<system.identityModel.services>` elementu.  
  
-   Wiele elementów, które można określić na poziomie usługi bezpośrednio w obszarze `<service>` element WIF 3.5 były ograniczone do określany w obszarze [ \<securityTokenHandlerConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element. (Nadal mogą być określone w obszarze [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu w wersji WIF 4.5 dla zgodności z poprzednimi wersjami.)  
  
 Aby uzyskać pełną listę elementów konfiguracji programu WIF 4.5, zobacz [schemat konfiguracji WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md).  
  
### <a name="visual-studio-tooling-changes"></a>Zmiany narzędzi Visual Studio  
 Zestaw SDK programu WIF 3.5 oferowane narzędzia federacyjnego autonomicznej, FedUtil.exe (FedUtil), można użyć do zewnętrznej obsługi zarządzania tożsamościami w aplikacjach z obsługą WIF usługę tokenu zabezpieczającego (STS). To narzędzie dodane ustawienia WIF do pliku konfiguracji aplikacji, aby umożliwić aplikacji w celu uzyskania tokeny zabezpieczające z co najmniej jeden STSs i został udostępniane w programie Visual Studio za pomocą **Dodaj odwołanie do usługi STS** przycisku. FedUtil nie jest składnikiem wersji WIF 4.5. Zamiast tego WIF 4.5 obsługuje nowe rozszerzenie programu Visual Studio o nazwie tożsamości i dostępu do narzędzi dla programu Visual Studio 2012, który służy do modyfikowania pliku konfiguracji aplikacji przy użyciu ustawień WIF, wymaganych do zewnętrznej obsługi zarządzania tożsamościami do usługi tokenu Zabezpieczającego. Tożsamość i narzędzie dostępu implementuje również tokenu Zabezpieczającego o nazwie lokalnej usługi STS używanej do testowania aplikacji z obsługą WIF. W wielu przypadkach ta funkcja zwalnia z obowiązku STSs niestandardowych, które były często niezbędne w WIF 3.5 w celu przetestowania rozwiązania opracowywane kompilacji. Z tego powodu szablony usługi STS nie są już obsługiwane w programie Visual Studio 2012; jednak klas, które obsługują rozwoju STSs są nadal dostępne w wersji WIF 4.5.  
  
 Możesz zainstalować narzędzie dostępu i tożsamości z rozszerzenia i aktualizacje Manager w programie Visual Studio lub można go pobrać z następującej strony w galerii kodu: [tożsamości i dostępu do narzędzi dla programu Visual Studio 2012 w galerii kodu](http://go.microsoft.com/fwlink/?LinkID=245849). Zmiany narzędzi Visual Studio przedstawiono na poniższej liście:  
  
-   Dodaj odwołanie do usługi STS funkcje zostaną usunięte. Zastąpienie jest narzędzie dostępu i tożsamości.  
  
-   Szablony Visual Studio STS zostaną usunięte. Możesz użyć lokalnej usługi STS dostępnej za pośrednictwem tożsamości i dostęp do narzędzia do testowania tożsamościach, tworzonych z WIF. Konfiguracja lokalnej usługi STS można zmodyfikować w taki sposób, aby dostosować oświadczenia, które służy ona.  
  
-   Autonomicznego narzędzia federacyjnego (FedUtil) nie jest dostępna w wersji WIF 4.5. Tożsamość i narzędzie dostępu służy do modyfikowania konfiguracji plików do zewnętrznej obsługi zarządzania tożsamościami do usługi tokenu Zabezpieczającego.  
  
 Aby uzyskać więcej informacji o tożsamości i dostępu narzędzie, zobacz [tożsamości i dostępu do narzędzi dla programu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)  
  
<a name="BKMK_ToolingChanges"></a>   
### <a name="passive-ws-federation-scenarios"></a>Scenariusze pasywny (WS-Federation):  
  
-   Klasy obsługujące scenariusze pasywnym zostały przeniesione do <xref:System.IdentityModel.Services?displayProperty=nameWithType> przestrzeni nazw. W WIF 3.5 tych klas były w `Microsoft.IdentityModel.Web` przestrzeni nazw.  
  
-   Klasy w `Microsoft.IdentityModel.Web.Configuration` przestrzeni nazw zostały przeniesione do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Te klasy reprezentują określonych obiektów do konfiguracji w scenariuszach pasywnych.  
  
-   `FederatedPasssiveSignInControl` Nie jest już obsługiwany; wszystkie klasy w `Microsoft.IdentityModel.Web.Controls` przestrzeni nazw zostały usunięte z wersji WIF 4.5.  
  
-   Moduł uwierzytelniania protokołu WS-Federation (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) funkcji wylogowania różni się od WIF 3.5. Aby uzyskać więcej informacji na temat sposobu wyrejestrowywania działa w wersji WIF 4.5, zobacz <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> klasy tematu.  
  
### <a name="active-wcfws-trust-scenarios"></a>Scenariuszy aktywnej (WCF WS-Trust):  
  
-   `Microsoft.IdentityModel.Protocols.WSTrust` Przestrzeń nazw została podzielona głównie do dwóch nazw w wersji WIF 4.5. Klasy reprezentujące artefaktów, które są specyficzne dla protokołu WS-Trust znajdują się teraz na <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. Dotyczy to również klas takich jak <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Klasy reprezentujące kontraktów usług, kanały, hosty usługi i pozostałych artefaktów związanych z aplikacji WCF za pomocą protokołu WS-Trust zostały przeniesione do <xref:System.ServiceModel.Security?displayProperty=nameWithType>, na przykład <xref:System.ServiceModel.Security.IWSTrust13AsyncContract> interfejsu.  
  
-   Konfigurowanie aplikacji WCF do użycia WIF znacznie uproszczono. Wcześniej `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` musiała zostać dodana jako rozszerzenia zachowania i następnie użyto tej funkcji do Zasuwa klinowa WIF do zachowania usługi, określając `<federatedServiceHostConfiguration>` elementu. WIF 4.5 został bardziej ściśle zintegrowany z programem WCF. Po włączeniu WIF usługi WCF, określając `useIdentityConfiguration` atrybutu `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` element jak następujący kod XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
-   W wersji WIF 4.5 usługi na hoście usługi należy określić certyfikat używany przez usługę active (WCF). W konfiguracji, można to zrobić za pomocą `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` / `<serviceCertificate>` element, jak pokazano w poprzednim przykładzie. W WIF 3.5 certyfikatu usługi może być określony za pomocą `<serviceCertificate>` elementem podrzędnym WIF `<service>` elementu. Ta funkcja nie istnieje w wersji WIF 4.5; Określ `<serviceCertificate>` elementu w obszarze `<serviceCredentials>` elementu zamiast tego.  
  
-   Klasy używane do Zasuwa klinowa WIF 3.5 do usługi WCF nie jest już istnieje. Obejmuje to następujące klasy w `Microsoft.IdentityModel.Tokens` przestrzeni nazw: `FederatedSecurityTokenManager`, `FederatedServiceCredentials`, i `IdentityModelServiceAuthorizationManager`, a także `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` klasy.  
  
## <a name="enabling-wif-35-in-windows-8"></a>Włączanie programu WIF 3.5 w systemie Windows 8  
 Ponieważ WIF 4.5 jest częścią .NET 4.5, jest automatycznie włączone na komputerach z systemem Windows 8 i Windows Server 2012 i domyślnie aplikacji utworzonych przy użyciu wersji WIF 4.5 jest uruchamiana w systemie Windows 8 lub Windows Server 2012. Jednak należy do uruchamiania aplikacji, które zostały utworzone przy użyciu WIF 3.5 na komputerze z systemem Windows 8 lub Windows Server 2012. W takim przypadku należy włączyć WIF 3.5 na komputerze docelowym. Na komputerze z systemem Windows 8 możesz to zrobić za pomocą narzędzia Deployment Image Servicing and Management (DISM). Na komputerze z systemem Windows Server 2012, można użyć narzędzia DISM albo użyć środowiska Windows PowerShell `Add-WindowsFeature` polecenia cmdlet. W obu przypadkach można wywołać odpowiednich poleceń w wierszu polecenia lub z wewnątrz środowiska Windows PowerShell.  
  
 Poniższe polecenia pokazują, jak za pomocą narzędzia DISM z wiersza polecenia lub w środowisku Windows PowerShell. Domyślnie moduł PowerShell narzędzie DISM jest dołączony do systemu Windows 8 i Windows Server 2012 i nie należy do zaimportowania. Aby uzyskać więcej informacji na temat używania narzędzia DISM przy użyciu programu Windows PowerShell, zobacz [sposobu użycia narzędzia DISM, w programie Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=254419).  
  
 Aby włączyć WIF 3.5 przy użyciu narzędzia DISM:  
  
```  
dism /online /enable-feature:windows-identity-foundation  
```  
  
 Aby wyłączyć WIF 3.5 przy użyciu narzędzia DISM:  
  
```  
dism /online /disable-feature:windows-identity-foundation  
```  
  
 Aby sprawdzić, które funkcje są włączone lub wyłączone za pomocą narzędzia DISM:  
  
```  
dism /online /get-features  
```  
  
 Na komputerach z systemem Windows Server 2012, można też włączyć WIF 3.5 przy użyciu programu Windows PowerShell `Add-WindowsFeature` polecenia cmdlet. W tym celu w wierszu polecenia można wprowadź następujące polecenie:  
  
```  
powershell "add-windowsfeature windows-identity-foundation"  
```  
  
 Z wewnątrz środowiska Windows PowerShell, można wprowadzić polecenie bezpośrednio:  
  
```  
add-windowsfeature windows-identity-foundation  
```  
  
> [!NOTE]
>  Ponieważ wiele klas WIF 3.5 i wersji WIF 4.5 udział tych samych nazw, gdy jest używany zarówno WIF 3.5, jak i wersji WIF 4.5 razem należy Użyj pełnych nazw klasy albo użyj przestrzeni nazw aliasów do rozróżniania między klasami w WIF 3.5 i wersji WIF 4.5.  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat konfiguracji programu WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)  
 [Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Co nowego w programie Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)  
 [Narzędzie tożsamości i dostępu dla programu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)
