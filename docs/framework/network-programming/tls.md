---
title: Transport Layer Security (TLS) najlepszych rozwiązań za pomocą programu .NET Framework
description: W tym artykule opisano najlepsze rozwiązania przy użyciu zabezpieczeń TLS (Transport Layer) za pomocą programu .NET Framework
ms.date: 03/15/2018
helpviewer_keywords:
- sending data, Internet security
- protocols, Internet security
- Network security
- network resources, Internet security
- receiving data, Internet security
- authentication [.NET Framework], Internet security
- Internet, security
- security [.NET Framework], Internet
- permissions [.NET Framework], Internet
author: blowdart
ms.openlocfilehash: a421b73edc1dd90be53d301d12160d39abe78f90
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577733"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Transport Layer Security (TLS) najlepszych rozwiązań za pomocą programu .NET Framework

Protokołu Transport Layer Security (TLS) jest standardem branżowym, zaprojektowany w celu ochrony prywatności informacji przekazywanych za pośrednictwem Internetu. [Protokół TLS 1.2](https://tools.ietf.org/html/rfc5246) to najnowsza standard wydana i zawiera ulepszenia bezpieczeństwa w porównaniu z poprzednimi wersjami. Protokół TLS 1.2 po pewnym czasie zostaną zastąpione przez [TLS 1.3](https://tools.ietf.org/html/draft-ietf-tls-tls13-22). W tym artykule przedstawiono zalecenia w celu zabezpieczenia aplikacji .NET Framework, które używają protokołu TLS.

Aby upewnić się, .NET Framework, aplikacje będą nadal bezpiecznego, powinien wersję protokołu TLS **nie** być zapisane na stałe. .NET framework aplikacje powinny używać wersji protokołu TLS, który obsługuje systemu operacyjnego (OS).

Ten dokument jest przeznaczony dla deweloperów, którzy są:

- Bezpośrednio przy użyciu <xref:System.Net> interfejsy API (na przykład <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- Bezpośrednio przy użyciu klientów usług WCF i usługami korzystającymi z <xref:System.ServiceModel?displayProperty=nameWithType> przestrzeni nazw.
- Za pomocą [usług Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) role sieć Web i proces roboczy, hostowanie i uruchamianie aplikacji. Zobacz [usług Azure Cloud Services](#azure-cloud-services) sekcji.

Zaleca się, możesz:

- Docelowy .NET Framework 4.7 lub nowszej wersji w aplikacjach. Docelowy .NET Framework 4.7.1 lub nowsze wersje w aplikacjach usługi WCF.
- Nie można określić wersji protokołu TLS. Skonfiguruj swój kod, aby umożliwić OS decyzję w sprawie wersji protokołu TLS.
- Wykonaj inspekcji dokładnego kodu, aby sprawdzić, czy nie należy określać wersję protokołu TLS lub SSL.

Gdy aplikacja pozwala systemu operacyjnego, wybierz wersję protokołu TLS:

- Automatycznie wykorzystuje ona nowe protokoły dodane w przyszłości, takie jak TLS 1.3.
- System operacyjny blokuje protokołów, które są odnajdywane nie powinien być bezpieczne.

Sekcja [inspekcji kodu i wprowadzać zmiany kodu](#audit-your-code-and-make-code-changes) obejmuje inspekcji i aktualizowania kodu.

W tym artykule omówiono sposób umożliwienia dostępne dla wersji programu .NET Framework, który jest przeznaczony dla twojej aplikacji i jest uruchamiany na najwyższy poziom zabezpieczeń. Gdy aplikacja jawnie ustawia protokół zabezpieczeń i wersji, zdecyduje poza wszelkie inne alternatywne i oznacza brak środowiska .NET Framework i systemu operacyjnego domyślne zachowanie zgody. Jeśli chcesz, aby aplikacja, aby można było negocjowania połączenia protokołu TLS 1.2, jawne ustawienie do starszej wersji protokołu TLS uniemożliwia połączenie protokołu TLS 1.2.

Jeśli nie można uniknąć hardcoding wersja protokołu, zdecydowanie zaleca się określenie protokołu TLS 1.2. Aby uzyskać wskazówki na identyfikowanie i usuwanie zależności protokołu TLS 1.0, Pobierz [rozwiązywanie problemu protokołu TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266) oficjalny dokument.

TLS1.0 obsługuje WCF, 1.1 i 1.2 jako domyślnego w programie .NET Framework 4.7. Począwszy od .NET Framework 4.7.1 domyślne WCF dla systemu operacyjnego skonfigurowany wersji. Jeśli aplikacja jest jawnie skonfigurowany z `SslProtocols.None`, WCF używa domyślnego ustawienia systemu operacyjnego, gdy za pomocą transportu NetTcp.

Możesz zadawać pytania dotyczące tego dokumentu w problem w usłudze GitHub [zabezpieczeń TLS (Transport Layer) najlepszych rozwiązań za pomocą programu .NET Framework](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Inspekcja kodu i wprowadzać zmiany kodu

Dla aplikacji ASP.NET, należy sprawdzić `<system.web><httpRuntime targetFramework>` elementu _web.config_ Aby sprawdzić, używasz zamierzony wersji programu .NET Framework.

Windows Forms i innych aplikacji, zobacz [jak: docelowa wersja systemu .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

Poniższe sekcje służą do upewnij się, że nie używasz określonej wersji protokołu TLS lub SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Jeśli aplikacja jest przeznaczona na .NET Framework 4.7 lub nowszej wersji

W poniższych sekcjach przedstawiono sposób sprawdzania, nie używasz określonej wersji protokołu TLS lub SSL.

### <a name="for-http-networking"></a>W przypadku protokołu HTTP sieci

<xref:System.Net.ServicePointManager>, przy użyciu programu .NET Framework 4.7 i nowszych wersjach wartość domyślna to wybranie najlepszych protokołu zabezpieczeń i wersji systemu operacyjnego. Aby uzyskać najlepszy wybór domyślnego systemu operacyjnego, jeśli to możliwe, nie jest ustawiana wartość <xref:System.Net.ServicePointManager.SecurityProtocol> właściwości. W przeciwnym wypadku ustaw <xref:System.Net.SecurityProtocolType.SystemDefault>.

W dalszej części tego artykułu nie jest istotne, gdy przeznaczonych dla platformy .NET Framework 4.7 lub nowszej wersji protokołu HTTP sieci.

### <a name="for-tcp-sockets-networking"></a>Dla gniazda TCP z sieci

<xref:System.Net.Security.SslStream>, przy użyciu programu .NET Framework 4.7 i nowszych wersjach wartość domyślna to wybranie najlepszych protokołu zabezpieczeń i wersji systemu operacyjnego. Aby uzyskać najlepszy wybór domyślnego systemu operacyjnego, jeśli to możliwe, nie używaj przeciążenia metody <xref:System.Net.Security.SslStream> , które wymagają jawnie <xref:System.Security.Authentication.SslProtocols> parametru. W przeciwnym razie przekazania <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Zaleca się, że nie używasz <xref:System.Security.Authentication.SslProtocols.Default>; ustawienie `SslProtocols.Default` wymusza użycie protokołu SSL 3.0 /TLS 1.0 i uniemożliwia protokołu TLS 1.2.

Nie jest ustawiana wartość <xref:System.Net.ServicePointManager.SecurityProtocol> właściwości (dla protokołu HTTP sieci).

Nie używaj przeciążenia metody <xref:System.Net.Security.SslStream> , które wymagają jawnie <xref:System.Security.Authentication.SslProtocols> parametr (dla gniazda TCP sieci). Jeśli przekierowanie aplikacji .NET Framework 4.7 lub nowszej wersji można będzie po najlepsze zalecenie rozwiązania.

W pozostałej części tego tematu nie jest istotne, gdy przeznaczonych dla platformy .NET Framework 4.7 lub nowszej wersji protokołu TCP dla gniazd sieci.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Dla protokołu TCP WCF transportu przy użyciu poświadczeń certyfikatu za pomocą zabezpieczeń transportu

Usługi WCF ten sam stos sieciowy jest używana jako pozostałej części programu .NET Framework.

Jeśli obiektem docelowym 4.7.1 WCF jest skonfigurowany do zezwalania systemu operacyjnego wybrać najlepsze protokołu zabezpieczeń domyślnie, chyba że jawnie skonfigurowane:

- W pliku konfiguracyjnym aplikacji.
- **Lub**, w aplikacji w kodzie źródłowym.

Domyślnie .NET Framework 4.7 lub nowszy jest skonfigurowany do używania protokołu TLS 1.2 i umożliwia nawiązywanie połączeń za pomocą protokołu TLS 1.1 i TLS 1.0. Konfigurowanie usługi WCF, aby zezwolić na system operacyjny wybrać najlepszą protokół zabezpieczeń, konfigurując powiązania w celu użycia <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Można go ustawić na <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None` dostęp jest możliwy z <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport` dostęp jest możliwy z <xref:System.ServiceModel.NetTcpBinding.Security>.

Jeśli używasz niestandardowego powiązania:

- Konfigurowanie usługi WCF, aby umożliwić systemu operacyjnego wybrać najlepszą protokół zabezpieczeń, ustawiając <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> używać <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Lub** Skonfiguruj protokół używany przy użyciu ścieżki konfiguracji `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Jeśli jesteś **nie** używanie powiązania niestandardowego **i** ustawiasz wiązania WCF za pomocą konfiguracji, ustaw protokół używany przy użyciu ścieżki konfiguracji `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Aby uzyskać zabezpieczenie wiadomości WCF przy użyciu poświadczeń certyfikatu

.NET framework 4.7 i nowsze wersje, które domyślnie używa protokołu określonego w <xref:System.Net.ServicePointManager.SecurityProtocol> właściwości. Gdy [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` ustawiono `true`, WCF wybiera najlepsze protokołu, maksymalnie protokołu TLS 1.0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Jeśli aplikacja jest przeznaczona na .NET Framework w wersji wcześniejszej niż 4.7

Przeprowadź inspekcję swój kod, aby sprawdzić, czy nie ustawiasz określonej wersji protokołu TLS lub SSL przy użyciu poniższych sekcjach:

### <a name="for-net-framework-46---462-and-not-wcf"></a>Dla programu .NET Framework 4.6 — 4.6.2 i nie WCF

Ustaw `DontEnableSystemDefaultTlsVersions` `AppContext` przełączyć się do `false`. Zobacz [Konfigurowanie zabezpieczeń za pomocą przełączników AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>Dla programu WCF za pomocą platformy .NET Framework 4.6 — 4.6.2 za pomocą zabezpieczeń transportu TCP przy użyciu poświadczeń certyfikatu

Należy zainstalować najnowsze poprawki systemu operacyjnego. Zobacz [aktualizacje zabezpieczeń](#security-updates).

WCF framework automatycznie wybiera protokołu najwyższy dostępny do protokołu TLS 1.2, chyba że jawnie skonfigurujesz wersji protokołu. Aby uzyskać więcej informacji, zobacz poprzednią sekcję [transportu dla TCP usługi WCF, za pomocą zabezpieczeń transportu przy użyciu poświadczeń certyfikatu](#wcf-tcp-cert).

### <a name="for-net-framework-35---452-and-not-wcf"></a>Dla programu .NET Framework 3.5 — 4.5.2 i nie WCF

Zalecane jest uaktualnienie aplikacji do programu .NET Framework 4.7 lub nowszej wersji. Jeśli nie można uaktualnić, wykonaj następujące kroki. W pewnym momencie w przyszłości, aplikacja może przestać działać do momentu uaktualnienia do programu .NET Framework 4.7 lub nowszej wersji.

Ustaw [SchUseStrongCrypto](#schusestrongcrypto) i [SystemDefaultTlsVersions](#systemdefaulttlsversions) kluczy rejestru do 1. Zobacz [Konfigurowanie zabezpieczeń za pomocą rejestru Windows](#configuring-security-via-the-windows-registry). Program .NET Framework w wersji 3.5 obsługuje `SchUseStrongCrypto` Flaga tylko, kiedy jest przekazywana jawną wartość TLS.

Jeśli używasz programu .NET Framework 3.5, należy instalacja poprawki gorąca, dzięki czemu można określić protokołu TLS 1.2, program:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Niezawodność zbiorczy HR-1605 — Obsługa protokołu TLS System domyślnej wersji zawarte w .NET Framework 3.5.1 na Windows 7 z dodatkiem SP1 i Server 2008 R2 z dodatkiem SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Niezawodność pakiet zbiorczy HR-1605 — Obsługa wersji domyślne systemu TLS zawarte w .NET Framework 3.5 w systemie Windows Server 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Pakiet zbiorczy niezawodność 1605 HR - pomocy technicznej dla wersji domyślne systemu TLS zawarte w .NET Framework 3.5 na Windows 8.1 i Windows Server 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | Pakiet poprawek 1605 3154521 dla programu .NET Framework 4.5.2 i 4.5.1 na Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>Dla programu WCF za pomocą platformy .NET Framework 3.5 — 4.5.2 za pomocą zabezpieczeń transportu TCP przy użyciu poświadczeń certyfikatu

Te wersje programu WCF framework są zapisane na stałe wartości, SSL 3.0 i TLS 1.0. Nie można zmienić tych wartości. Należy zaktualizować, a następnie Przekieruj do NET Framework 4.6 lub nowszej wersji, aby używać protokołu TLS 1.1 i 1.2.

## <a name="if-your-app-targets-net-framework-35"></a>Jeśli aplikacja jest przeznaczona na .NET Framework 3.5

Jeśli musisz jawnie ustawić protokół zabezpieczeń, zamiast automatycznego .NET framework lub wyboru systemu operacyjnego protokół zabezpieczeń, należy dodać `SecurityProtocolTypeExtensions` i `SslProtocolsExtension` wyliczenia w kodzie. `SecurityProtocolTypeExtensions` i `SslProtocolsExtension` zawierają wartości dla `Tls12`, `Tls11`i `SystemDefault` wartość. Zobacz [pomocy technicznej dla wersji domyślne systemu TLS zawarte w .NET Framework 3.5 on Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Konfigurowanie zabezpieczeń za pomocą AppContext zmienia (dla platformy .NET Framework 4.6 lub nowszy)

[AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) parametrów opisanych w tej sekcji Jeśli Twojej aplikacji jest przeznaczony dla lub uruchomienia na .NET Framework 4.6 lub nowszy. Czy domyślnie lub jeśli ustawisz je jawnie przełączników należy `false` , jeśli jest to możliwe. Jeśli chcesz skonfigurować zabezpieczenia za pomocą jednego lub obu przełączników, następnie określać zabezpieczenia protokołu wartości w kodzie; Spowoduje to więc przesłonić metodę przełączników.

Przełączniki mają ten sam efekt, czy wykonujesz sieci HTTP (<xref:System.Net.ServicePointManager>) lub TCP gniazd sieci (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Wartość `false` dla `Switch.System.Net.DontEnableSchUseStrongCrypto` powoduje, że aplikację do używania silnej kryptografii. Wartość `false` dla `DontEnableSchUseStrongCrypto` blokach protokołów, które nie są bezpieczne i używa bardziej bezpieczne protokoły (TLS 1.2, TLS 1.1 i TLS 1.0). Aby uzyskać więcej informacji, zobacz [flagi SCH_USE_STRONG_CRYPTO](#the-schusestrongcrypto-flag). Wartość `true` wyłącza silna Kryptografia dla swojej aplikacji.

Jeśli aplikacja jest przeznaczona na .NET Framework 4.6 lub nowszy, ten przełącznik, wartość domyślna to `false`. To bezpieczny domyślna, którą firma Microsoft zaleca. Jeśli aplikacja działa na platformie .NET Framework 4.6, ale jest przeznaczony dla starszej wersji, przełącznika, wartość domyślna to `true`. W takim przypadku należy jawnie ustawić go `false`.

`DontEnableSchUseStrongCrypto` powinien mieć tylko wartość `true` Jeśli potrzebujesz nawiązać starszej wersji usługi, które nie obsługują silnej kryptografii i nie może zostać uaktualniona.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Wartość `false` dla `Switch.System.Net.DontEnableSystemDefaultTlsVersions` powoduje, że system operacyjny wybrać protokół aplikacji. Wartość `true` powoduje, że aplikację w celu korzystania z protokołów pobrane przez program .NET Framework.

Jeśli aplikacja jest przeznaczona na .NET Framework 4.7 lub nowszej wersji, ten przełącznik, wartość domyślna to `false`. To domyślnymi zabezpieczeń, które firma Microsoft zaleca. Jeśli aplikacja działa na .NET Framework 4.7 lub nowszej wersji, ale jest przeznaczony dla starszej wersji, przełącznika, wartość domyślna to `true`. W takim przypadku należy jawnie ustawić go `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Wartość `false` dla `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` powoduje, że aplikacja korzysta z wartości zdefiniowanych w `ServicePointManager.SecurityProtocols` dla zabezpieczenia wiadomości przy użyciu poświadczeń certyfikatu. Wartość `true` korzysta z protokołu najwyższy dostępny, maksymalnie TLS1.0

Dla aplikacji przeznaczonych dla platformy .NET Framework 4.7 i nowszych wersjach, wartością domyślną jest `false`. Dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.2 i wcześniej, wartością domyślną jest `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Wartość `false` dla `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` ustawia domyślną konfigurację, aby system operacyjny wybrać protokół. Wartość `true` ustawiana domyślnie dostępne, maksymalnie TLS1.2 protokołu najwyższy.

Dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 i nowszych wersjach, wartością domyślną jest `false`. Dla aplikacji przeznaczonych dla środowiska .NET Framework w wersji 4.7 lub starszym, wartością domyślną jest `true`.

Aby uzyskać więcej informacji na temat protokoły TLS Zobacz [ograniczenie: protokoły TLS](../migration-guide/mitigation-tls-protocols.md). Aby uzyskać więcej informacji na temat `AppContext` przełączników, zobacz [ `<AppContextSwitchOverrides> Element` ](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Konfigurowanie zabezpieczeń za pomocą rejestru Windows

> [!WARNING]
> Ustawienie kluczy rejestru ma wpływ na wszystkie aplikacje w systemie. Użyj tej opcji tylko wtedy, gdy są dostępne w pełną kontrolę nad maszyną i kontrolować zmiany w rejestrze.

Jeśli ustawienie jedno lub oba `AppContext` przełączniki nie jest to możliwe, można kontrolować protokołów zabezpieczeń, które Twoja aplikacja korzysta z kluczami rejestru Windows, opisane w tej sekcji. Nie można użyć jednego lub obu `AppContext` przełączniki, jeśli aplikacja jest przeznaczona na .NET Framework w wersji starszej niż 4.6 lub nie można edytować plik konfiguracji. Jeśli chcesz skonfigurować zabezpieczenia z rejestrem, następnie określać zabezpieczenia protokołu wartości w kodzie; Spowoduje to więc przesłonić metodę rejestru.

Nazwy kluczy rejestru, które są podobne do nazwy odpowiadającego `AppContext` zmienia, ale bez `DontEnable` dołączona do nazwy. Na przykład `AppContext` Przełącz `DontEnableSchUseStrongCrypto` nosi nazwę klucza rejestru [SchUseStrongCrypto](#schusestrongcrypto).

Te klucze są dostępne we wszystkich wersjach systemu .NET Framework, dla których jest najnowsze poprawki zabezpieczeń. Zobacz [aktualizacje zabezpieczeń](#security-updates).

Wszystkie klucze rejestru, w opisany poniżej mają ten sam efekt, czy wykonujesz sieci HTTP (<xref:System.Net.ServicePointManager>) lub TCP gniazd sieci (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` Klucza rejestru ma wartość typu DWORD. Wartość 1 powoduje, że aplikację do używania silnej kryptografii. Silna Kryptografia blokach protokołów, które nie są bezpieczne i używa bardziej bezpieczne protokoły (TLS 1.2, TLS 1.1 i TLS 1.0). Wartość 0 wyłącza silnej kryptografii. Aby uzyskać więcej informacji, zobacz [flagi SCH_USE_STRONG_CRYPTO](#the-schusestrongcrypto-flag).

Jeśli aplikacja jest przeznaczona na .NET Framework 4.6 lub nowszy, ten klucz domyślnie wartość 1. To domyślnymi zabezpieczeń, które firma Microsoft zaleca. Jeśli aplikacja działa na platformie .NET Framework 4.6, ale jest przeznaczony dla starszej wersji, a następnie klucza wartość domyślna to 0. W takim przypadku należy jawnie ustawić jej wartość 1.

Ten klucz powinien mieć tylko wartość 0, jeśli potrzebujesz nawiązać starszej wersji usługi, które nie obsługują silnej kryptografii i nie może zostać uaktualniona.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` Klucza rejestru ma wartość typu DWORD. Wartość 1 powoduje, że system operacyjny wybrać protokół aplikacji. Wartość 0 powoduje, że aplikację w celu korzystania z protokołów pobrane przez program .NET Framework.

`<VERSION>` musi być 4.0.30319 (programu .NET Framework 4 i nowszych) lub v2.0.50727 (programu .NET Framework 3.5).

Jeśli aplikacja jest przeznaczona na .NET Framework 4.7 lub nowszej wersji, ten klucz domyślnie wartość 1. To domyślnymi zabezpieczeń, które firma Microsoft zaleca. Jeśli aplikacja działa na .NET Framework 4.7 lub nowszej wersji, ale jest przeznaczony dla starszej wersji, klucz wartość domyślna 0. W takim przypadku należy jawnie ustawić jej wartość 1.

Aby uzyskać więcej informacji, zobacz [zbiorczej aktualizacji dla systemu Windows 10 w wersji 1511 i systemu Windows Server 2016 Technical Preview 4: 10 maja 2016 r.](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016)

Aby uzyskać więcej informacji na platformie .NET framework 3.5.1, zobacz [obsługę wersji domyślne systemu TLS zawarte w .NET Framework 3.5.1 na Windows 7 z dodatkiem SP1 i Server 2008 R2 z dodatkiem SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Następujące _. REG_ pliku zestawy kluczy rejestru i ich warianty najbardziej bezpieczne wartości:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001
```

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Konfigurowanie protokoły Schannel w rejestrze systemu Windows

Za pomocą rejestru dla szczegółową kontrolę nad tym protokoły, które negocjuje aplikację klienta i/lub serwerem. Aplikacji sieci przechodzi przez Schannel (czyli inną nazwę dla [bezpiecznego kanału](/windows/desktop/SecAuthN/secure-channel). Konfigurując `Schannel`, można skonfigurować zachowanie aplikacji.

Rozpoczynać `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` klucza rejestru. W tym kluczu można utworzyć wszystkie podklucze w zestawie `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1`, i `TLS 1.2`. W ramach każdej z tych podkluczach, można utworzyć podkluczy `Client` i/lub `Server`. W obszarze `Client` i `Server`, można utworzyć wartości DWORD `DisabledByDefault` (0 lub 1) i `Enabled` (0 lub 0xFFFFFFFF).

## <a name="the-schusestrongcrypto-flag"></a>Flaga SCH_USE_STRONG_CRYPTO

Gdy jest włączone (domyślnie przez `AppContext` przełączyć się, lub w rejestrze systemu Windows), .NET Framework używa `SCH_USE_STRONG_CRYPTO` Flaga, gdy aplikacja żąda protokołu zabezpieczeń TLS. `SCH_USE_STRONG_CRYPTO` Flagę można włączyć domyślnie za pomocą `AppContext` przełączyć, lub za pomocą rejestru. System operacyjny przekazuje flagi `Schannel`można wydać polecenie wyłączenia znanych stosowania słabych algorytmów kryptograficznych, cipher zestawów i wersji protokołu TLS/SSL, które może być inaczej włączona dla lepsze współdziałanie. Aby uzyskać więcej informacji, zobacz:

- [Należy zabezpieczyć kanał](/windows/desktop/SecAuthN/secure-channel)
- [Struktura SCHANNEL_CRED](/windows/desktop/api/schannel/ns-schannel-_schannel_cred)

`SCH_USE_STRONG_CRYPTO` Flagi również jest przekazywany do `Schannel` jawnie zastosowania `Tls` (TLS 1.0) `Tls11`, lub `Tls12` wyliczonych wartości <xref:System.Net.SecurityProtocolType> lub <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Aktualizacje zabezpieczeń

Najlepsze praktyki w tym artykule są zależne od najnowszych aktualizacji zabezpieczeń, które są zainstalowane. Te aktualizacje obejmują możliwość korzystania z zaawansowanych .NET Framework 4.7 i funkcje. Najnowsze aktualizacje zabezpieczeń są ważne, jeśli aplikacja działa w .NET Framework 4.7 i nowszych wersjach (nawet jeśli jest on przeznaczony dla starszej wersji).

Aby zaktualizować .NET Framework, aby system operacyjny wybrać najlepszą wersję protokołu TLS do użycia, należy zainstalować co najmniej:

- [.NET Framework sierpnia 2017 w wersji zapoznawczej pakietu zbiorczego jakości](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup).
- **Lub** [zabezpieczeń programu .NET Framework września 2017 r. i jakości Rollup](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup).

Zobacz też:

- [Wersje programu .NET framework i zależności](../migration-guide/versions-and-dependencies.md)
- [Porady: Określanie, które wersje programu .NET Framework są zainstalowane](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Obsługa protokołu TLS 1.2

Aplikację w celu negocjowania protokołu TLS 1.2, systemu operacyjnego i wersji programu .NET Framework zarówno na potrzeby obsługi protokołu TLS 1.2.

**Wymagania dotyczące systemu operacyjnego do obsługi protokołu TLS 1.2**

Aby włączyć lub ponownie włączyć protokół TLS 1.2 i/lub protokołu TLS 1.1 w systemie, który obsługuje takie, zobacz [zabezpieczeń TLS (Transport Layer), ustawień rejestru](/windows-server/security/tls/tls-registry-settings).

| **OS** | **Obsługa protokołu TLS 1.2** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | Obsługiwane i domyślnie włączona. |
| Windows 8.1</br>Windows Server 2012 z dodatkiem R2 | Obsługiwane i domyślnie włączona. |
| Windows 8.0</br>Windows Server 2012 | Obsługiwane i domyślnie włączona. |
| Windows 7 z dodatkiem SP1</br>Windows Server 2008 R2 SP1 | Obsługiwane, ale nie jest włączony domyślnie. Zobacz [zabezpieczeń TLS (Transport Layer), ustawień rejestru](/windows-server/security/tls/tls-registry-settings) strony sieci web, aby uzyskać szczegółowe informacje o sposobie włączania protokołu TLS 1.2. |
| Windows Server 2008 | Obsługa protokołu TLS 1.2, TLS 1.1 wymaga aktualizacji. Zobacz [aktualizacji, aby dodać obsługę protokołu TLS 1.1 i TLS 1.2 w systemie Windows Server 2008 z dodatkiem SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Nieobsługiwane. |

Aby uzyskać informacje o protokole TLS/SSL, które protokoły są włączone domyślnie w każdej wersji systemu Windows, zobacz [protokołów TLS/SSL (dostawca SSP Schannel)](https://msdn.microsoft.com/library/windows/desktop/mt808159).

**Wymagania dotyczące obsługi protokołu TLS 1.2, za pomocą programu .NET Framework 3.5**

W poniższej tabeli zamieszczono aktualizacji systemu operacyjnego należy do obsługi protokołu TLS 1.2, za pomocą programu .NET Framework 3.5. Zalecane jest stosowanie wszystkie aktualizacje systemu operacyjnego.

| **OS** | **Aktualizacja minimalne wymagane do obsługi protokołu TLS 1.2, za pomocą programu .NET Framework 3.5** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [Aktualizacja zbiorcza dla systemu Windows 10 w wersji 1511 i systemu Windows Server 2016 Technical w wersji zapoznawczej 4: 10 maja 2016 r.](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 z dodatkiem R2 | [Obsługa wersji domyślne systemu TLS zawarte w .NET Framework 3.5 na Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0</br>Windows Server 2012 | [Obsługa wersji domyślne systemu TLS zawarte w .NET Framework 3.5 w systemie Windows Server 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 z dodatkiem SP1</br>Windows Server 2008 R2 SP1 | [Obsługa wersji domyślne systemu TLS zawarte w .NET Framework 3.5.1, Windows 7 z dodatkiem SP1 i Server 2008 R2 z dodatkiem SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Obsługa wersji domyślne systemu TLS zawarte w .NET Framework 2.0 z dodatkiem SP2 Windows Vista z dodatkiem SP2 i Server 2008 z dodatkiem SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Nieobsługiwane |

## <a name="azure-cloud-services"></a>Usług Azure Cloud Services

Jeśli używasz [usług Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) role sieć Web i proces roboczy hostować i uruchamiać aplikację, istnieją pewne zagadnienia, które należy wziąć pod uwagę do obsługi protokołu TLS 1.2.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>Domyślnie .NET framework 4.7 nie jest zainstalowany w systemie operacyjnym gościa platformy Azure

Najnowsza wersja, które są zainstalowane w najnowszej wersji 5 rodziny systemów operacyjnych gościa platformy Azure (system Windows Server 2016) to 4.6.2. Aby zobaczyć, które wersje programu .NET Framework są zainstalowane w każdym systemie operacyjnym gościa platformy Azure, zobacz [wersji systemu operacyjnego gościa platformy Azure i zgodności zestawów SDK](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Jeśli aplikacja jest przeznaczona na .NET Framework w wersji, która nie jest dostępna w wersji systemu operacyjnego gościa platformy Azure, musisz zainstalować je samodzielnie. Zobacz [Zainstaluj platformę .NET na ról usługi w chmurze Azure](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Instalacja framework wymaga ponownego uruchomienia, ról usługi może być również ponowne uruchomienie przed wejściem do stanu gotowości.

### <a name="azure-guest-os-registry-settings"></a>Ustawienia rejestru systemu operacyjnego gościa platformy Azure

Obraz systemu operacyjnego gościa platformy Azure, dla [usług Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) ma już `SchUseStrongCrypto` klucz rejestru jest ustawiony na wartość 1. Aby uzyskać więcej informacji, zobacz [SchUseStrongCrypto](#schusestrongcrypto).

Ustaw [SystemDefaultTlsVersions](#systemdefaulttlsversions) klucz rejestru na wartość 1. Zobacz [Konfigurowanie zabezpieczeń za pomocą rejestru Windows](#configuring-security-via-the-windows-registry).
