---
title: "Najlepsze praktyki Transport Layer Security (TLS) w środowisku .NET Framework"
description: "Opis najlepszych rozwiązań za pomocą zabezpieczeń TLS (Transport Layer) z programu .NET Framework"
ms.date: 03/15/2018
ms.prod: .net-framework
ms.topic: article
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
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64829eee5b21a44acb18cbec9b901d77d49cab90
ms.sourcegitcommit: 3eea47bff3201ae5d3395b0c7947806c2faca255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Najlepsze praktyki Transport Layer Security (TLS) w środowisku .NET Framework

Protokołu zabezpieczeń warstwy transportu (TLS) jest standardem branżowym, zaprojektowany w celu ochrony prywatności informacji przekazywane za pośrednictwem Internetu. [Protokołu TLS 1.2](https://tools.ietf.org/html/rfc5246) jest najnowszych standardów zwolnione i zawiera ulepszenia bezpieczeństwa w porównaniu z poprzednimi wersjami. Protokołu TLS 1.2 po pewnym czasie zostaną zastąpione przez [TLS 1.3](https://tools.ietf.org/html/draft-ietf-tls-tls13-22). W tym artykule przedstawiono zalecenia do zabezpieczania aplikacji .NET Framework, które używają protokołu TLS.

Aby zapewnić odporne aplikacji .NET Framework, należy TLS, wersja **nie** zostać zapisane na stałe. .NET framework aplikacje powinny używać TLS, wersja systemu operacyjnego (OS) obsługiwanych przez.

Ten dokument jest przeznaczony dla deweloperów, którzy są:

- Bezpośrednio za pomocą <xref:System.Net> interfejsów API (na przykład <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- Bezpośrednio przy użyciu usługi WCF klientów i usług przy użyciu <xref:System.ServiceModel?displayProperty=nameWithType> przestrzeni nazw.
- Przy użyciu [usługi w chmurze Azure](https://azure.microsoft.com/services/cloud-services/) role sieć Web i proces roboczy ma być hostem, a następnie uruchom aplikację. Zobacz [usługi w chmurze Azure](#azure-cloud-services) sekcji.

Zalecamy, aby użytkownik:

- Docelowy .NET Framework 4.7 lub nowszy w aplikacjach. Docelowy .NET Framework 4.7.1 lub nowszy w aplikacjach WCF.
- Nie można określić wersji protokołu TLS. Skonfiguruj swój kod, aby umożliwić podejmowanie decyzji o TLS, wersja systemu operacyjnego.
- Wykonaj inspekcji dokładnego kodu, aby sprawdzić, czy nie jest określenie wersji protokołu TLS lub SSL.

Gdy aplikacji pozwala wybrać TLS, wersja systemu operacyjnego:

- On automatycznie korzysta z protokołów nowe dodane w przyszłości, takie jak TLS 1.3.
- System operacyjny blokuje protokołów, które są odnajdywane nie do zabezpieczenia.

Sekcja [inspekcji kodu i wprowadź zmiany kodu](#audit-your-code-and-make-code-changes) obejmuje inspekcji i aktualizowanie kodu.

W tym artykule opisano sposób włączania najwyższego poziomu zabezpieczeń dostępne dla wersji programu .NET Framework, która aplikacja elementów docelowych i uruchamia. Gdy aplikacja jawnie ustawia zabezpieczeń protokołu i wersji, zdecyduje się poza innej możliwości i wyłącza funkcję .NET Framework i systemu operacyjnego zachowanie domyślne. Jeśli chcesz aplikację, aby mieć możliwość negocjowania połączenia protokołu TLS 1.2, jawne ustawienie do starszej wersji protokołu TLS uniemożliwia połączenie protokołu TLS 1.2.

Jeśli nie można uniknąć hardcoding wersja protokołu, zdecydowanie zaleca się określenie protokołu TLS 1.2. Aby uzyskać wskazówki dotyczące identyfikowanie i usuwanie zależności protokołu TLS 1.0, Pobierz [rozwiązywanie problemu TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266) oficjalny dokument.

TLS1.0 obsługuje WCF, 1.1 i 1.2 jako domyślnego w programie .NET Framework 4.7. W programie .NET Framework 4.7.1, WCF, wartością domyślną będzie systemu operacyjnego skonfigurowany wersji. Jeśli aplikacja jest jawnie skonfigurowany z `SslProtocols.None`, WCF używa domyślnego ustawienia systemu operacyjnego, podczas korzystania z NetTcp transportu.

Należy zadać pytania dotyczące tego dokumentu w problem GitHub [zabezpieczeń TLS (Transport Layer) najlepsze rozwiązania w środowisku .NET Framework](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Inspekcja kodu i wprowadź zmiany kodu

Dla aplikacji ASP.NET, należy sprawdzić `<system.web><httpRuntime targetFramework>` elementu _web.config_ można zweryfikować używasz zamierzone wersji programu .NET Framework.

Formularze systemu Windows i innych aplikacji, zobacz [porady: wersja docelowa platformy .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

Poniższe sekcje umożliwiają Sprawdź, czy nie używasz określonej wersji protokołu TLS lub SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Jeśli aplikacja jest przeznaczony dla programu .NET Framework 4.7 lub nowszej wersji

W poniższych sekcjach przedstawiono sposób weryfikowania określonej wersji protokołu TLS lub SSL nie jest używany.

### <a name="for-http-networking"></a>Do obsługi protokołu HTTP sieci

<xref:System.Net.ServicePointManager>, przy użyciu programu .NET Framework 4.7 i nowszych wersjach, domyślnie przyjmowana jest na wybieranie najlepszych zabezpieczeń protokołu i wersji systemu operacyjnego. Aby uzyskać najlepszy wybór domyślnego systemu operacyjnego, jeśli to możliwe, nie jest ustawiana wartość <xref:System.Net.ServicePointManager.SecurityProtocol> właściwości. W przeciwnym wypadku ustaw ją na <xref:System.Net.SecurityProtocolType.SystemDefault>.

W dalszej części tego artykułu nie jest ważna, jeśli program .NET Framework 4.7 lub nowszych wersji protokołu HTTP sieci.

### <a name="for-tcp-sockets-networking"></a>Protokołu TCP dla gniazda sieci

<xref:System.Net.Security.SslStream>, przy użyciu programu .NET Framework 4.7 i nowszych wersjach, domyślnie przyjmowana jest na wybieranie najlepszych zabezpieczeń protokołu i wersji systemu operacyjnego. Aby uzyskać najlepszy wybór domyślnego systemu operacyjnego, jeśli to możliwe, nie używaj przeciążeń metody <xref:System.Net.Security.SslStream> , które wymagają jawnego <xref:System.Security.Authentication.SslProtocols> parametru. W przeciwnym razie przekazania <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Zaleca się, że nie używasz <xref:System.Security.Authentication.SslProtocols.Default>; ustawienie `SslProtocols.Default` wymusza stosowanie protokołu SSL 3.0 /TLS 1.0 i zapobiec protokołu TLS 1.2.

Nie jest ustawiana wartość <xref:System.Net.ServicePointManager.SecurityProtocol> właściwości (dla protokołu HTTP sieci).

Nie używaj przeciążeń metody <xref:System.Net.Security.SslStream> , które wymagają jawnego <xref:System.Security.Authentication.SslProtocols> parametr (dla sieci gniazda TCP). Gdy Przekieruj aplikacji .NET Framework 4.7 lub nowszej wersji, będzie można następujące najlepsze rozwiązania w zakresie zalecenie.

W pozostałej części tego tematu nie jest istotne, gdy przeznaczonych dla platformy .NET Framework 4.7 lub nowszej wersji protokołu TCP dla gniazda sieci.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Usługi WCF protokołu TCP dla transportu za pomocą zabezpieczeń transportu z poświadczeniami certyfikatu

Usługi WCF używa sam stos sieciowy jako pozostała część programu .NET Framework.

Jeśli aplikacja jest przeznaczona dla 4.7.1, WCF jest skonfigurowane i umożliwiają systemu operacyjnego wybrać najlepsze protokół zabezpieczeń domyślnie, chyba że jawnie skonfigurowane:

- W pliku konfiguracyjnym aplikacji.
- **Lub**, w aplikacji w kodzie źródłowym.

Domyślnie .NET Framework 4.7 lub nowszy jest skonfigurowana do używania protokołu TLS 1.2 i zezwala na połączenia przy użyciu protokołu TLS 1.1 i TLS 1.0. Konfigurowanie usługi WCF, aby umożliwić systemu operacyjnego wybrać najlepsze protokół zabezpieczeń, konfigurując powiązania w celu użycia <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Można go ustawić na <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None` można uzyskać z <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport` można uzyskać z <xref:System.ServiceModel.NetTcpBinding.Security>.

Jeśli używasz niestandardowego powiązania:

- Konfigurowanie usługi WCF, aby umożliwić systemu operacyjnego wybrać najlepsze protokół zabezpieczeń przez ustawienie <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> do użycia <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Lub** Skonfiguruj protokół używany ze ścieżką konfiguracji `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Jeśli jesteś **nie** przy użyciu niestandardowego powiązania **i** ustawiasz wiązania WCF za pomocą konfiguracji, należy ustawić protokół używany ze ścieżką konfiguracji `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Dla usługi WCF Zabezpieczanie komunikatów za pomocą poświadczeń certyfikatu

.NET framework 4.7 i nowszych wersjach domyślnie korzysta z protokołu określone w <xref:System.Net.ServicePointManager.SecurityProtocol> właściwości. Gdy [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` ma ustawioną wartość `true`, WCF wybiera najlepsze protokołu, do protokołu TLS 1.0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Jeśli aplikacja jest przeznaczony dla wersji programu .NET Framework starszych niż 4.7

Przeprowadź inspekcję swój kod, aby sprawdzić, czy nie ustawiasz określonej wersji protokołu TLS lub SSL przy użyciu w następujących sekcjach:

### <a name="for-net-framework-46---462-and-not-wfc"></a>Dla programu .NET Framework 4.6 - 4.6.2 i nie WFC

Ustaw `DontEnableSystemDefaultTlsVersions` `AppContext` przełączyć się do `false`. Zobacz [Konfigurowanie zabezpieczeń za pośrednictwem przełączników AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>Przy użyciu platformy .NET Framework 4.6 - 4.6.2 za pomocą zabezpieczeń transportu TCP z poświadczeniami certyfikatu usług WCF

Należy zainstalować najnowsze poprawki systemu operacyjnego. Zobacz [aktualizacje zabezpieczeń](#security-updates).

WCF framework automatycznie wybierze protokołu najwyższy dostępny do protokołu TLS 1.2, chyba że jawnie skonfigurować wersji protokołu. Aby uzyskać więcej informacji, zobacz poprzednią sekcję [transportu dla TCP WCF za pomocą zabezpieczeń transportu z poświadczeniami certyfikatu](#wcf-tcp-cert).

### <a name="for-net-framework-35---451-and-not-wcf"></a>Dla programu .NET Framework 3.5 - 4.5.1 i nie WCF

Zaleca się uaktualniania do programu .NET Framework 4.7 lub nowszej wersji aplikacji. Nie można uaktualnić, należy wykonać następujące kroki. W pewnym momencie w przyszłości, aplikacja może zakończyć się niepowodzeniem do momentu uaktualnienia do programu .NET Framework 4.7 lub nowszej wersji.

Ustaw [SchUseStrongCrypto](#schusestrongcrypto) i [SystemDefaultTlsVersions](#systemdefaulttlsversions) klucze rejestru do 1. Zobacz [Konfigurowanie zabezpieczeń za pomocą rejestru systemu Windows](#configuring-security-via-the-windows-registry). .NET Framework w wersji 3.5 obsługuje `SchUseStrongCrypto` Flaga tylko, gdy jest przekazywany jawną wartość TLS.

Jeśli korzystasz z programu .NET Framework 3.5, należy zainstalować poprawkę gorących protokołu TLS 1.2, może zostać określony przez program:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Niezawodność zbiorczy HR-1605 - pomocy technicznej dla wersji domyślne systemu TLS zawarte w .NET Framework 3.5.1 w systemie Windows 7 z dodatkiem SP1 i Server 2008 R2 z dodatkiem SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Niezawodność zbiorczy HR-1605 - pomocy technicznej dla wersji domyślne systemu TLS zawarte w .NET Framework 3.5 w systemie Windows Server 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Pakiet zbiorczy niezawodności 1605 HR - pomocy technicznej dla wersji domyślne systemu TLS zawarte w .NET Framework 3.5 na Windows 8.1 i Windows Server 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | Pakiet poprawek 1605 3154521 dla programu .NET Framework 4.5.2 i 4.5.1 w systemie Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>Aby WCF za pomocą .NET Framework 3.5 - 4.5.2 za pomocą zabezpieczeń transportu TCP z poświadczeniami certyfikatu

Te wersje platformy WCF są zapisane na stałe wartości, SSL 3.0 i TLS 1.0. Nie można zmienić tych wartości. Należy zaktualizować i Przekieruj do NET Framework 4.6 lub nowszym, użyj TLS 1.1 i 1.2.

## <a name="if-your-app-targets-net-framework-35"></a>Jeśli aplikacja jest przeznaczony dla platformy .NET Framework 3.5

Jeśli musisz jawnie ustawić protokół zabezpieczeń, zamiast czekać na .NET framework lub pobrania systemu operacyjnego protokół zabezpieczeń, Dodaj `SecurityProtocolTypeExtensions` i `SslProtocolsExtension` wyliczenia w kodzie. `SecurityProtocolTypeExtensions` i `SslProtocolsExtension` zawierają wartości dla `Tls12`, `Tls11`i `SystemDefault` wartość. Zobacz [pomocy technicznej dla wersji domyślne systemu TLS uwzględnione w programie .NET Framework 3.5 na Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Konfigurowanie zabezpieczeń za pomocą AppContext zmienia (dla programu .NET Framework 4.6 lub nowszy)

[AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) parametrów opisanych w tej sekcji Jeśli aplikacja jest przeznaczona dla lub działa na .NET Framework 4.6 lub nowszy. Czy domyślnie lub zmieniając ich ustawienie jawnie przełączników należy `false` Jeśli to możliwe. Jeśli chcesz skonfigurować zabezpieczenia za pośrednictwem jednej lub obu przełączników nie Określ wartość protokołu zabezpieczeń w kodzie; Spowoduje to przesłonić przełączników.

Przełączniki mają ten sam efekt, czy podczas wykonywania protokołu HTTP sieci (<xref:System.Net.ServicePointManager>) lub sieci gniazda TCP (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Wartość `false` dla `Switch.System.Net.DontEnableSchUseStrongCrypto` powoduje, że aplikację, aby użyć silnej kryptografii. Wartość `false` dla `DontEnableSchUseStrongCrypto` używa bardziej bezpieczne protokołów sieciowych (protokołu TLS 1.2, protokół TLS 1.1 i TLS 1.0) i blokuje protokołów, które nie są bezpieczne. Aby uzyskać więcej informacji, zobacz [flagi SCH_USE_STRONG_CRYPTO](#the-schusestrongcrypto-flag). Wartość `true` wyłącza silna Kryptografia dla aplikacji.

Jeśli aplikacja jest przeznaczony dla platformy .NET Framework 4.6 lub nowszy, domyślnie ten przełącznik `false`. To domyślnymi zabezpieczeń, zaleca się. Jeśli aplikacja działa na .NET Framework 4.6, ale jest przeznaczony dla starszej wersji, przełącznik domyślnie `true`. W takim przypadku należy jawnie ustawić go `false`.

`DontEnableSchUseStrongCrypto` powinien mieć tylko wartość `true` Jeśli musisz nawiązać starszej wersji usług, które nie obsługują silnej kryptografii i nie może zostać uaktualniona.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Wartość `false` dla `Switch.System.Net.DontEnableSystemDefaultTlsVersions` powoduje, że system operacyjny wybrać protokół aplikacji. Wartość `true` powoduje, że z aplikacji przy użyciu protokołów pobrane przez program .NET Framework.

Jeśli aplikacja jest przeznaczony dla platformy .NET Framework 4.7 lub nowszej wersji, domyślnie ten przełącznik `false`. To domyślnymi zabezpieczeń, które firma Microsoft zaleca. Jeśli aplikacja działa na .NET Framework 4.7 lub nowszej wersji, ale jest przeznaczony dla starszej wersji, przełącznik domyślnie `true`. W takim przypadku należy jawnie ustawić go `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Wartość `false` dla `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` powoduje, że aplikacja Użyj wartości zdefiniowanej w `ServicePointManager.SecurityProtocols` przy użyciu certyfikatu poświadczeń zabezpieczeń wiadomości. Wartość `true` korzysta z protokołu najwyższy dostępny do TLS1.0

Dla aplikacji przeznaczonych dla platformy .NET Framework 4.7 i nowszych wersjach, wartością domyślną jest `false`. Dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.2 i wcześniej, wartością domyślną jest `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Wartość `false` dla `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` ustawia domyślną konfigurację, aby system operacyjny wybrać protokół. Wartość `true` ustawia domyślne najwyższy dostępny do TLS1.2 protokołu.

Dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 i nowszych wersjach, wartością domyślną jest `false`. Dla aplikacji przeznaczonych dla platformy .NET Framework 4,7 i wcześniejszych, wartością domyślną jest `true`.

Aby uzyskać więcej informacji na temat protokoły TLS, zobacz [ograniczenie: protokoły TLS](../migration-guide/mitigation-tls-protocols.md). Aby uzyskać więcej informacji na temat `AppContext` przełączników, zobacz [ `<AppContextSwitchOverrides> Element` ](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Konfigurowanie zabezpieczeń za pomocą rejestru systemu Windows

Jeśli ustawienie jednego lub obu `AppContext` przełączników nie jest to możliwe, można kontrolować protokołów zabezpieczeń, które Twoja aplikacja korzysta z kluczy rejestru systemu Windows, opisane w tej sekcji. Nie można użyć jednego lub obu `AppContext` zmienia, jeśli aplikacja jest przeznaczony dla .NET Framework w wersji starszej niż 4.6 lub nie można edytować pliku konfiguracji. Jeśli chcesz skonfigurować zabezpieczenia w rejestrze nie Określ wartość protokołu zabezpieczeń w kodzie; Spowoduje to przesłonić rejestru.

Nazwy kluczy rejestru są podobne do nazwy odpowiadającego `AppContext` zmienia, ale bez `DontEnable` dołączany na początku nazwy. Na przykład `AppContext` przełącznika `DontEnableSchUseStrongCrypto` nosi nazwę klucza rejestru [SchUseStrongCrypto](#schusestrongcrypto).

Klucze te są dostępne we wszystkich wersjach systemu .NET Framework, dla których jest najnowsze poprawki zabezpieczeń. Zobacz [aktualizacje zabezpieczeń](#security-updates).

Wszystkie klucze rejestru opisanych poniżej mają ten sam efekt czy robimy HTTP sieci (<xref:System.Net.ServicePointManager>) lub sieci gniazda TCP (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` Klucz rejestru ma wartość typu DWORD. Wartość 1 powoduje, że aplikację, aby użyć silnej kryptografii. Silna Kryptografia używa bardziej bezpieczne protokołów sieciowych (protokołu TLS 1.2, protokół TLS 1.1 i TLS 1.0) i blokuje protokołów, które nie są bezpieczne. Wartość 0 powoduje wyłączenie silnej kryptografii. Aby uzyskać więcej informacji, zobacz [flagi SCH_USE_STRONG_CRYPTO](#the-schusestrongcrypto-flag).

Jeśli aplikacja jest przeznaczony dla platformy .NET Framework 4.6 lub nowszy, ten klucz domyślnie wartość 1. To domyślnymi zabezpieczeń, które firma Microsoft zaleca. Jeśli aplikacja działa na .NET Framework 4.6, ale jest przeznaczony dla starszej wersji, a następnie klucza wartość domyślna to 0. W takim przypadku należy jawnie ustawić jej wartość na 1.

Ten klucz powinien mieć tylko wartość 0, jeśli chcesz nawiązać połączenie starszej wersji usług, które nie obsługują silnej kryptografii i nie można uaktualnić.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` Klucz rejestru ma wartość typu DWORD. Wartość 1 powoduje, że system operacyjny wybrać protokół aplikacji. Wartość 0 powoduje, że z aplikacji przy użyciu protokołów pobrane przez program .NET Framework.

`<VERSION>` musi być 4.0.30319 (dla programu .NET Framework 4 i nowszych) lub v2.0.50727 (programu .NET Framework 3.5).

Jeśli aplikacja jest przeznaczony dla platformy .NET Framework 4.7 lub nowszej wersji, ten klucz domyślnie wartość 1. To domyślnymi zabezpieczeń, które firma Microsoft zaleca. Jeśli aplikacja działa na .NET Framework 4.7 lub nowszej wersji, ale jest przeznaczony dla starszej wersji, klucz jest równa 0. W takim przypadku należy jawnie ustawić jej wartość na 1.

Aby uzyskać więcej informacji, zobacz [Zbiorcza aktualizacja dla systemu Windows 10 w wersji 1511 i Windows Server 2016 Technical Preview 4: 10 maja 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

Aby uzyskać więcej informacji o .NET framework 3.5.1, zobacz [pomocy technicznej dla wersji domyślne systemu TLS zawarte w .NET Framework 3.5.1 w systemie Windows 7 z dodatkiem SP1 i Server 2008 R2 z dodatkiem SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Następujące _. REG_ pliku ustawia najbardziej bezpieczne wartości kluczy rejestru i ich warianty:

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

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Konfigurowanie protokołów Schannel w rejestrze systemu Windows

Można użyć rejestru dla precyzyjną kontrolę nad protokołów, które negocjuje klienta i/lub serwera aplikacji. Sieć aplikacji przechodzi przez Schannel (czyli inną nazwę dla [bezpiecznego kanału](https://msdn.microsoft.com/library/windows/desktop/aa380123). Konfigurując `Schannel`, można skonfigurować zachowanie aplikacji.

Rozpoczynać `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` klucza rejestru. W tym kluczu wszystkie podklucze można utworzyć w zestawie `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1`, i `TLS 1.2`. W każdej z tych podkluczy, można utworzyć podkluczy `Client` i/lub `Server`. W obszarze `Client` i `Server`, tworząc wartości DWORD `DisabledByDefault` (0 lub 1) i `Enabled` (0 lub 0xFFFFFFFF).

## <a name="the-schusestrongcrypto-flag"></a>Flaga SCH_USE_STRONG_CRYPTO

Gdy jest włączona (domyślnie przez `AppContext` przełącznika, lub rejestru systemu Windows), korzysta z programu .NET Framework `SCH_USE_STRONG_CRYPTO` Flaga aplikacji żądanie protokołu zabezpieczeń TLS. `SCH_USE_STRONG_CRYPTO` Flagi można włączyć domyślnie z `AppContext` przełącznika, lub z rejestru. System operacyjny przekazuje flagi `Schannel`nakazać, aby wyłączyć znane słabe algorytmy kryptograficzne, szyfrowania mechanizmów i wersji protokołu TLS/SSL, które może być włączone w przeciwnym razie współdziałania lepiej. Aby uzyskać więcej informacji, zobacz:

- [Bezpieczny kanał](https://msdn.microsoft.com/library/windows/desktop/aa380123)
- [Struktura SCHANNEL_CRED](https://msdn.microsoft.com/library/windows/desktop/aa379810)

`SCH_USE_STRONG_CRYPTO` Flagi również jest przekazywana do `Schannel` jawnie korzystając `Tls` (TLS 1.0) `Tls11`, lub `Tls12` wartości wyliczane <xref:System.Net.SecurityProtocolType> lub <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Aktualizacje zabezpieczeń

Najlepsze rozwiązania w tym artykule są zależne od są zainstalowane najnowsze aktualizacje zabezpieczeń. Aktualizacje te obejmują możliwość używania zaawansowane 4.7 Framework .NET i funkcje. Najnowsze aktualizacje zabezpieczeń są ważne, jeśli aplikacja będzie działać w programie .NET Framework 4.7 i nowszych wersjach (nawet jeśli jego jest przeznaczony dla starszej wersji).

Aby zaktualizować system operacyjny wybrać najlepszą wersję protokołu TLS można używać .NET Framework, należy zainstalować co najmniej:

- [.NET Framework 2017 sierpnia Podgląd zestawienia jakości](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup).
- **Lub** [2017 września zabezpieczenia programu .NET Framework i jakość Rollup](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup).

Zobacz też:

- [Wersje programu .NET framework i zależności](../migration-guide/versions-and-dependencies.md)
- [Porady: Określanie, które wersje programu .NET Framework są zainstalowane](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Obsługa protokołu TLS 1.2

Dla aplikacji do negocjowania protokołu TLS 1.2, systemu operacyjnego i programu .NET Framework w wersji zarówno muszą obsługiwać protokół TLS 1.2.

**Wymagania dotyczące systemu operacyjnego do obsługi protokołu TLS 1.2**

Aby włączyć lub ponownie włączyć protokół TLS 1.2 i/lub protokołu TLS 1.1 w systemie, która je obsługuje, zobacz [zabezpieczeń TLS (Transport Layer), ustawienia rejestru](/windows-server/security/tls/tls-registry-settings).

| **OS** | **Obsługa protokołu TLS 1.2** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | Obsługiwane i domyślnie włączona. |
| Windows 8.1</br>Windows Server 2012 z dodatkiem R2 | Obsługiwane i domyślnie włączona. |
| Windows 8.0</br>Windows Server 2012 | Obsługiwane i domyślnie włączona. |
| Windows 7 z dodatkiem SP1</br>Windows Server 2008 R2 SP1 | Obsługiwane, lecz nie jest włączona domyślnie. Zobacz [zabezpieczeń TLS (Transport Layer), ustawienia rejestru](/windows-server/security/tls/tls-registry-settings) strony sieci web, aby uzyskać więcej informacji o sposobie włączania protokołu TLS 1.2. |
| Windows Server 2008 | Obsługa protokołu TLS 1.2 i protokołu TLS 1.1 wymaga aktualizacji. Zobacz [aktualizacji, aby dodać obsługę protokołu TLS 1.1 i TLS 1.2 w systemie Windows Server 2008 z dodatkiem SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Nieobsługiwane. |

Aby uzyskać informacje o protokole TLS/SSL, które protokoły są domyślnie włączone w każdej wersji systemu Windows, temacie [protokoły TLS/SSL (dostawca SSP Schannel)](https://msdn.microsoft.com/library/windows/desktop/mt808159).

**Wymagania dotyczące obsługi protokołu TLS 1.2 z programem .NET Framework 3.5**

Ta tabela zawiera aktualizację systemu operacyjnego, potrzebne do obsługi protokołu TLS 1.2 z programem .NET Framework 3.5. Zaleca się zastosowanie wszystkie aktualizacje systemu operacyjnego.

| **OS** | **Aktualizacja minimalne wymagane do obsługi protokołu TLS 1.2 z programem .NET Framework 3.5** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [Aktualizacja zbiorcza dla systemu Windows 10 w wersji 1511 i Windows Server 2016 Technical Preview 4: 10 maja 2016 r.](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 z dodatkiem R2 | [Obsługa wersji domyślne systemu TLS zawarte w .NET Framework 3.5 na Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0</br>Windows Server 2012 | [Obsługa wersji domyślne systemu TLS zawarte w .NET Framework 3.5 w systemie Windows Server 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 z dodatkiem SP1</br>Windows Server 2008 R2 SP1 | [Obsługa wersji domyślne systemu TLS uwzględnione w programie .NET Framework 3.5.1 w systemie Windows 7 z dodatkiem SP1 i Server 2008 R2 z dodatkiem SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Obsługa wersji domyślne systemu TLS zawarte w .NET Framework 2.0 z dodatkiem SP2 w systemie Windows Vista z dodatkiem SP2 i Server 2008 z dodatkiem SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Nieobsługiwane |

## <a name="azure-cloud-services"></a>Usługi w chmurze Azure

Jeśli używasz [usługi w chmurze Azure](https://azure.microsoft.com/services/cloud-services/) role sieć Web i proces roboczy ma być hostem, a następnie uruchom aplikację, istnieją pewne kwestie, które należy wziąć pod uwagę w celu obsługi protokołu TLS 1.2.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>Domyślnie program .NET framework 4.7 nie jest zainstalowany na Azure systemu operacyjnego gościa

W najnowszej wersji w najnowszym wydaniu 5 rodziny systemu operacyjnego gościa Azure (Windows Server 2016) jest 4.6.2. Aby sprawdzić, które wersje programu .NET Framework są zainstalowane na każdym systemu operacyjnego gościa Azure, zobacz [wersji systemu operacyjnego gościa Azure i zgodność pakietu SDK](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Jeśli aplikacja jest przeznaczony dla wersji programu .NET Framework, która nie jest dostępna w wersji systemu operacyjnego gościa Azure, musisz zainstalować samodzielnie. Zobacz [zainstalować program .NET na role usługi w chmurze Azure](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Instalacja framework wymaga ponownego uruchomienia komputera, ról usługi może być również ponowne uruchomienie przed wejściem w stanie gotowe.

### <a name="azure-guest-os-registry-settings"></a>Azure ustawienia rejestru systemu operacyjnego gościa

Obraz systemu operacyjnego gościa Azure dla [usługi w chmurze Azure](https://azure.microsoft.com/services/cloud-services/) ma już `SchUseStrongCrypto` klucza rejestru jest ustawiona na wartość 1. Aby uzyskać więcej informacji, zobacz [SchUseStrongCrypto](#schusestrongcrypto).

Ustaw [SystemDefaultTlsVersions](#systemdefaulttlsversions) klucza rejestru na wartość 1. Zobacz [Konfigurowanie zabezpieczeń za pomocą rejestru systemu Windows](#configuring-security-via-the-windows-registry).
