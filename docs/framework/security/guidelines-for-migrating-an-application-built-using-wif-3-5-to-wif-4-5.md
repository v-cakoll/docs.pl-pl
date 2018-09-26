---
title: Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
ms.openlocfilehash: ec66803edc21f186fa9a8c5bcb91b5181789893d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086869"
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5
## <a name="applies-to"></a>Dotyczy:  
  
-   Microsoft® Windows® Identity Foundation (WIF) 3.5 i 4.5.  
  
## <a name="overview"></a>Omówienie  
 Windows Identity Foundation (WIF) pierwotnie został wydany w przedziale czasu .NET 3.5 z dodatkiem SP1. Ta wersja programu WIF nazywa się WIF 3.5. Została wydana jako oddzielne środowiska uruchomieniowego i zestawu SDK, co oznaczało, że każdy komputer, na którym uruchomiono program WIF obsługą musi mieć zainstalowanego środowiska uruchomieniowego programu WIF i deweloperom było konieczne pobranie i zainstalowanie zestawu SDK programu WIF można pobrać szablony programu Visual Studio i narzędzia, które są włączone programowanie aplikacji obsługujących program WIF. Począwszy od .NET 4.5, WIF zostało w pełni zintegrowane programu .NET Framework. Oddzielne środowiska uruchomieniowego nie są już potrzebne, i w programie Visual Studio 2012 można zainstalować narzędzi programu WIF, korzystając z Menedżera rozszerzeń usługi Visual Studio. Ta wersja programu WIF nazywa się program WIF 4.5.  
  
 Integracja programu WIF w środowisku .NET wymuszone kilka zmian w powierzchnię interfejsu API programu WIF. Program WIF 4.5 zawiera nowe przestrzenie nazw, pewne zmiany do elementów konfiguracji i nowe narzędzia dla programu Visual Studio. Ten temat zawiera wskazówki, które można użyć, aby ułatwić migrowanie aplikacji utworzonych przy użyciu programu WIF 3.5 to WIF 4.5. Mogą istnieć scenariusze, w których należy przeprowadzić starsze aplikacje utworzone przy użyciu programu WIF 3.5 na komputerach z systemem Windows 8 lub Windows Server 2012. Ten temat zawiera także wskazówki dotyczące sposobu włączania środowiska WIF 3.5 dla tych systemów operacyjnych.  
  
## <a name="changes-required-for-wif-45"></a>Zmiany wymagane do programu WIF 4.5  
 W tej sekcji opisano zmiany, które są wymagane do migracji aplikacji WIF 3.5 to WIF 4.5.  
  
### <a name="assembly-and-namespace-changes"></a>Zestaw i zmiany Namespace  
 W WIF 3.5 zostały wszystkie klasy programu WIF są zawarte w `Microsoft.IdentityModel` zestawu (microsoft.identitymicrosoft.identitymodel.dll). W programu WIF 4.5 klasy środowiska WIF zostały rozdzielone między następujących zestawów: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll) i `System.ServiceModel` (System.ServiceModel.dll ).  
  
 Klasy WIF 3.5 były zawarte w jednym z `Microsoft.IdentityModel` przestrzenie nazw, na przykład `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web`i tak dalej. W programu WIF 4.5 klasy środowiska WIF są teraz rozproszone między [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) przestrzeni nazw, <xref:System.Security.Claims?displayProperty=nameWithType> przestrzeni nazw, a <xref:System.ServiceModel.Security?displayProperty=nameWithType> przestrzeni nazw. Oprócz tego reorganizacji zostały porzucone niektóre klasy programu WIF 3.5 w programie WIF 4.5.  
  
 W poniższej tabeli przedstawiono niektóre ważniejsze WIF 4.5 przestrzenie nazw i typ klasy, które zawierają. Aby uzyskać bardziej szczegółowe informacje dotyczące sposobu mapowania przestrzeni nazw między WIF 3.5 i WIF 4.5 oraz o przestrzeni nazw i klas, które zostały usunięte w programie WIF 4.5, zobacz [Namespace mapowanie między WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
|Program WIF 4.5 Namespace|Opis|  
|-----------------------|-----------------|  
|<xref:System.IdentityModel?displayProperty=nameWithType>|Zawiera klasy reprezentujące transformacje pliku cookie, usługi tokenu zabezpieczeń i wyspecjalizowane czytelników słownika XML. Zawiera klasy, które z następujących przestrzeni nazw WIF 3.5: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`, i `Microsoft.IdentityModel.Threading`.|  
|<xref:System.Security.Claims?displayProperty=nameWithType>|Zawiera klasy reprezentujące oświadczeń, tożsamości opartej na oświadczeniach, oświadczenia na podstawie jednostki i inne artefakty modelu tożsamości oświadczeń. Zawiera klasy z `Microsoft.IdentityModel.Claims` przestrzeni nazw.|  
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Zawiera klasy reprezentujące tokeny zabezpieczające, programy obsługi tokenów zabezpieczających i innych artefaktów tokenu zabezpieczeń. Zawiera klasy, które z następujących przestrzeni nazw WIF 3.5: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`, i `Microsoft.IdentityModel.Tokens.Saml2`.|  
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Zawiera klasy, które są używane w scenariuszach usługi pasywnym (WS-Federation). Zawiera klasy z `Microsoft.IdentityModel.Web` przestrzeni nazw.|  
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|Klasy reprezentujące WCF umów, kanałów i hosty usług oraz innych artefaktów, które są używane w aktywnej scenariuszy (WS-Trust) jest obecnie w tej przestrzeni nazw. W programu WIF 3.5, w ramach tych zajęć były w `Microsoft.IdentityModel.Protocols.WSTrust` przestrzeni nazw.|  
  
> [!IMPORTANT]
>  Następujące `System.IdentityModel` przestrzenie nazw zawierają klasy, które implementują modelu tożsamości opartej na oświadczeniach WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Nie należy używać klas w tych trzech przestrzeni nazw, podczas tworzenia rozwiązań opartych na programu WIF.  
  
### <a name="changes-due-to-net-integration"></a>Zmian z powodu integracja .NET  
 Program WIF jest teraz zintegrowana w programie .NET Framework. Większość klas tożsamości i jednostki .NET pochodzą teraz od <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. Wyniki następujące zmiany w programie WIF 4.5:  
  
-   Klasy programu WIF, reprezentujące oświadczeń, tożsamości i jednostki teraz objęte <xref:System.Security.Claims?displayProperty=nameWithType> przestrzeni nazw.  
  
    > [!IMPORTANT]
    >  <xref:System.IdentityModel.Claims?displayProperty=nameWithType> Przestrzeń nazw zawiera klasy reprezentujące artefaktów w modelu tożsamości opartej na oświadczeniach WCF. Wiele z tych klas mają nazwy, które są takie same jak klasy programu WIF; na przykład `Claims`. Nie należy używać w ramach tych zajęć, podczas tworzenia rozwiązań opartych na programu WIF.  
  
-   Klasy tożsamości i jednostki .NET pochodzą teraz bezpośrednio z <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, które reprezentują tożsamości opartej na oświadczeniach i nazwy główne. Z tego powodu WIF 3.5 interfejsy `IClaimsIdentity` i `IClaimsPrincipal` nie są już potrzebne i nie są dostępne w programie WIF 4.5.  
  
-   Because.NET tożsamości i jednostki klasy takie jak <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> i <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> pochodzą teraz od <xref:System.Security.Claims.ClaimsIdentity> i <xref:System.Security.Claims.ClaimsPrincipal>, mają wbudowany funkcjonalność oświadczeń. Dla tego powodu, specyficzne dla oświadczeń, tożsamości i jednostki klasy, takie jak `WindowsClaimsIdentity` i `WindowsClaimsPrincipal` , które były obecne w WIF 3.5 nie są już potrzebne i nie istnieją w WIF 4.5.  
  
### <a name="other-changes-to-wif-functionality"></a>Inne zmiany w funkcjonalności programu WIF  
 Oprócz zmian przestrzeni nazw i zmian z powodu integracji z platformą .NET zachodzą następujące zmiany ogólne funkcjonalności programu WIF w WIF 4.5.  
  
-   `Microsoft.IdentityModel.ExceptionMapper` Klasy, która jest podana funkcji, która umożliwiała Mapowanie wyjątków do określonych błędach SOAP, zostanie usunięty.  
  
-   Wyjątek znacznie ją ograniczono.  
  
-   Wiele klas, które zdefiniowane lub protokołu usługi WS-* określonych stałe zostały usunięte; na przykład `Microsoft.IdentityModel.WSAddressing10Constants` klasy, która zdefiniowane stałe związane z WS-Addressing 1.0.  
  
-   Oświadczenia do usługi tokenu Windows (c2wts) i jego skojarzonych klas w `Microsoft.IdentityModel.WindowsTokenService` przestrzeni nazw są usuwane.  
  
### <a name="wif-configuration-changes"></a>Zmiany konfiguracji programu WIF  
 Wiele zmian w pliku konfiguracyjnym zostać spowodowane aktualizacji przestrzeni nazw w programie WIF 4.5. Na przykład rozważmy następujący wpis WIF 3.5 w `<httpModules>` sekcji, aby dodać Menedżera uwierzytelniania protokołu WS-Federation do aplikacji:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />  
```  
  
 Ten wpis został zaktualizowany w WIF 4.5, aby uwzględnić nowe przestrzenie nazw i wersję zestawu:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>  
```  
  
 Poniższa lista wylicza poważne zmiany w pliku konfiguracji dla programu WIF 4.5.  
  
-   `<microsoft.identityModel>` Sekcja jest teraz [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) sekcji.  
  
-   `<service>` Element jest teraz [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.  
  
-   Nowa sekcja [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), została dodana do określania ustawień, które kontrolują zachowanie w pasywnym scenariuszach (WS-Federation).  
  
-   [ \<FederationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu i jego elementy podrzędne zostały przeniesione z `<service>` elementu w WIF 3.5 do nowego `<system.identityModel.services>` elementu.  
  
-   Kilka elementów, które można określić na poziomie usługi bezpośrednio w obszarze `<service>` element WIF 3.5 ograniczeniom określone w obszarze [ \<securityTokenHandlerConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element. (Nadal może być określone w obszarze [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element WIF 4.5 zgodności z poprzednimi wersjami.)  
  
 Aby uzyskać pełną listę elementów konfiguracji programu WIF 4.5, zobacz [schemat konfiguracji programu WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md).  
  
### <a name="visual-studio-tooling-changes"></a>Zmiany narzędzi programu Visual Studio  
 Zestawu SDK programu WIF 3.5 oferowane narzędziem autonomicznej Federacji FedUtil.exe (FedUtil), można użyć w celu oddelegowania procesów zarządzania tożsamościami w aplikacjach z obsługą programu WIF do usługi tokenu zabezpieczającego (STS). To narzędzie dodane ustawienia programu WIF do pliku konfiguracji aplikacji, aby umożliwić aplikacji w celu uzyskania tokenów zabezpieczających, przez co najmniej jeden usługi STS i został udostępnione w programie Visual Studio za pośrednictwem **Dodaj odwołanie do usługi STS** przycisku. FedUtil nie jest składnikiem programu WIF 4.5. Zamiast tego program WIF 4.5 obsługuje nowe rozszerzenie programu Visual Studio o nazwie narzędzie tożsamości i dostępu dla programu Visual Studio 2012, który służy do modyfikowania pliku konfiguracji aplikacji przy użyciu ustawień programu WIF, wymagane w celu oddelegowania procesów zarządzania tożsamości do usługi STS. Narzędzie tożsamość i dostęp implementuje również usługi tokenu Zabezpieczającego usług o nazwie lokalnej usługi STS, którego można użyć, aby testować swoje aplikacje z włączoną obsługą programu WIF. W wielu przypadkach ta funkcja zwalnia z obowiązku Tworzenie niestandardowych usług STS, które były często konieczne w WIF 3.5 to testowanie rozwiązań w fazie projektowania. Z tego powodu w szablonach usługi STS nie są już obsługiwane w programie Visual Studio 2012; jednak klasy obsługujące tworzenie usług STS, które są wciąż dostępne w WIF 4.5.  
  
 Możesz zainstalować narzędzie tożsamość i dostęp z rozszerzenia i aktualizacje Manager w programie Visual Studio lub można go pobrać z następującej strony w galerii kodów: [narzędzie tożsamości i dostępu dla programu Visual Studio 2012 w galerii kodów](https://go.microsoft.com/fwlink/?LinkID=245849). Zmiany narzędzi programu Visual Studio są podsumowywane na poniższej liście:  
  
-   Funkcje Dodaj odwołanie do usługi STS jest usuwany. Zastąpienie jest narzędzie tożsamość i dostęp.  
  
-   Szablony programu Visual Studio usługi STS, są usuwane. Możesz użyć lokalnej usługi STS, która jest dostępna za pośrednictwem narzędzie tożsamość i dostęp do przetestowania rozwiązania tożsamości, które tworzysz przy użyciu programu WIF. Konfiguracja lokalnej usługi STS można zmodyfikować w taki sposób, aby dostosować oświadczenia, które służy ona.  
  
-   Autonomiczne narzędzia federacyjnego (FedUtil) nie jest dostępna w programie WIF 4.5. Narzędzie tożsamości i dostępu umożliwia modyfikowanie plików konfiguracji w celu oddelegowania procesów zarządzania tożsamości do usługi STS.  
  
 Aby uzyskać więcej informacji na temat narzędzie tożsamości i dostępu, zobacz [narzędzie tożsamości i dostępu dla programu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)  
  
<a name="BKMK_ToolingChanges"></a>   
### <a name="passive-ws-federation-scenarios"></a>Scenariusze pasywnym (WS-Federation):  
  
-   Klasy, które obsługują scenariusze pasywnym zostały przeniesione do ikony <xref:System.IdentityModel.Services?displayProperty=nameWithType> przestrzeni nazw. W programu WIF 3.5 w ramach tych zajęć były w `Microsoft.IdentityModel.Web` przestrzeni nazw.  
  
-   Klasy w `Microsoft.IdentityModel.Web.Configuration` przestrzeni nazw zostały przeniesione do ikony <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Te klasy reprezentują określonych obiektów do konfiguracji w scenariuszach pasywnym.  
  
-   `FederatedPasssiveSignInControl` Nie jest już obsługiwany; wszystkie klasy w `Microsoft.IdentityModel.Web.Controls` przestrzeni nazw zostały usunięte z programu WIF 4.5.  
  
-   Moduł uwierzytelniania protokołu WS-Federation (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) funkcji wylogowania różni się od programu WIF 3.5. Aby uzyskać więcej szczegółów na temat sposobu wyrejestrowywania działa w programie WIF 4.5, zobacz <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> temat poświęcony klasie.  
  
### <a name="active-wcfws-trust-scenarios"></a>Aktywne (WCF protokołu WS-Trust) scenariusze:  
  
-   `Microsoft.IdentityModel.Protocols.WSTrust` Przestrzeni nazw został podzielony przede wszystkim na dwóch przestrzeniach nazw programu WIF 4.5. Klas reprezentujących artefakty, które są specyficzne dla protokołu WS-Trust są teraz w <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. Obejmuje to klasy takie jak <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Klasy reprezentujące kontraktów usług, kanały, hosty usług i innych artefaktów, które są zaangażowane WE w aplikacji WCF za pomocą protokołu WS-Trust zostały przeniesione do ikony <xref:System.ServiceModel.Security?displayProperty=nameWithType>, na przykład <xref:System.ServiceModel.Security.IWSTrust13AsyncContract> interfejsu.  
  
-   Konfigurowanie aplikacji WCF korzystanie ze środowiska WIF znacznie uproszczono. Wcześniej `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` musiał zostać dodany jako rozszerzenia zachowania i następnie użyto tej funkcji do wedge programu WIF do zachowanie usługi, określając `<federatedServiceHostConfiguration>` elementu. Program WIF 4.5 zostały bardziej ściśle zintegrowane z programem WCF. Trwa włączanie programu WIF w usłudze WCF poprzez określenie `useIdentityConfiguration` atrybutu na `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` elementu, tak jak następujący kod XML:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
-   W programu WIF 4.5 usługi na hoście usługi należy określić certyfikat używany przez aktywne usługi (WCF). W konfiguracji, można to zrobić za pomocą `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` / `<serviceCertificate>` elementu, jak pokazano w powyższym przykładzie. W programu WIF 3.5 certyfikatu usługi może być określony za pomocą `<serviceCertificate>` element podrzędny elementu WIF `<service>` elementu. Ta funkcja nie istnieje w WIF 4.5; Określ `<serviceCertificate>` pod `<serviceCredentials>` elementu zamiast tego.  
  
-   Klasy umożliwiają wedge WIF 3.5 do usług WCF nie jest już istnieje. Obejmuje to następujące klasy w `Microsoft.IdentityModel.Tokens` przestrzeni nazw: `FederatedSecurityTokenManager`, `FederatedServiceCredentials`, i `IdentityModelServiceAuthorizationManager`, jak również `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` klasy.  
  
## <a name="enabling-wif-35-in-windows-8"></a>Włączania środowiska WIF 3.5 w systemie Windows 8  
 Ponieważ program WIF 4.5 jest częścią platformy .NET 4.5, zostaje automatycznie włączony na komputerach z systemem Windows 8 i Windows Server 2012 i aplikacje, które zostały utworzone przy użyciu programu WIF 4.5 zostanie domyślnie uruchamiane w systemie Windows 8 lub Windows Server 2012. Jednak może być konieczne uruchomienie aplikacji, które zostały utworzone przy użyciu programu WIF 3.5 na komputerze, na którym działa system Windows 8 lub Windows Server 2012. W takim przypadku należy włączyć WIF 3.5 na komputerze docelowym. Na komputerze z systemem Windows 8 możesz to zrobić za pomocą narzędzia Deployment Image Servicing i zarządzanie (DISM). Na komputerze z systemem Windows Server 2012, można użyć narzędzia DISM, lub można użyć programu Windows PowerShell `Add-WindowsFeature` polecenia cmdlet. W obu przypadkach może być wywoływany odpowiednich poleceń w wierszu polecenia lub od wewnątrz środowiska Windows PowerShell.  
  
 Poniższe polecenia pokazują, jak za pomocą narzędzia DISM z wiersza polecenia lub w środowisku Windows PowerShell. Domyślnie moduł DISM PowerShell znajduje się w systemie Windows 8 i Windows Server 2012 i nie musi zostać zaimportowany. Aby uzyskać więcej informacji o używaniu narzędzia DISM przy użyciu programu Windows PowerShell, zobacz [sposób użycia narzędzia DISM, w programie Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=254419).  
  
 Aby włączyć program WIF 3.5 przy użyciu narzędzia DISM:  
  
```  
dism /online /enable-feature:windows-identity-foundation  
```  
  
 Aby wyłączyć WIF 3.5 przy użyciu narzędzia DISM:  
  
```  
dism /online /disable-feature:windows-identity-foundation  
```  
  
 Aby sprawdzić, jakie funkcje są włączone lub wyłączone przy użyciu narzędzia DISM:  
  
```  
dism /online /get-features  
```  
  
 Na komputerach z systemem Windows Server 2012 można też włączyć WIF 3.5 przy użyciu programu Windows PowerShell `Add-WindowsFeature` polecenia cmdlet. Aby to zrobić z wiersza polecenia można wprowadzić następujące polecenie:  
  
```  
powershell "add-windowsfeature windows-identity-foundation"  
```  
  
 Z wewnątrz środowiska Windows PowerShell, można wprowadzić polecenie bezpośrednio:  
  
```  
add-windowsfeature windows-identity-foundation  
```  
  
> [!NOTE]
>  Ponieważ wiele klas programu WIF 3.5 i WIF 4.5 mają takie same nazwy, podczas korzystania z programu WIF 3.5 i WIF 4.5 ze sobą, należy koniecznie Użyj nazwy klasy w pełni kwalifikowana lub użyj aliasy obszaru nazw do rozróżniania między klasami w WIF 3.5 i WIF 4.5.  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat konfiguracji programu WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)  
 [Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Co nowego w programie Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)  
 [Narzędzie tożsamości i dostępu dla programu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)
