---
title: Najważniejsze wskazówki dotyczące zabezpieczeń warstwy transportu (TLS) w ramach platformy .NET Framework
description: W tym artykule opisano najlepsze rozwiązania dotyczące korzystania z programu Transport Layer Security (TLS) w ramach .NET Framework
ms.date: 10/22/2018
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
ms.openlocfilehash: 81ac469f75f925ea00c02ff94ade0e8793e7efff
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546714"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Najważniejsze wskazówki dotyczące zabezpieczeń warstwy transportu (TLS) w ramach platformy .NET Framework

Protokół TLS (Transport Layer Security) jest standardem branżowym zaprojektowanym w celu ochrony prywatności informacji przekazywanych przez Internet. [TLS 1.2](https://tools.ietf.org/html/rfc5246) to standard, który zapewnia ulepszenia zabezpieczeń w porównaniu z poprzednimi wersjami. TLS 1.2 zostanie ostatecznie zastąpiony przez najnowszy wydany standard [TLS 1.3,](https://tools.ietf.org/html/rfc8446) który jest szybszy i ma lepsze bezpieczeństwo. W tym artykule przedstawiono zalecenia dotyczące zabezpieczania aplikacji .NET Framework korzystających z protokołu TLS.

Aby upewnić się, że aplikacje .NET Framework pozostają bezpieczne, wersja TLS **nie** powinna być zakodowana na stałe. Aplikacje .NET Framework powinny używać wersji TLS, której obsługuje system operacyjny (OS).

Ten dokument jest skierowany do deweloperów, którzy są:

- Bezpośrednio przy <xref:System.Net> użyciu interfejsów API <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> (na przykład i <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- Bezpośrednio przy użyciu klientów I usług <xref:System.ServiceModel?displayProperty=nameWithType> WCF przy użyciu obszaru nazw.

Zalecamy wykonanie następujących czynności:

- Target .NET Framework 4.7 lub nowsze wersje w aplikacjach. Target .NET Framework 4.7.1 lub nowszych wersji w aplikacjach WCF.
- Nie należy określać wersji protokołu TLS. Skonfiguruj kod, aby umożliwić systemowi operacyjnemu decydowania o wersji protokołu TLS.
- Wykonaj dokładny audyt kodu, aby sprawdzić, czy nie określasz wersji TLS lub SSL.

Gdy aplikacja pozwala systemowi operacyjnemu wybrać wersję TLS:

- Automatycznie korzysta z nowych protokołów dodanych w przyszłości, takich jak TLS 1.3.
- System operacyjny blokuje protokoły, które są odnalezione jako nie są bezpieczne.

Sekcja [Inspekcja kodu i wprowadzanie zmian w kodzie](#audit-your-code-and-make-code-changes) obejmuje inspekcję i aktualizowanie kodu.

W tym artykule wyjaśniono, jak włączyć najsilniejsze zabezpieczenia dostępne dla wersji programu .NET Framework, która jest przeznaczona dla aplikacji i działa na. Gdy aplikacja jawnie ustawia protokół zabezpieczeń i wersję, rezygnuje z innych alternatyw i rezygnuje z zachowania domyślnego programu .NET Framework i systemu operacyjnego. Jeśli chcesz, aby aplikacja mogła negocjować połączenie TLS 1.2, jawne ustawienie niższej wersji protokołu TLS uniemożliwia połączenie TLS 1.2.

Jeśli nie można uniknąć hardcoding wersji protokołu, zdecydowanie zaleca się określenie protokołu TLS 1.2. Aby uzyskać wskazówki dotyczące identyfikowania i usuwania zależności TLS 1.0, pobierz oficjalny dokument [rozwiązywania problemów protokołu TLS 1.0.](https://www.microsoft.com/download/details.aspx?id=55266)

WCF obsługuje TLS1.0, 1.1 i 1.2 jako wartość domyślna w .NET Framework 4.7. Począwszy od programu .NET Framework 4.7.1, WCF domyślnie do wersji skonfigurowane przez system operacyjny. Jeśli aplikacja jest jawnie `SslProtocols.None`skonfigurowana za pomocą programu , WCF używa domyślnego ustawienia systemu operacyjnego podczas korzystania z transportu NetTcp.

Pytania dotyczące tego dokumentu można zadawać w [sieci TLS (Transport Layer Security) w usłudze .NET Framework](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Inspekcja kodu i wprowadzanie zmian w kodzie

W przypadku ASP.NET aplikacji sprawdź `<system.web><httpRuntime targetFramework>` element _web.config,_ aby sprawdzić, czy używasz zamierzonej wersji programu .NET Framework.

W przypadku formularzy systemu Windows i innych aplikacji zobacz [Jak: Kierowanie na wersję programu .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).

Poniższe sekcje umożliwiają sprawdzenie, czy nie używasz określonej wersji protokołu TLS lub SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Jeśli aplikacja jest przeznaczona dla wersji .NET Framework 4.7 lub nowszych

W poniższych sekcjach pokazano, jak sprawdzić, czy nie używasz określonej wersji protokołu TLS lub SSL.

### <a name="for-http-networking"></a>Dla sieci HTTP

<xref:System.Net.ServicePointManager>, używając platformy .NET Framework 4.7 i nowszych wersji, użyje domyślnego protokołu zabezpieczeń skonfigurowany w os. Aby uzyskać domyślny wybór systemu operacyjnego, jeśli to <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> możliwe, nie ustawiaj wartości właściwości, która domyślnie <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>ma wartość .

Ponieważ <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> ustawienie powoduje <xref:System.Net.ServicePointManager> użycie domyślnego protokołu zabezpieczeń skonfigurowany przez system operacyjny, aplikacja może działać inaczej w oparciu o system operacyjny, na który jest uruchomiony. Na przykład system Windows 7 z dodatku SP1 używa protokołu TLS 1.0, podczas gdy systemy Windows 8 i Windows 10 używają protokołu TLS 1.2.

Poniżej dalsza część artykułu Nie jest istotne, gdy kierowanie .NET Framework 4.7 lub nowszych wersji dla sieci HTTP.

### <a name="for-tcp-sockets-networking"></a>Dla sieci gniazd TCP

<xref:System.Net.Security.SslStream>, używając programu .NET Framework 4.7 i nowszych wersji, domyślnie system operacyjny wybiera najlepszy protokół zabezpieczeń i wersję. Aby uzyskać domyślny najlepszy wybór systemu operacyjnego, <xref:System.Net.Security.SslStream> jeśli to możliwe, nie <xref:System.Security.Authentication.SslProtocols> należy używać przeciążenia metody tego wziąć jawny parametr. W przeciwnym <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>razie przekaż . Zalecamy, aby nie <xref:System.Security.Authentication.SslProtocols.Default>używać ; ustawienie `SslProtocols.Default` wymusza użycie protokołu SSL 3.0 /TLS 1.0 i zapobiega TLS 1.2.

Nie ustawiaj wartości <xref:System.Net.ServicePointManager.SecurityProtocol> właściwości (dla sieci HTTP).

Nie należy używać przeciążenia <xref:System.Net.Security.SslStream> metody, które <xref:System.Security.Authentication.SslProtocols> przyjmują jawny parametr (dla sieci gniazd TCP). Podczas ponownego kierowania aplikacji do platformy .NET Framework 4.7 lub nowszych wersji, należy kierować się zaleceniami najlepszych rozwiązań.

Pozostała część tego tematu nie jest istotna w przypadku kierowania na .NET Framework 4.7 lub nowszych wersji dla sieci gniazd TCP.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>W przypadku transportu TCP WCF przy użyciu zabezpieczeń transportu z poświadczeniami certyfikatu

WCF używa tego samego stosu sieciowego, co reszta programu .NET Framework.

Jeśli kierowane są 4.7.1, WCF jest skonfigurowany tak, aby umożliwić systemowi operacyjnemu wybranie najlepszego protokołu zabezpieczeń domyślnie, chyba że zostanie jawnie skonfigurowany:

- W pliku konfiguracji aplikacji.
- **Lub**, w aplikacji w kodzie źródłowym.

Domyślnie .NET Framework 4.7 i nowsze wersje są skonfigurowane do używania protokołu TLS 1.2 i zezwalają na połączenia przy użyciu protokołu TLS 1.1 lub TLS 1.0. Skonfiguruj WCF, aby umożliwić systemowi operacyjnemu wybranie <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>najlepszego protokołu zabezpieczeń, konfigurując powiązanie do użycia . Można go ustawić <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>na . `SslProtocols.None`można uzyskać z <xref:System.ServiceModel.NetTcpSecurity.Transport>pliku . `NetTcpSecurity.Transport`można uzyskać z <xref:System.ServiceModel.NetTcpBinding.Security>pliku .

Jeśli używasz niestandardowego powiązania:

- Skonfiguruj WCF, aby umożliwić systemowi <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> operacyjnemu <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>wybranie najlepszego protokołu zabezpieczeń, ustawiając do użycia .
- **Lub** skonfiguruj protokół `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`używany ze ścieżką konfiguracji .

Jeśli **nie** używasz niestandardowego powiązania **i** ustawiasz powiązanie WCF przy użyciu konfiguracji, `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`ustaw protokół używany ze ścieżką konfiguracji .

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Dla zabezpieczenia wiadomości WCF z poświadczeniami certyfikatu

.NET Framework 4.7 i nowsze wersje domyślnie używa protokołu określonego we <xref:System.Net.ServicePointManager.SecurityProtocol> właściwości. Gdy [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` jest `true`ustawiona na , WCF wybiera najlepszy protokół, do TLS 1.0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Jeśli aplikacja jest przeznaczona dla wersji programu .NET Framework wcześniejszej niż 4.7

Inspekcja kodu, aby sprawdzić, czy nie ustawiasz określonej wersji protokołu TLS lub SSL, korzystając z następujących sekcji:

### <a name="for-net-framework-46---462-and-not-wcf"></a>Dla .NET Framework 4.6 - 4.6.2, a nie WCF

`DontEnableSystemDefaultTlsVersions` `AppContext` Ustaw przełącznik `false`na . Zobacz [Konfigurowanie zabezpieczeń za pomocą przełączników AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>Dla WCF przy użyciu .NET Framework 4.6 - 4.6.2 przy użyciu zabezpieczeń transportu TCP z poświadczeniami certyfikatu

Należy zainstalować najnowsze poprawki systemu operacyjnego. Zobacz [Aktualizacje zabezpieczeń](#security-updates).

Struktura WCF automatycznie wybiera najwyższy protokół dostępny do TLS 1.2, chyba że jawnie skonfigurować wersję protokołu. Aby uzyskać więcej informacji, zobacz poprzednią sekcję [Dla transportu TCP WCF przy użyciu zabezpieczeń transportu z poświadczeniami certyfikatu](#wcf-tcp-cert).

### <a name="for-net-framework-35---452-and-not-wcf"></a>Dla .NET Framework 3.5 - 4.5.2, a nie WCF

Firma Microsoft zaleca uaktualnienie aplikacji do wersji .NET Framework 4.7 lub nowszych. Jeśli nie można uaktualnić, należy wykonać następujące kroki. W pewnym momencie w przyszłości aplikacja może zakończyć się niepowodzeniem, dopóki uaktualnienie do wersji .NET Framework 4.7 lub nowszych.

Ustaw klucze rejestru [SchUseStrongCrypto](#schusestrongcrypto) i [SystemDefaultTlsVersions](#systemdefaulttlsversions) na 1. Zobacz [Konfigurowanie zabezpieczeń za pośrednictwem rejestru systemu Windows](#configuring-security-via-the-windows-registry). .NET Framework w wersji 3.5 obsługuje flagę `SchUseStrongCrypto` tylko wtedy, gdy jest przekazywana jawna wartość TLS.

Jeśli korzystasz z programu .NET Framework 3.5, musisz zainstalować gorącą poprawkę, aby program mógł określić tls 1.2:

| [aktualizacja kb3154518](https://support.microsoft.com/kb/3154518) | Zbiorczość niezawodności HR-1605 — obsługa domyślnych wersji systemu TLS zawartych w programie .NET Framework 3.5.1 w systemie Windows 7 z dodatku SP1 i server 2008 R2 z dodatku SP1 |
| --- | --- |
| [aktualizacja kb3154519](https://support.microsoft.com/kb/3154519) | Zbiorczość niezawodności HR-1605 — obsługa domyślnych wersji systemu TLS zawartych w programie .NET Framework 3.5 w systemie Windows Server 2012 |
| [aktualizacja KB3154520](https://support.microsoft.com/kb/3154520) | Zbiorczość niezawodności HR-1605 — obsługa domyślnych wersji systemu TLS zawartych w programie .NET Framework 3.5 w systemach Windows 8.1 i Windows Server 2012 R2 |
| [aktualizacja KB3156421](https://support.microsoft.com/kb/3156421) | 1605 Hotfix rollup 3154521 dla programu .NET Framework 4.5.2 i 4.5.1 w systemie Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>Dla WCF przy użyciu .NET Framework 3.5 - 4.5.2 przy użyciu zabezpieczeń transportu TCP z poświadczeniami certyfikatu

Te wersje WCF framework są hardcoded do używania wartości SSL 3.0 i TLS 1.0. Tych wartości nie można zmienić. Aby używać protokołu TLS 1.1 i 1.2, należy zaktualizować i ponownie kierować je do wersji programu NET Framework 4.6 lub nowszych.

## <a name="if-your-app-targets-net-framework-35"></a>Jeśli aplikacja jest przeznaczona dla programu .NET Framework 3.5

Jeśli należy jawnie ustawić protokół zabezpieczeń zamiast zezwalać .NET lub systemowi `SecurityProtocolTypeExtensions` `SslProtocolsExtension` operacyjnemu na wybranie protokołu zabezpieczeń, dodaj i wyliczasz do kodu. `SecurityProtocolTypeExtensions`i `SslProtocolsExtension` uwzględnić `Tls12` `Tls11`wartości dla `SystemDefault` , i wartość. Aby uzyskać więcej informacji, zobacz [Obsługa domyślnych wersji systemu TLS zawartych w programie .NET Framework 3.5 w systemach Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Konfigurowanie zabezpieczeń za pomocą przełączników AppContext (dla wersji .NET Framework 4.6 lub nowszych)

[Przełączniki AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) opisane w tej sekcji są istotne, jeśli cele aplikacji lub działa na.NET Framework 4.6 lub nowszych wersjach. Czy domyślnie lub przez ustawienie ich jawnie, `false` przełączniki powinny być, jeśli to możliwe. Jeśli chcesz skonfigurować zabezpieczenia za pomocą jednego lub obu przełączników, nie określaj wartości protokołu zabezpieczeń w kodzie; w ten sposób zastąpiłoby przełącznik(y).

Przełączniki mają taki sam efekt, niezależnie od<xref:System.Net.ServicePointManager>tego, czy korzystasz z<xref:System.Net.Security.SslStream>sieci http ( ) lub TCP sockets networks ( ).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Wartość `false` dla `Switch.System.Net.DontEnableSchUseStrongCrypto` powoduje, że aplikacja do korzystania z silnej kryptografii. Wartość `false` dla `DontEnableSchUseStrongCrypto` używa bezpieczniejszych protokołów sieciowych (TLS 1.2, TLS 1.1 i TLS 1.0) i blokuje protokoły, które nie są bezpieczne. Aby uzyskać więcej informacji, zobacz [Flaga SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag). Wartość wyłącza silną `true` kryptografię aplikacji.

Jeśli aplikacja jest przeznaczona dla wersji .NET Framework 4.6 lub nowszych, ten przełącznik jest domyślnie włączony do `false`. To bezpieczne ustawienie domyślne, które zalecamy. Jeśli aplikacja działa w programie .NET Framework 4.6, ale jest `true`przeznaczona dla starszej wersji, przełącznik domyślnie na . W takim przypadku należy wyraźnie ustawić `false`go na .

`DontEnableSchUseStrongCrypto`powinien mieć wartość `true` tylko wtedy, gdy trzeba połączyć się ze starszymi usługami, które nie obsługują silnej kryptografii i nie mogą być uaktualniane.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Wartość `false` for `Switch.System.Net.DontEnableSystemDefaultTlsVersions` powoduje, że aplikacja, aby umożliwić systemowi operacyjnemu, aby wybrać protokół. Wartość `true` powoduje, że aplikacja do korzystania z protokołów wybranych przez .NET Framework.

Jeśli aplikacja jest przeznaczona dla wersji .NET Framework 4.7 lub nowszych, ten przełącznik jest domyślnie włączony do `false`. To bezpieczne ustawienie domyślne, które zalecamy. Jeśli aplikacja działa w wersji .NET Framework 4.7 lub nowszej, `true`ale jest przeznaczona dla starszej wersji, przełącznik domyślnie ma wartość . W takim przypadku należy wyraźnie ustawić `false`go na .

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUżywanieServicePointManagerSecurityProtocols

Wartość `false` for `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` powoduje, że aplikacja do `ServicePointManager.SecurityProtocols` używania wartości zdefiniowanej w zabezpieczeniach wiadomości przy użyciu poświadczeń certyfikatu. Wartość użycia `true` najwyższego dostępnego protokołu, do TLS1.0

W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.7 i nowszych wersjach wartość domyślnie ma wartość `false`. W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.6.2 i wcześniejszych wartość jest domyślna `true`na .

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Wartość `false` dla `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` ustawia domyślną konfigurację, aby umożliwić systemowi operacyjnemu wybranie protokołu. Wartość `true` ustawia domyślny do najwyższego dostępnego protokołu, do TLS1.2.

W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 i nowszych wersji wartość ta jest domyślna `false`na . W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.7 lub wcześniejszych wartość domyślnie oznacza `true`.

Aby uzyskać więcej informacji na temat protokołów TLS, zobacz [Łagodzenie: Protokoły TLS](../migration-guide/mitigation-tls-protocols.md). Aby uzyskać `AppContext` więcej informacji [`<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)na temat przełączników, zobacz .

## <a name="configuring-security-via-the-windows-registry"></a>Konfigurowanie zabezpieczeń za pośrednictwem rejestru systemu Windows

> [!WARNING]
> Ustawienie kluczy rejestru ma wpływ na wszystkie aplikacje w systemie. Tej opcji należy używać tylko wtedy, gdy użytkownik ma pełną kontrolę nad urządzeniem i może kontrolować zmiany w rejestrze.

Jeśli ustawienie jednego `AppContext` lub obu przełączników nie jest opcją, można sterować protokołami zabezpieczeń używanymi przez aplikację za pomocą kluczy rejestru systemu Windows opisanych w tej sekcji. Nie można użyć jednego lub obu `AppContext` przełączników, jeśli aplikacja jest uruchamiana w programie .NET Framework 4.5.2 lub wcześniejszych wersjach lub jeśli nie można edytować pliku konfiguracyjnego. Jeśli chcesz skonfigurować zabezpieczenia w rejestrze, nie określaj wartości protokołu zabezpieczeń w kodzie; zastępuje to ustawienie rejestru.

Nazwy kluczy rejestru są podobne do nazw `AppContext` odpowiednich przełączników, ale bez poprzedzania `DontEnable` nazwy. Na przykład `AppContext` przełącznik `DontEnableSchUseStrongCrypto` jest kluczem rejestru o nazwie [SchUseStrongCrypto](#schusestrongcrypto).

Te klucze są dostępne we wszystkich wersjach programu .NET Framework, dla których istnieje najnowsza poprawka zabezpieczeń. Zobacz [Aktualizacje zabezpieczeń](#security-updates).

Wszystkie klucze rejestru opisane poniżej mają ten sam efekt,<xref:System.Net.ServicePointManager>niezależnie od tego, czy<xref:System.Net.Security.SslStream>korzystasz z sieci HTTP ( ) lub TCP sockets networks ( ).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto ( SchUseStrongCrypto )

Klucz `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` rejestru ma wartość typu DWORD. Wartość 1 powoduje, że aplikacja do korzystania z silnej kryptografii. Silna kryptografia używa bezpieczniejszych protokołów sieciowych (TLS 1.2, TLS 1.1 i TLS 1.0) i blokuje protokoły, które nie są bezpieczne. Wartość 0 wyłącza silną kryptografię. Aby uzyskać więcej informacji, zobacz [Flaga SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag).

Jeśli aplikacja jest przeznaczona dla wersji .NET Framework 4.6 lub nowszych, ten klucz domyślnie ma wartość 1. To bezpieczne ustawienie domyślne, które zalecamy. Jeśli aplikacja jest przeznaczona dla platformy .NET Framework 4.5.2 lub wcześniejszych wersji, klucz domyślnie 0. W takim przypadku należy jawnie ustawić jego wartość na 1.

Ten klucz powinien mieć wartość 0 tylko wtedy, gdy musisz połączyć się ze starszymi usługami, które nie obsługują silnej kryptografii i nie można uaktualnić.

### <a name="systemdefaulttlsversions"></a>Wersje systemdefaulttls

Klucz `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` rejestru ma wartość typu DWORD. Wartość 1 powoduje, że aplikacja zezwala systemowi operacyjnemu na wybranie protokołu. Wartość 0 powoduje, że aplikacja do korzystania z protokołów wybranych przez .NET Framework.

`<VERSION>`musi być w wersji 4.0.30319 (dla .NET Framework 4 i powyżej) lub v2.0.50727 (dla .NET Framework 3.5).

Jeśli aplikacja jest przeznaczona dla wersji .NET Framework 4.7 lub nowszych, ten klucz domyślnie ma wartość 1. To bezpieczne ustawienie domyślne, które zalecamy. Jeśli aplikacja jest przeznaczona dla platformy .NET Framework 4.6.1 lub wcześniejszych wersji, klucz domyślnie 0. W takim przypadku należy jawnie ustawić jego wartość na 1.

Aby uzyskać więcej informacji, zobacz [Zbiorcza aktualizacja dla systemu Windows 10 w wersji 1511 i Windows Server 2016 Technical Preview 4: 10 maja 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016)r. .

Aby uzyskać więcej informacji o programie .NET Framework 3.5.1, zobacz [Obsługa domyślnych wersji systemu TLS zawartych w programie .NET Framework 3.5.1 w systemie Windows 7 z dodatku SP1 i server 2008 R2 z dodatku SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Poniżej dalsza jest. _ _Plik REG ustawia klucze rejestru i ich warianty na najbardziej bezpieczne wartości:

```text
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

Rejestru można używać do precyzyjnej kontroli nad protokołami negocjowanym przez klienta i/lub aplikację serwera. Sieć aplikacji przechodzi przez Schannel (która jest inną nazwą [bezpiecznego kanału](/windows/desktop/SecAuthN/secure-channel). Konfigurując `Schannel`program , można skonfigurować zachowanie aplikacji.

Zacznij od `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` klucza rejestru. Pod tym klawiszem można utworzyć dowolne `SSL 3.0` `TLS 1.0`podklu skróty w zestawie `TLS 1.1` `SSL 2.0`, , , i `TLS 1.2`. W przypadku każdego z tych podkluczów można utworzyć podklu skróty `Client` i/lub `Server`plik . W `Client` `Server`obszarze i , można `DisabledByDefault` utworzyć wartości DWORD `Enabled` (0 lub 1) i (0 lub 0xFFFFFFFFFF).

## <a name="the-sch_use_strong_crypto-flag"></a><a name="the-sch_use_strong_crypto-flag"></a>Flaga SCH_USE_STRONG_CRYPTO

Gdy jest włączona (domyślnie przez `AppContext` przełącznik lub przez rejestr systemu Windows), program `SCH_USE_STRONG_CRYPTO` .NET Framework używa flagi, gdy aplikacja żąda protokołu zabezpieczeń TLS. Flagę `SCH_USE_STRONG_CRYPTO` można włączyć domyślnie, `AppContext` za pomocą przełącznika lub rejestru. System operacyjny przekazuje flagę, aby poinstruować `Schannel`ją, aby wyłączyła znane słabe algorytmy kryptograficzne, mechanizmy szyfrowania i wersje protokołów TLS/SSL, które w przeciwnym razie mogą być włączone w celu lepszej współdziałania. Aby uzyskać więcej informacji, zobacz:

- [Bezpieczny kanał](/windows/desktop/SecAuthN/secure-channel)
- [Struktura SCHANNEL_CRED](/windows/win32/api/schannel/ns-schannel-schannel_cred)

Flaga `SCH_USE_STRONG_CRYPTO` jest również `Schannel` przekazywana do `Tls` gdy jawnie używasz `Tls11`(TLS 1.0), `Tls12` lub wyliczonych wartości <xref:System.Net.SecurityProtocolType> lub <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Aktualizacje zabezpieczeń

Najważniejsze rozwiązania tego artykułu zależą od instalowanych ostatnich aktualizacji zabezpieczeń. Te aktualizacje obejmują możliwość korzystania z zaawansowanych funkcji .NET Framework 4.7 i nowszych. Najnowsze aktualizacje zabezpieczeń są ważne, jeśli aplikacja działa w programie .NET Framework 4.7 i nowszych wersjach (nawet jeśli jest przeznaczona dla starszej wersji).

Aby zaktualizować program .NET Framework, aby umożliwić systemowi operacyjnemu wybranie najlepszej wersji protokołu TLS do użycia, należy zainstalować co najmniej:

- .NET [Framework sierpień 2017 Podgląd zestawienia jakości](https://devblogs.microsoft.com/dotnet/net-framework-august-2017-preview-of-quality-rollup/).
- **Lub** [.NET Framework wrzesień 2017 Security and Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-september-2017-security-and-quality-rollup/).

Zobacz też:

- [Wersje i zależności platformy .NET Framework](../migration-guide/versions-and-dependencies.md)
- [Jak: Określ, które wersje programu .NET Framework są zainstalowane](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Obsługa protokołu TLS 1.2

Aby aplikacja negocjowała TLS 1.2, system operacyjny i wersja programu .NET Framework muszą obsługiwać tls 1.2.

**Wymagania dotyczące systemu operacyjnego dla obsługi protokołu TLS 1.2**

Aby włączyć lub ponownie włączyć protokół TLS 1.2 i/lub TLS 1.1 w systemie, który je obsługuje, zobacz [Ustawienia rejestru TLS (Transport Layer Security).](/windows-server/security/tls/tls-registry-settings)

| **System operacyjny** | **Obsługa protokołu TLS 1.2** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | Obsługiwane i domyślnie włączone. |
| Windows 8.1<br>Windows Server 2012 R2 | Obsługiwane i domyślnie włączone. |
| Windows 8.0<br>Windows Server 2012 | Obsługiwane i domyślnie włączone. |
| Windows 7 z dodatkiem SP1<br>Windows Server 2008 R2 SP1 | Obsługiwane, ale domyślnie nie włączone. Szczegółowe informacje na temat włączania protokołu TLS 1.2 można znaleźć na stronie [internetowej ustawień rejestru zabezpieczeń warstwy transportu (TLS).](/windows-server/security/tls/tls-registry-settings) |
| Windows Server 2008 | Obsługa protokołu TLS 1.2 i TLS 1.1 wymaga aktualizacji. Zobacz [Aktualizacja, aby dodać obsługę protokołu TLS 1.1 i TLS 1.2 w systemie Windows Server 2008 SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Bez pomocy technicznej. |

Aby uzyskać informacje o tym, które protokoły TLS/SSL są domyślnie włączone w każdej wersji systemu Windows, zobacz [Protokoły w protokołach TLS/SSL (Schannel SSP).](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-)

**Wymagania dotyczące obsługi protokołu TLS 1.2 przy użyciu platformy .NET Framework 3.5**

W tej tabeli przedstawiono aktualizację systemu operacyjnego, której potrzebujesz do obsługi protokołu TLS 1.2 z programem .NET Framework 3.5. Zalecamy zastosowanie wszystkich aktualizacji systemu operacyjnego.

| **System operacyjny** | **Minimalna aktualizacja wymagana do obsługi protokołu TLS 1.2 z platformą .NET Framework 3.5** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | [Aktualizacja zbiorcza dla systemów Windows 10 w wersji 1511 i Windows Server 2016 Technical Preview 4: 10 maja 2016 r.](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1<br>Windows Server 2012 R2 | [Obsługa domyślnych wersji systemu TLS zawartych w programie .NET Framework 3.5 w systemach Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0<br>Windows Server 2012 | [Obsługa domyślnych wersji systemu TLS zawartych w programie .NET Framework 3.5 w systemie Windows Server 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 z dodatkiem SP1<br>Windows Server 2008 R2 SP1 | [Obsługa domyślnych wersji systemu TLS zawartych w programie .NET Framework 3.5.1 w systemie Windows 7 z dodatku SP1 i server 2008 R2 z dodatku SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Obsługa domyślnych wersji systemu TLS zawartych w dodatku SP2 programu .NET Framework 2.0 w systemie Windows Vista z dodatkami SP2 i server 2008 z dodatku SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Nieobsługiwane |
