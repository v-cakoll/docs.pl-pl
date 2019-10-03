---
title: Wskazówki dotyczące migrowania aplikacji utworzonych za pomocą programu WIF 3.5 do wersji WIF 4.5
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
ms.openlocfilehash: 645fd09de91d8190384faea9df2ef18511162c2f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834522"
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

W WIF 3,5 wszystkie klasy WIF zostały zawarte w zestawie `Microsoft.IdentityModel` (Microsoft. identitymicrosoft. IdentityModel. dll). W WIF 4,5 klasy WIF zostały podzielone na następujące zestawy: `mscorlib` (mscorlib. dll), `System.IdentityModel` (System. IdentityModel. dll), `System.IdentityModel.Services` (System. IdentityModel. Services. dll) i `System.ServiceModel` (System. ServiceModel. dll).

Wszystkie klasy WIF 3,5 zostały zawarte w jednej z przestrzeni nazw `Microsoft.IdentityModel`; na przykład `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web` i tak dalej. W WIF 4,5 klasy WIF są teraz rozmieszczane w przestrzeni nazw [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) , przestrzeni nazw <xref:System.Security.Claims?displayProperty=nameWithType> i przestrzeni nazw <xref:System.ServiceModel.Security?displayProperty=nameWithType>. Poza tą reorganizacją niektóre klasy WIF 3,5 zostały porzucone w WIF 4,5.

W poniższej tabeli przedstawiono niektóre z ważniejszych przestrzeni nazw WIF 4,5 i rodzaj klas, które zawierają. Aby uzyskać bardziej szczegółowe informacje na temat sposobu mapowania przestrzeni nazw między WIF 3,5 i WIF 4,5 oraz o przestrzeniach nazw i klasach, które zostały porzucone w WIF 4,5, zobacz [mapowanie przestrzeni nazw między WIF 3,5 i WIF 4,5](namespace-mapping-between-wif-3-5-and-wif-4-5.md).

|WIF 4,5 — przestrzeń nazw|Opis|
|-----------------------|-----------------|
|<xref:System.IdentityModel?displayProperty=nameWithType>|Zawiera klasy reprezentujące przekształcenia plików cookie, usługi tokenów zabezpieczających i wyspecjalizowane czytniki słownika XML. Zawiera klasy z następujących przestrzeni nazw WIF 3,5: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService` i `Microsoft.IdentityModel.Threading`.|
|<xref:System.Security.Claims?displayProperty=nameWithType>|Zawiera klasy reprezentujące oświadczenia, tożsamości oparte na oświadczeniach, podmioty zabezpieczeń oparte na oświadczeniach oraz inne artefakty modelu tożsamości oparte na oświadczeniach. Zawiera klasy z przestrzeni nazw `Microsoft.IdentityModel.Claims`.|
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Zawiera klasy reprezentujące tokeny zabezpieczające, programy obsługi tokenów zabezpieczających i inne artefakty tokenów zabezpieczających. Zawiera klasy z następujących przestrzeni nazw WIF 3,5: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11` i `Microsoft.IdentityModel.Tokens.Saml2`.|
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Zawiera klasy, które są używane w scenariuszach pasywnych (WS-Federation). Zawiera klasy z przestrzeni nazw `Microsoft.IdentityModel.Web`.|
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|Klasy reprezentujące kontrakty, kanały, hosty usług i inne artefakty, które są używane w scenariuszach Active (WS-Trust), są teraz w tej przestrzeni nazw. W WIF 3,5 te klasy znajdowały się w przestrzeni nazw `Microsoft.IdentityModel.Protocols.WSTrust`.|

> [!IMPORTANT]
> Następujące przestrzenie nazw `System.IdentityModel` zawierają klasy implementujące model tożsamości opartych na oświadczeniach WCF: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> i <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Model zarządzania tożsamościami oparty na oświadczeniach stosowany w środowisku WCF jest zastąpiony modelem ze środowiska WIF. Nie należy używać klas w tych trzech przestrzeniach nazw podczas kompilowania rozwiązań opartych na WIF.

### <a name="changes-due-to-net-integration"></a>Zmiany ze względu na integrację z platformą .NET

WIF jest teraz zintegrowana z .NET Framework. Większość tożsamości i klas głównych platformy .NET pochodzi teraz od <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. Wynikiem są następujące zmiany w WIF 4,5:

- Klasy WIF, które reprezentują oświadczenia, tożsamości i podmioty zabezpieczeń, teraz istnieją w przestrzeni nazw <xref:System.Security.Claims?displayProperty=nameWithType>.

    > [!IMPORTANT]
    > Przestrzeń nazw <xref:System.IdentityModel.Claims?displayProperty=nameWithType> zawiera klasy reprezentujące artefakty w modelu tożsamości opartego na oświadczeniach programu WCF. Wiele z tych klas ma nazwy, które są takie same jak klasy WIF; na przykład `Claims`. Nie należy używać tych klas podczas kompilowania rozwiązań opartych na WIF.

- Tożsamości platformy .NET i klasy główne teraz pochodzą bezpośrednio od <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> i <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, które reprezentują tożsamości i podmioty zabezpieczeń oparte na oświadczeniach. Z tego powodu interfejsy WIF 3,5 `IClaimsIdentity` i `IClaimsPrincipal` nie są już potrzebne i nie są dostępne w WIF 4,5.

- Because.NET Identity i Principal Classes, takie jak <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> i <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType>, teraz pochodzą od <xref:System.Security.Claims.ClaimsIdentity> i <xref:System.Security.Claims.ClaimsPrincipal>, mają wbudowaną funkcję oświadczenia. Z tego powodu tożsamości specyficzne dla oświadczeń i klasy główne, takie jak `WindowsClaimsIdentity` i `WindowsClaimsPrincipal`, które były obecne w WIF 3,5, nie są już potrzebne i nie istnieją w WIF 4,5.

### <a name="other-changes-to-wif-functionality"></a>Inne zmiany w funkcji WIF

Poza zmianami przestrzeni nazw i zmianami spowodowanymi integracją z platformą .NET, następujące ogólne zmiany funkcji WIF są wykonywane w WIF 4,5.

- Klasa `Microsoft.IdentityModel.ExceptionMapper`, która udostępnia funkcje, które umożliwiają mapowanie wyjątków do określonych błędów SOAP, jest usuwana.

- Powierzchnia wyjątku została znacznie zmniejszona.

- Wiele klas, które zostały określone przez określony protokół lub protokołu WS-*, zostało usunięte. na przykład Klasa `Microsoft.IdentityModel.WSAddressing10Constants`, która definiuje stałe związane z WS-Addressing 1,0.

- Oświadczenia do usługi tokenu systemu Windows (C2WTS) i skojarzonych z nimi klas w przestrzeni nazw `Microsoft.IdentityModel.WindowsTokenService` są usuwane.

### <a name="wif-configuration-changes"></a>WIF zmiany konfiguracji

Wiele zmian w pliku konfiguracyjnym zostało spowodowanych przez aktualizacje przestrzeni nazw w WIF 4,5. Rozważmy na przykład następujący wpis WIF 3,5 w sekcji `<httpModules>`, aby dodać Menedżera uwierzytelniania WS-Federation do aplikacji:

```xml
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />
```

Ten wpis został zaktualizowany w WIF 4,5, aby uwzględnić nowe przestrzenie nazw i wersję zestawu:

```xml
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>
```

Poniższa lista zawiera Wyliczenie najważniejszych zmian w pliku konfiguracji dla WIF 4,5.

- Sekcja `<microsoft.identityModel>` jest teraz sekcją [> \<System. IdentityModel](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) .

- Element `<service>` jest teraz elementem [> \<identityConfiguration](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) .

- Dodano nową sekcję [\<System. IdentityModel. services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), aby określić ustawienia kontrolujące zachowanie w scenariuszach pasywnych (WS-Federation).

- Element [\<federationConfiguration >](../configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) i jego elementy podrzędne zostały przeniesione z elementu `<service>` w WIF 3,5 do nowego elementu `<system.identityModel.services>`.

- Kilka elementów, które można określić na poziomie usług bezpośrednio pod elementem `<service>` w WIF 3,5, zostały ograniczone do określonych w elemencie [> \<securityTokenHandlerConfiguration](../configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) . (Mogą być one nadal określone w [@no__t 1identityConfiguration >](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu WIF 4,5 dla zgodności z poprzednimi wersjami).

Aby uzyskać pełną listę elementów konfiguracji WIF 4,5, zobacz [WIF Configuration Schema](../configure-apps/file-schema/windows-identity-foundation/index.md).

### <a name="visual-studio-tooling-changes"></a>Zmiany narzędzi programu Visual Studio

Zestaw WIF 3,5 SDK oferuje autonomiczne narzędzie federacyjne, FedUtil. exe (FedUtil), którego można użyć do zarządzania tożsamościami w aplikacjach z obsługą WIFymi do usługi tokenu zabezpieczającego (STS). To narzędzie dodaliśmy ustawienia WIF do pliku konfiguracji aplikacji, aby umożliwić aplikacji pobieranie tokenów zabezpieczających z jednego lub większej liczby usług STS i zostały utworzone w programie Visual Studio za pomocą przycisku **Dodaj odwołanie do usługi STS** . FedUtil nie jest dostarczany z WIF 4,5. Zamiast tego WIF 4,5 obsługuje nowe rozszerzenie programu Visual Studio o nazwie Narzędzie do obsługi tożsamości i dostępu dla programu Visual Studio 2012, którego można użyć do zmodyfikowania pliku konfiguracyjnego aplikacji za pomocą ustawień WIF wymaganych do zarządzania tożsamościami w usłudze STS. Narzędzie do obsługi tożsamości i dostępu implementuje także usługę STS o nazwie Local STS, która umożliwia testowanie aplikacji z obsługą WIF. W wielu przypadkach ta funkcja eliminuje konieczność tworzenia niestandardowych usług STS, które były często niezbędne w WIF 3,5 do testowania rozwiązań w fazie opracowywania. Z tego powodu szablony usługi STS nie są już obsługiwane w programie Visual Studio 2012; jednak klasy obsługujące programowanie usług STS są nadal dostępne w WIF 4,5.

Narzędzie tożsamość i dostęp można zainstalować z poziomu rozszerzeń i programu Updates Manager w programie Visual Studio lub pobrać je z następującej strony w galerii kodu: narzędzia do zarządzania [tożsamościami i dostępem dla programu Visual Studio 2012 w galerii kodu](https://go.microsoft.com/fwlink/?LinkID=245849). Zmiany narzędzi programu Visual Studio zostały podsumowane na poniższej liście:

- Funkcja dodawania odwołań do usługi STS jest usuwana. Zastępowanie to narzędzie tożsamości i dostępu.

- Szablony programu Visual Studio STS są usuwane. Możesz użyć lokalnej usługi STS dostępnej za pomocą narzędzia tożsamości i dostępu do testowania rozwiązań do tworzenia tożsamości, które opracowujesz przy użyciu WIF. Lokalną konfigurację usługi STS można zmodyfikować, aby dostosować oświadczenia, które obsługuje.

- Autonomiczne narzędzie federacyjne (FedUtil) nie jest dostępne w WIF 4,5. Za pomocą narzędzia tożsamości i dostępu można modyfikować pliki konfiguracji w celu zarządzania tożsamościami w usłudze STS.

Aby uzyskać więcej informacji na temat narzędzia tożsamości i dostępu, zobacz [Narzędzie tożsamości i dostępu dla programu Visual Studio 2012](identity-and-access-tool-for-vs.md).

<a name="BKMK_ToolingChanges"></a>

### <a name="passive-ws-federation-scenarios"></a>Scenariusze pasywne (WS-Federation):

- Klasy obsługujące scenariusze pasywne zostały przeniesione do przestrzeni nazw <xref:System.IdentityModel.Services?displayProperty=nameWithType>. W WIF 3,5 te klasy znajdowały się w przestrzeni nazw `Microsoft.IdentityModel.Web`.

- Klasy w przestrzeni nazw `Microsoft.IdentityModel.Web.Configuration` zostały przeniesione do <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Klasy te reprezentują obiekty specyficzne dla konfiguracji w scenariuszach pasywnych.

- @No__t-0 nie jest już obsługiwana; wszystkie klasy w przestrzeni nazw `Microsoft.IdentityModel.Web.Controls` zostały usunięte z WIF 4,5.

- Funkcja wylogowywania modułu uwierzytelniania WS-Federation (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) jest różna od WIF 3,5. Aby uzyskać więcej informacji na temat sposobu wylogowania w programie WIF 4,5, zobacz temat klasy <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>.

### <a name="active-wcfws-trust-scenarios"></a>Scenariusze aktywne (WCF/WS-Trust):

- Przestrzeń nazw `Microsoft.IdentityModel.Protocols.WSTrust` została podzielona głównie na dwie przestrzenie nazw w WIF 4,5. Klasy reprezentujące artefakty, które są specyficzne dla protokołu WS-Trust, są teraz w <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. Obejmuje to takie klasy jak <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Klasy reprezentujące kontrakty usługi, kanały, hosty usług i inne artefakty, które są związane z korzystaniem z protokołu WS-Trust w aplikacjach WCF, zostały przeniesione do <xref:System.ServiceModel.Security?displayProperty=nameWithType>; na przykład interfejs <xref:System.ServiceModel.Security.IWSTrust13AsyncContract>.

- Konfigurowanie aplikacji WCF do użycia WIF zostało znacznie uproszczone. Wcześniej `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` musiała zostać dodana jako rozszerzenie zachowania, a ta funkcja była używana do klinowania WIF do zachowania usługi przez określenie elementu `<federatedServiceHostConfiguration>`. WIF 4,5 jest ściśle zintegrowany z WCF. Teraz można włączyć WIF w usłudze WCF, określając atrybut `useIdentityConfiguration` w `<system.serviceModel>` @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7, jak w poniższym kodzie XML:

    ```xml
    <serviceCredentials useIdentityConfiguration="true">
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />
    </serviceCredentials>
    ```

- W WIF 4,5 należy określić certyfikat usługi używany przez aktywną usługę (WCF) na hoście usługi. W konfiguracji można to zrobić za pomocą `<system.serviceModel>` @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8, jak pokazano w poprzednim przykładzie. W WIF 3,5 można określić certyfikat usługi za pomocą elementu podrzędnego `<serviceCertificate>` elementu WIF `<service>`. Ta funkcja nie istnieje w WIF 4,5; w zamian Określ element `<serviceCertificate>` pod elementem `<serviceCredentials>`.

- Klasy używane do klinowania WIF 3,5 do WCF już nie istnieją. Obejmuje to następujące klasy w przestrzeni nazw `Microsoft.IdentityModel.Tokens`: `FederatedSecurityTokenManager`, `FederatedServiceCredentials` i `IdentityModelServiceAuthorizationManager`, a także klasy `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement`.

## <a name="enabling-wif-35-in-windows-8"></a>Włączanie WIF 3,5 w systemie Windows 8

Ponieważ WIF 4,5 jest częścią programu .NET 4,5, jest on automatycznie włączany na komputerach z systemem Windows 8 i Windows Server 2012, a aplikacje utworzone przy użyciu usługi WIF 4,5 będą domyślnie uruchamiane w systemie Windows 8 lub Windows Server 2012. Jednak może być konieczne uruchomienie aplikacji, które zostały skompilowane przy użyciu WIF 3,5 na komputerze z systemem Windows 8 lub Windows Server 2012. W takim przypadku należy włączyć WIF 3,5 na komputerze docelowym. Na komputerze z systemem Windows 8 można to zrobić za pomocą narzędzia Obsługa i zarządzanie obrazami wdrażania (DISM). Na komputerze z systemem Windows Server 2012 można użyć narzędzia DISM lub użyć polecenia cmdlet `Add-WindowsFeature` programu Windows PowerShell. W obu przypadkach odpowiednie polecenia można wywołać w wierszu polecenia lub w środowisku środowiska Windows PowerShell.

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

Alternatywnie na komputerach z systemem Windows Server 2012 można włączyć WIF 3,5 przy użyciu polecenia cmdlet `Add-WindowsFeature` programu Windows PowerShell. W tym celu w wierszu polecenia można wprowadzić następujące polecenie:

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
