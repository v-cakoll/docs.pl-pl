---
title: Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
ms.openlocfilehash: 3ba99a061d060ebe7740fe61846c3684b5c3085d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045485"
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5

## <a name="applies-to"></a>Dotyczy:

- Microsoft® Windows® Identity Foundation (WIF) 3,5 i 4,5.

## <a name="overview"></a>Omówienie

Program Windows Identity Foundation (WIF) został pierwotnie wydzierżawiony w przedziale czasu .NET 3,5 z dodatkiem SP1. Ta wersja WIF jest określana jako WIF 3,5. Został on wydzielony jako osobny środowisko uruchomieniowe i zestaw SDK, co oznacza, że na każdym komputerze, na którym uruchomiono aplikację z obsługą WIF, należało zainstalować środowisko uruchomieniowe WIF i deweloperzy musieli pobrać i zainstalować zestaw SDK WIF w celu pobrania szablonów i narzędzi programu Visual Studio, które są włączone opracowywanie aplikacji z obsługą WIF. Począwszy od programu .NET 4,5, WIF został w pełni zintegrowany z .NET Framework. Oddzielne środowisko uruchomieniowe nie jest już potrzebne, a narzędzia WIF można zainstalować w programie Visual Studio 2012 przy użyciu Menedżera rozszerzeń programu Visual Studio. Ta wersja programu WIF jest określana jako WIF 4,5.

Integracja WIF z platformą .NET wymagała kilku zmian w powierzchni interfejsu API WIF. WIF 4,5 obejmuje nowe przestrzenie nazw, pewne zmiany elementów konfiguracji oraz nowe narzędzia dla programu Visual Studio. Ten temat zawiera wskazówki, za pomocą których można migrować Aplikacje skompilowane przy użyciu WIF 3,5 do WIF 4,5. Mogą istnieć scenariusze, w których należy uruchamiać starsze aplikacje skompilowane przy użyciu WIF 3,5 na komputerach z systemem Windows 8 lub Windows Server 2012. Ten temat zawiera również wskazówki dotyczące włączania WIF 3,5 dla tych systemów operacyjnych.

## <a name="changes-required-for-wif-45"></a>Zmiany wymagane przez WIF 4,5

W tej sekcji opisano zmiany, które są wymagane do migrowania aplikacji WIF 3,5 do WIF 4,5.

### <a name="assembly-and-namespace-changes"></a>Zmiany zestawu i przestrzeni nazw

W WIF 3,5 wszystkie klasy WIF zostały zawarte w `Microsoft.IdentityModel` zestawie (Microsoft. identitymicrosoft. IdentityModel. dll). W WIF 4,5 klasy WIF zostały podzielone `mscorlib` na następujące zestawy: (mscorlib. dll), `System.IdentityModel` (System. IdentityModel. dll), `System.IdentityModel.Services` (System. IdentityModel. Services. dll) i `System.ServiceModel` (System. ServiceModel. dll ).

Klasy WIF 3,5 zostały zawarte w jednej `Microsoft.IdentityModel` z przestrzeni nazw, na `Microsoft.IdentityModel`przykład `Microsoft.IdentityModel.Tokens` `Microsoft.IdentityModel.Web`,,, i tak dalej. W WIF 4,5 klasy WIF są teraz rozmieszczane w przestrzeniach nazw [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) , <xref:System.Security.Claims?displayProperty=nameWithType> <xref:System.ServiceModel.Security?displayProperty=nameWithType> przestrzeń nazw i przestrzeń nazw. Poza tą reorganizacją niektóre klasy WIF 3,5 zostały porzucone w WIF 4,5.

W poniższej tabeli przedstawiono niektóre z ważniejszych przestrzeni nazw WIF 4,5 i rodzaj klas, które zawierają. Aby uzyskać bardziej szczegółowe informacje na temat sposobu mapowania przestrzeni nazw między WIF 3,5 i WIF 4,5 oraz o przestrzeniach nazw i klasach, które zostały porzucone w WIF 4,5, zobacz [mapowanie przestrzeni nazw między WIF 3,5 i WIF 4,5](namespace-mapping-between-wif-3-5-and-wif-4-5.md).

|WIF 4,5 — przestrzeń nazw|Opis|
|-----------------------|-----------------|
|<xref:System.IdentityModel?displayProperty=nameWithType>|Zawiera klasy reprezentujące przekształcenia plików cookie, usługi tokenów zabezpieczających i wyspecjalizowane czytniki słownika XML. Zawiera klasy z następujących przestrzeni nazw WIF 3,5: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`, i `Microsoft.IdentityModel.Threading`.|
|<xref:System.Security.Claims?displayProperty=nameWithType>|Zawiera klasy reprezentujące oświadczenia, tożsamości oparte na oświadczeniach, podmioty zabezpieczeń oparte na oświadczeniach oraz inne artefakty modelu tożsamości oparte na oświadczeniach. Zawiera klasy z `Microsoft.IdentityModel.Claims` przestrzeni nazw.|
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Zawiera klasy reprezentujące tokeny zabezpieczające, programy obsługi tokenów zabezpieczających i inne artefakty tokenów zabezpieczających. Zawiera klasy z następujących przestrzeni nazw WIF 3,5: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`, i `Microsoft.IdentityModel.Tokens.Saml2`.|
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Zawiera klasy, które są używane w scenariuszach pasywnych (WS-Federation). Zawiera klasy z `Microsoft.IdentityModel.Web` przestrzeni nazw.|
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|Klasy reprezentujące kontrakty, kanały, hosty usług i inne artefakty, które są używane w scenariuszach Active (WS-Trust), są teraz w tej przestrzeni nazw. W WIF 3,5 te klasy znajdowały się w `Microsoft.IdentityModel.Protocols.WSTrust` przestrzeni nazw.|

> [!IMPORTANT]
> Następujące `System.IdentityModel` przestrzenie nazw zawierają klasy implementujące model tożsamości oparty na oświadczeniach WCF <xref:System.IdentityModel.Claims?displayProperty=nameWithType>: <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Nie należy używać klas w tych trzech przestrzeniach nazw podczas kompilowania rozwiązań opartych na WIF.

### <a name="changes-due-to-net-integration"></a>Zmiany ze względu na integrację z platformą .NET

WIF jest teraz zintegrowana z .NET Framework. Większość tożsamości i klas głównych platformy .NET pochodzi teraz <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> od <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>i. Wynikiem są następujące zmiany w WIF 4,5:

- Klasy WIF, które reprezentują oświadczenia, tożsamości i podmioty zabezpieczeń, już istnieją w <xref:System.Security.Claims?displayProperty=nameWithType> przestrzeni nazw.

    > [!IMPORTANT]
    > <xref:System.IdentityModel.Claims?displayProperty=nameWithType> Przestrzeń nazw zawiera klasy reprezentujące artefakty w modelu tożsamości opartego na oświadczeniach programu WCF. Wiele z tych klas ma nazwy, które są takie same jak klasy WIF; na przykład `Claims`. Nie należy używać tych klas podczas kompilowania rozwiązań opartych na WIF.

- Tożsamości i klasy główne platformy .NET teraz pochodzą bezpośrednio <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> z <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>i, które reprezentują tożsamości i podmioty zabezpieczeń oparte na oświadczeniach. Z tego powodu interfejsy `IClaimsIdentity` WIF 3,5 i `IClaimsPrincipal` nie są już potrzebne i nie są dostępne w WIF 4,5.

- Because.NET tożsamość i główne klasy, takie <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> jak <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> i teraz pochodzą <xref:System.Security.Claims.ClaimsIdentity> od <xref:System.Security.Claims.ClaimsPrincipal>i, mają wbudowaną funkcję oświadczeń. Z tego powodu tożsamości specyficzne dla oświadczeń i klasy główne, takie jak `WindowsClaimsIdentity` i `WindowsClaimsPrincipal` , które znajdowały się w WIF 3,5, nie są już potrzebne i nie istnieją w WIF 4,5.

### <a name="other-changes-to-wif-functionality"></a>Inne zmiany w funkcji WIF

Poza zmianami przestrzeni nazw i zmianami spowodowanymi integracją z platformą .NET, następujące ogólne zmiany funkcji WIF są wykonywane w WIF 4,5.

- `Microsoft.IdentityModel.ExceptionMapper` Klasa, która udostępnia funkcje, które umożliwiają mapowanie wyjątków do określonych błędów SOAP, jest usuwana.

- Powierzchnia wyjątku została znacznie zmniejszona.

- Wiele klas, które zostały określone przez określony protokół lub protokołu WS-*, zostało usunięte. na przykład `Microsoft.IdentityModel.WSAddressing10Constants` Klasa, która definiuje stałe powiązane z WS-Addressing 1,0.

- Oświadczenia do usługi tokenu systemu Windows (C2WTS) i skojarzonych z nią klas w `Microsoft.IdentityModel.WindowsTokenService` przestrzeni nazw są usuwane.

### <a name="wif-configuration-changes"></a>WIF zmiany konfiguracji

Wiele zmian w pliku konfiguracyjnym zostało spowodowanych przez aktualizacje przestrzeni nazw w WIF 4,5. Rozważmy na przykład następujący wpis WIF 3,5 w `<httpModules>` sekcji, aby dodać Menedżera uwierzytelniania usługi WS-Federation do aplikacji:

```xml
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />
```

Ten wpis został zaktualizowany w WIF 4,5, aby uwzględnić nowe przestrzenie nazw i wersję zestawu:

```xml
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>
```

Poniższa lista zawiera Wyliczenie najważniejszych zmian w pliku konfiguracji dla WIF 4,5.

- Sekcja jest teraz sekcją [> System.IdentityModel.\<](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) `<microsoft.identityModel>`

- Element jest teraz elementem IdentityConfiguration >. [ \<](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) `<service>`

- Dodano nową sekcję [ \<system. IdentityModel. Services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), która umożliwia określenie ustawień kontrolujących zachowanie w scenariuszach pasywnych (WS-Federation).

- Element federationConfiguration > i jego elementy podrzędne zostały przeniesione z `<service>` elementu WIF 3,5 do nowego `<system.identityModel.services>` elementu. [ \<](../configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)

- Kilka elementów, które można określić na poziomie usług bezpośrednio pod `<service>` elementem w WIF 3,5, [ \<](../configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) zostały ograniczone do określonych w elemencie securityTokenHandlerConfiguration >. (Mogą być one nadal określone [ \<w IdentityConfiguration >](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu WIF 4,5 dla zgodności z poprzednimi wersjami).

Aby uzyskać pełną listę elementów konfiguracji WIF 4,5, zobacz [WIF Configuration Schema](../configure-apps/file-schema/windows-identity-foundation/index.md).

### <a name="visual-studio-tooling-changes"></a>Zmiany narzędzi programu Visual Studio

Zestaw WIF 3,5 SDK oferuje autonomiczne narzędzie federacyjne, FedUtil. exe (FedUtil), którego można użyć do zarządzania tożsamościami w aplikacjach z obsługą WIFymi do usługi tokenu zabezpieczającego (STS). To narzędzie dodaliśmy ustawienia WIF do pliku konfiguracji aplikacji, aby umożliwić aplikacji pobieranie tokenów zabezpieczających z jednego lub większej liczby usług STS i zostały utworzone w programie Visual Studio za pomocą przycisku **Dodaj odwołanie do usługi STS** . FedUtil nie jest dostarczany z WIF 4,5. Zamiast tego WIF 4,5 obsługuje nowe rozszerzenie programu Visual Studio o nazwie Narzędzie do obsługi tożsamości i dostępu dla programu Visual Studio 2012, którego można użyć do zmodyfikowania pliku konfiguracyjnego aplikacji za pomocą ustawień WIF wymaganych do zarządzania tożsamościami w usłudze STS. Narzędzie do obsługi tożsamości i dostępu implementuje także usługę STS o nazwie Local STS, która umożliwia testowanie aplikacji z obsługą WIF. W wielu przypadkach ta funkcja eliminuje konieczność tworzenia niestandardowych usług STS, które były często niezbędne w WIF 3,5 do testowania rozwiązań w fazie opracowywania. Z tego powodu szablony usługi STS nie są już obsługiwane w programie Visual Studio 2012; jednak klasy obsługujące programowanie usług STS są nadal dostępne w WIF 4,5.

Narzędzie tożsamość i dostęp można zainstalować z poziomu rozszerzeń i programu Updates Manager w programie Visual Studio lub pobrać je z następującej strony w galerii kodu: [Narzędzie tożsamości i dostępu dla programu Visual Studio 2012 w galerii kodu](https://go.microsoft.com/fwlink/?LinkID=245849). Zmiany narzędzi programu Visual Studio zostały podsumowane na poniższej liście:

- Funkcja dodawania odwołań do usługi STS jest usuwana. Zastępowanie to narzędzie tożsamości i dostępu.

- Szablony programu Visual Studio STS są usuwane. Możesz użyć lokalnej usługi STS dostępnej za pomocą narzędzia tożsamości i dostępu do testowania rozwiązań do tworzenia tożsamości, które opracowujesz przy użyciu WIF. Lokalną konfigurację usługi STS można zmodyfikować, aby dostosować oświadczenia, które obsługuje.

- Autonomiczne narzędzie federacyjne (FedUtil) nie jest dostępne w WIF 4,5. Za pomocą narzędzia tożsamości i dostępu można modyfikować pliki konfiguracji w celu zarządzania tożsamościami w usłudze STS.

Aby uzyskać więcej informacji na temat narzędzia tożsamości i dostępu, zobacz [Narzędzie tożsamości i dostępu dla programu Visual Studio 2012](identity-and-access-tool-for-vs.md)

<a name="BKMK_ToolingChanges"></a>

### <a name="passive-ws-federation-scenarios"></a>Scenariusze pasywne (WS-Federation):

- Klasy obsługujące scenariusze pasywne zostały przeniesione do <xref:System.IdentityModel.Services?displayProperty=nameWithType> przestrzeni nazw. W WIF 3,5 te klasy znajdowały się w `Microsoft.IdentityModel.Web` przestrzeni nazw.

- Klasy w `Microsoft.IdentityModel.Web.Configuration` przestrzeni nazw zostały przeniesione do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Klasy te reprezentują obiekty specyficzne dla konfiguracji w scenariuszach pasywnych.

- Program nie `Microsoft.IdentityModel.Web.Controls` jest już obsługiwany; wszystkie klasy w przestrzeni nazw zostały usunięte z WIF 4,5. `FederatedPassiveSignInControl`

- Funkcja wylogowywania modułu uwierzytelniania WS-<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>Federation () jest różna od WIF 3,5. Aby uzyskać więcej informacji na temat sposobu wylogowania w programie WIF 4,5, zobacz <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> temat Klasa.

### <a name="active-wcfws-trust-scenarios"></a>Scenariusze aktywne (WCF/WS-Trust):

- `Microsoft.IdentityModel.Protocols.WSTrust` Przestrzeń nazw została podzielona głównie na dwie przestrzenie nazw w WIF 4,5. Klasy reprezentujące artefakty, które są specyficzne dla protokołu WS-Trust, są <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>teraz w. Obejmuje to takie klasy <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>jak. Klasy reprezentujące kontrakty usługi, kanały, hosty usług i inne artefakty, które są związane z korzystaniem z protokołu WS-Trust <xref:System.ServiceModel.Security?displayProperty=nameWithType>w aplikacjach WCF, zostały <xref:System.ServiceModel.Security.IWSTrust13AsyncContract> przeniesione do lokalizacji, na przykład w interfejsie.

- Konfigurowanie aplikacji WCF do użycia WIF zostało znacznie uproszczone. Wcześniej musiał zostać dodany jako rozszerzenie zachowania, a ta funkcja była używana do klinowania WIF do zachowania usługi przez `<federatedServiceHostConfiguration>` określenie elementu. `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` WIF 4,5 jest ściśle zintegrowany z WCF. Teraz można włączyć `useIdentityConfiguration` WIF w usłudze WCF, określając atrybut `<behaviors>` / / `<system.serviceModel>` `<serviceBehaviors>` welemencie,jakwponiższymkodzieXML:/ `<serviceCredentials>`

    ```xml
    <serviceCredentials useIdentityConfiguration="true">
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />
    </serviceCredentials>
    ```

- W WIF 4,5 należy określić certyfikat usługi używany przez aktywną usługę (WCF) na hoście usługi. W obszarze Konfiguracja można wykonać tę czynność za pomocą `<system.serviceModel>` / `<serviceBehaviors>` `<behaviors>` / elementu,/ jak pokazano w powyższym przykładzie. `<serviceCredentials>` / `<serviceCertificate>` W WIF 3,5 można określić certyfikat usługi za pomocą `<serviceCertificate>` elementu podrzędnego elementu WIF. `<service>` Ta funkcja nie istnieje w WIF 4,5; `<serviceCertificate>` Określ element `<serviceCredentials>` zamiast elementu.

- Klasy używane do klinowania WIF 3,5 do WCF już nie istnieją. Obejmuje to następujące `Microsoft.IdentityModel.Tokens` klasy w przestrzeni nazw: `FederatedSecurityTokenManager`, `FederatedServiceCredentials`, i, `IdentityModelServiceAuthorizationManager`a także `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` klasę.

## <a name="enabling-wif-35-in-windows-8"></a>Włączanie WIF 3,5 w systemie Windows 8

Ponieważ WIF 4,5 jest częścią programu .NET 4,5, jest on automatycznie włączany na komputerach z systemem Windows 8 i Windows Server 2012, a aplikacje utworzone przy użyciu usługi WIF 4,5 będą domyślnie uruchamiane w systemie Windows 8 lub Windows Server 2012. Jednak może być konieczne uruchomienie aplikacji, które zostały skompilowane przy użyciu WIF 3,5 na komputerze z systemem Windows 8 lub Windows Server 2012. W takim przypadku należy włączyć WIF 3,5 na komputerze docelowym. Na komputerze z systemem Windows 8 można to zrobić za pomocą narzędzia Obsługa i zarządzanie obrazami wdrażania (DISM). Na komputerze z systemem Windows Server 2012 można użyć narzędzia DISM lub użyć polecenia cmdlet programu Windows PowerShell `Add-WindowsFeature` . W obu przypadkach odpowiednie polecenia można wywołać w wierszu polecenia lub w środowisku środowiska Windows PowerShell.

Poniższe polecenia pokazują, jak używać narzędzia DISM z wiersza polecenia lub z wnętrza środowiska Windows PowerShell. Domyślnie moduł DISM programu PowerShell jest dołączony do systemu Windows 8 i Windows Server 2012 i nie musi zostać zaimportowany. Aby uzyskać więcej informacji na temat używania narzędzia DISM z programem Windows PowerShell, zobacz [jak używać narzędzia DISM w programie Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=254419).

Aby włączyć WIF 3,5 przy użyciu narzędzia DISM:

```console
dism /online /enable-feature:windows-identity-foundation
```

Aby wyłączyć WIF 3,5 przy użyciu narzędzia DISM:

```console
dism /online /disable-feature:windows-identity-foundation
```

Aby sprawdzić, które funkcje są włączone lub wyłączone za pomocą narzędzia DISM:

```console
dism /online /get-features
```

Alternatywnie na komputerach z systemem Windows Server 2012 można włączyć WIF 3,5 przy użyciu polecenia cmdlet programu Windows PowerShell `Add-WindowsFeature` . W tym celu w wierszu polecenia można wprowadzić następujące polecenie:

```console
powershell "add-windowsfeature windows-identity-foundation"
```

 W środowisku programu Windows PowerShell można bezpośrednio wprowadzić polecenie:

```powershell
Add-WindowsFeature windows-identity-foundation
```

> [!NOTE]
> Ponieważ wiele klas w WIF 3,5 i WIF 4,5 współużytkują te same nazwy, w przypadku używania zarówno WIF 3,5 i WIF 4,5, pamiętaj, aby użyć w pełni kwalifikowanych nazw klas lub użyć aliasów przestrzeni nazw do rozróżniania klas w WIF 3,5 i WIF 4,5.

## <a name="see-also"></a>Zobacz także

- [Schemat konfiguracji programu WIF](../configure-apps/file-schema/windows-identity-foundation/index.md)
- [Mapowanie przestrzeni nazw między programami WIF 3.5 i WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Co nowego w programie Windows Identity Foundation 4.5](whats-new-in-wif.md)
- [Narzędzie tożsamości i dostępu dla programu Visual Studio 2012](identity-and-access-tool-for-vs.md)
