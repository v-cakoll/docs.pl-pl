---
title: Transport Layer Security (TLS) — najlepsze rozwiązania dotyczące .NET Framework
description: Opisuje najlepsze rozwiązania przy użyciu Transport Layer Security (TLS) z .NET Framework
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
ms.openlocfilehash: e2f8f1304de587e1bedd8cde60e665971d903183
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937697"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>Transport Layer Security (TLS) — najlepsze rozwiązania dotyczące .NET Framework

Protokół Transport Layer Security (TLS) jest standardem branżowym, który umożliwia ochronę prywatności informacji przekazywanych przez Internet. [TLS 1,2](https://tools.ietf.org/html/rfc5246) to standard, który zapewnia lepsze zabezpieczenia w porównaniu z poprzednimi wersjami. Protokół TLS 1,2 zostanie ostatecznie zastąpiony przez najnowszy opublikowany standard [TLS 1,3](https://tools.ietf.org/html/rfc8446) , który jest szybszy i ma ulepszone zabezpieczenia. W tym artykule przedstawiono zalecenia dotyczące zabezpieczania .NET Framework aplikacji korzystających z protokołu TLS.

Aby zapewnić, że aplikacje .NET Framework pozostają bezpieczne, wersja protokołu TLS **nie** powinna być stałe. Aplikacje .NET Framework powinny używać wersji protokołu TLS obsługiwanej przez system operacyjny (OS).

Ten dokument jest przeznaczony dla deweloperów, którzy są:

- Bezpośrednio przy użyciu <xref:System.Net> interfejsów API (na przykład <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- Bezpośrednio przy użyciu klientów i usług WCF przy użyciu przestrzeni nazw <xref:System.ServiceModel?displayProperty=nameWithType>.
- Używanie ról sieci Web i procesu roboczego [platformy Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) do hostowania i uruchamiania aplikacji. Zapoznaj się z sekcją [Cloud Services platformy Azure](#azure-cloud-services) .

Zalecamy wykonanie następujących czynności:

- Docelowa wersja .NET Framework 4,7 lub nowsza w aplikacjach. Docelowa .NET Framework 4.7.1 lub nowsza wersja w aplikacjach WCF.
- Nie określaj wersji protokołu TLS. Skonfiguruj kod, aby umożliwić systemowi operacyjnemu podjęcie decyzji dotyczącej wersji protokołu TLS.
- Wykonaj gruntowną inspekcję kodu, aby sprawdzić, czy nie określono wersji protokołu TLS lub SSL.

Gdy aplikacja umożliwia systemowi operacyjnemu wybór wersji protokołu TLS:

- Automatycznie wykorzystuje nowe protokoły dodane w przyszłości, takie jak TLS 1,3.
- System operacyjny blokuje protokoły, które nie są bezpieczne.

Sekcja [inspekcji kodu i wprowadzania zmian w kodzie](#audit-your-code-and-make-code-changes) obejmuje inspekcję i aktualizowanie kodu.

W tym artykule wyjaśniono, jak włączyć najwyższe zabezpieczenia dostępne dla wersji .NET Framework, w której aplikacja jest przeznaczona do działania. Gdy aplikacja jawnie ustawia protokół zabezpieczeń i wersję, nie jest ona zależna od żadnej innej alternatywy i powoduje, że .NET Framework i domyślne zachowanie systemu operacyjnego. Jeśli chcesz, aby aplikacja mogła negocjować połączenie TLS 1,2, jawnie ustawienie niższej wersji protokołu TLS uniemożliwia połączenie TLS 1,2.

Jeśli nie możesz uniknąć zakodowana wersji protokołu, zdecydowanie zalecamy określenie protokołu TLS 1,2. Aby uzyskać wskazówki dotyczące identyfikowania i usuwania zależności TLS 1,0, Pobierz oficjalny dokument [dotyczący problemu z protokołem tls 1,0](https://www.microsoft.com/download/details.aspx?id=55266) .

Program WCF obsługuje protokoły TLS 1.0, 1,1 i 1,2 jako domyślne w .NET Framework 4,7. Począwszy od .NET Framework 4.7.1, program WCF domyślnie używa skonfigurowanej wersji systemu operacyjnego. Jeśli aplikacja jest jawnie skonfigurowana przy użyciu `SslProtocols.None`, WCF używa domyślnego ustawienia systemu operacyjnego w przypadku korzystania z transportu NetTcp.

Pytania dotyczące tego dokumentu można zadawać w [Transport Layer Security z najlepszymi rozwiązaniami](https://github.com/dotnet/docs/issues/4675)związanymi z PROTOKOŁem TLS, .NET Framework.

## <a name="audit-your-code-and-make-code-changes"></a>Inspekcja kodu i wprowadzanie zmian w kodzie

W przypadku aplikacji ASP.NET Sprawdź `<system.web><httpRuntime targetFramework>` elementu _Web. config_ , aby sprawdzić, czy korzystasz z zamierzonej wersji .NET Framework.

Aby uzyskać Windows Forms i inne aplikacje, zobacz [How to: Target a Version of the .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).

Skorzystaj z poniższych sekcji, aby sprawdzić, czy nie używasz określonej wersji protokołu TLS lub SSL.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Jeśli aplikacja jest przeznaczona dla .NET Framework 4,7 lub nowszych wersji

W poniższych sekcjach pokazano, jak sprawdzić, czy nie jest używana określona wersja protokołu TLS lub SSL.

### <a name="for-http-networking"></a>Dla sieci HTTP

<xref:System.Net.ServicePointManager>przy użyciu .NET Framework 4,7 i nowszych wersji program użyje domyślnego protokołu zabezpieczeń skonfigurowanego w systemie operacyjnym. Aby wybrać domyślny wybór systemu operacyjnego, jeśli to możliwe, nie ustawiaj wartości właściwości <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>, która jest domyślnie <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>.

Ponieważ ustawienie <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> powoduje, że <xref:System.Net.ServicePointManager> użyć domyślnego protokołu zabezpieczeń skonfigurowanego przez system operacyjny, aplikacja może działać inaczej w zależności od systemu operacyjnego, w którym jest uruchamiany. Na przykład system Windows 7 z dodatkiem SP1 korzysta z protokołu TLS 1,0, podczas gdy system Windows 8 i system Windows 10 używają protokołu TLS 1,2.

Pozostała część tego artykułu nie ma znaczenia w przypadku .NET Framework 4,7 lub nowszych wersji dla sieci HTTP.

### <a name="for-tcp-sockets-networking"></a>Dla sieci TCP Sockets

<xref:System.Net.Security.SslStream>, przy użyciu .NET Framework 4,7 i nowszych wersji, domyślnie jest wybierany system operacyjny z najlepszym protokołem zabezpieczeń i wersją. Aby uzyskać domyślny najlepszy wybór systemu operacyjnego, jeśli jest to możliwe, nie używaj przeciążeń metody <xref:System.Net.Security.SslStream>, które pobierają jawny <xref:System.Security.Authentication.SslProtocols> parametr. W przeciwnym razie Przekaż <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Zalecamy, aby nie używać <xref:System.Security.Authentication.SslProtocols.Default>; ustawienie `SslProtocols.Default` wymusza użycie protokołu SSL 3,0/TLS 1,0 i zapobiega 1,2 protokołu TLS.

Nie ustawiaj wartości właściwości <xref:System.Net.ServicePointManager.SecurityProtocol> (dla sieci HTTP).

Nie używaj przeciążeń metody <xref:System.Net.Security.SslStream>, które pobierają jawny parametr <xref:System.Security.Authentication.SslProtocols> (dla sieci TCP Sockets). Po przekierowaniu aplikacji do wersji .NET Framework 4,7 lub nowszej należy wykonać zalecenie dotyczące najlepszych rozwiązań.

Pozostała część tego tematu nie ma znaczenia w przypadku .NET Framework 4,7 lub nowszych wersji dla sieci TCP Sockets.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>W przypadku transportu TCP WCF przy użyciu zabezpieczeń transportu z poświadczeniami certyfikatów

Funkcja WCF używa tego samego stosu sieciowego co reszta .NET Framework.

Jeśli celem jest 4.7.1, platforma WCF jest skonfigurowana tak, aby system operacyjny domyślnie wybierał najlepszy protokół zabezpieczeń, chyba że jest on jawnie skonfigurowany:

- W pliku konfiguracyjnym aplikacji.
- **Lub**, w aplikacji w kodzie źródłowym.

Domyślnie .NET Framework 4,7 i nowsze wersje są skonfigurowane do korzystania z protokołu TLS 1,2 i umożliwiają nawiązywanie połączeń przy użyciu protokołu TLS 1,1 lub TLS 1,0. Skonfiguruj funkcję WCF, aby umożliwić systemowi operacyjnemu wybranie najlepszego protokołu zabezpieczeń przez skonfigurowanie powiązania do używania <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Tę wartość można ustawić na <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. dostęp do `SslProtocols.None` można uzyskać z <xref:System.ServiceModel.NetTcpSecurity.Transport>. dostęp do `NetTcpSecurity.Transport` można uzyskać z <xref:System.ServiceModel.NetTcpBinding.Security>.

Jeśli używasz niestandardowego powiązania:

- Skonfiguruj program WCF, aby umożliwić systemowi operacyjnemu wybranie najlepszego protokołu zabezpieczeń przez ustawienie <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> do użycia <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Lub** Skonfiguruj protokół używany z ścieżką konfiguracyjną `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Jeśli **nie** używasz niestandardowego powiązania **i** ustawisz powiązanie WCF przy użyciu konfiguracji, ustaw protokół używany z ścieżką konfiguracyjną `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>W przypadku zabezpieczeń komunikatów WCF przy użyciu poświadczeń certyfikatu

.NET Framework 4,7 i nowsze wersje domyślnie korzystają z protokołu określonego we właściwości <xref:System.Net.ServicePointManager.SecurityProtocol>. Gdy `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) jest ustawiony na `true`, WCF wybiera najlepszy protokół, do TLS 1,0.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Jeśli aplikacja jest przeznaczona dla .NET Framework wersji wcześniejszej niż 4,7

Przeprowadź inspekcję kodu, aby upewnić się, że nie skonfigurowano określonej wersji protokołu TLS lub SSL, korzystając z następujących sekcji:

### <a name="for-net-framework-46---462-and-not-wcf"></a>Dla .NET Framework 4,6 — 4.6.2, a nie WCF

Ustaw `DontEnableSystemDefaultTlsVersions` `AppContext` Przełącz, aby `false`. Zobacz [Konfigurowanie zabezpieczeń za pomocą przełączników AppContext](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>W przypadku WCF przy użyciu .NET Framework 4,6 4.6.2 przy użyciu zabezpieczeń transportu TCP z poświadczeniami certyfikatów

Należy zainstalować najnowsze poprawki systemu operacyjnego. Zobacz [aktualizacje zabezpieczeń](#security-updates).

Platforma WCF automatycznie wybiera najwyższy dostęp do protokołu TLS 1,2, chyba że jawnie skonfigurujesz wersję protokołu. Aby uzyskać więcej informacji, zobacz poprzednią sekcję [dotyczącą transportu TCP WCF przy użyciu zabezpieczeń transportu z poświadczeniami certyfikatów](#wcf-tcp-cert).

### <a name="for-net-framework-35---452-and-not-wcf"></a>Dla .NET Framework 3,5-4.5.2 i nie WCF

Zalecamy uaktualnienie aplikacji .NET Framework do wersji 4,7 lub nowszej. Jeśli nie możesz przeprowadzić uaktualnienia, wykonaj następujące czynności. W pewnym momencie w przyszłości aplikacja może się nie powieść, dopóki nie zostanie uaktualniona .NET Framework do wersji 4,7 lub nowszej.

Ustaw klucze rejestru [schusestrongcrypto we](#schusestrongcrypto) i [SystemDefaultTlsVersions](#systemdefaulttlsversions) na 1. Zobacz [Konfigurowanie zabezpieczeń za pośrednictwem rejestru systemu Windows](#configuring-security-via-the-windows-registry). .NET Framework w wersji 3,5 obsługuje flagę `SchUseStrongCrypto` tylko wtedy, gdy jest przenoszona jawna wartość TLS.

W przypadku korzystania z programu na .NET Framework 3,5 należy zainstalować gorącą poprawkę, aby protokół TLS 1,2 można było określić w programie:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Zestawienie niezawodności HR-1605 — obsługa domyślnych wersji systemu TLS uwzględnionych w .NET Framework 3.5.1 w systemach Windows 7 z dodatkiem SP1 i Server 2008 R2 z dodatkiem SP1 |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Zestawienie niezawodności HR-1605 — obsługa domyślnych wersji systemu TLS uwzględnionych w .NET Framework 3,5 w systemie Windows Server 2012 |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Zestawienie niezawodności HR-1605 — obsługa domyślnych wersji systemu TLS uwzględnionych w .NET Framework 3,5 w systemach Windows 8.1 i Windows Server 2012 R2 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | 1605 pakiet zbiorczy poprawek 3154521 dla .NET Framework 4.5.2 i 4.5.1 w systemie Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>W przypadku WCF przy użyciu .NET Framework 3,5-4.5.2 przy użyciu zabezpieczeń transportu TCP z poświadczeniami certyfikatów

Te wersje struktury WCF są stałe do używania wartości SSL 3,0 i TLS 1,0. Tych wartości nie można zmienić. Aby korzystać z protokołu TLS 1,1 i 1,2, należy zaktualizować i przekierować do wersji .NET Framework 4,6 lub nowszej.

## <a name="if-your-app-targets-net-framework-35"></a>Jeśli aplikacja jest przeznaczona .NET Framework 3,5

Jeśli musisz jawnie ustawić protokół zabezpieczeń zamiast zezwalać programowi .NET Framework lub systemowi operacyjnemu wybrać protokół zabezpieczeń, Dodaj `SecurityProtocolTypeExtensions` i `SslProtocolsExtension` wyliczenia do kodu. `SecurityProtocolTypeExtensions` i `SslProtocolsExtension` zawierają wartości `Tls12`, `Tls11`i `SystemDefault` wartości. Zobacz [obsługę domyślnych wersji systemu TLS uwzględnionych w .NET Framework 3,5 w systemach Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Konfigurowanie zabezpieczeń za pomocą przełączników AppContext (dla .NET Framework 4,6 lub nowszych)

Przełączniki [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) opisane w tej sekcji są istotne w przypadku, gdy aplikacja jest docelowa lub działa w .NET Framework 4,6 lub nowszych. Niezależnie od tego, czy są one domyślnie, czy przez ustawienie jawnie, przełączniki powinny być `false`, jeśli jest to możliwe. Jeśli chcesz skonfigurować zabezpieczenia za pomocą jednego lub obu przełączników, nie określaj wartości protokołu zabezpieczeń w kodzie; wykonanie tej operacji spowodowałoby przesłonięcie przełączników.

Przełączniki mają ten sam efekt, niezależnie od tego, czy są używane sieci HTTP (<xref:System.Net.ServicePointManager>) czy sieci TCP Sockets (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Wartość `false` dla `Switch.System.Net.DontEnableSchUseStrongCrypto` powoduje, że aplikacja korzysta z mocnej kryptografii. Wartość `false` dla `DontEnableSchUseStrongCrypto` używa bezpieczniejszych protokołów sieciowych (TLS 1,2, TLS 1,1 i TLS 1,0) i blokuje protokoły, które nie są bezpieczne. Aby uzyskać więcej informacji, zobacz [flagę SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag). Wartość `true` powoduje wyłączenie mocnej kryptografii dla aplikacji.

Jeśli aplikacja jest przeznaczona dla .NET Framework 4,6 lub nowszej wersji, ten przełącznik jest domyślnie `false`. Jest to bezpieczne ustawienie domyślne, które zalecamy. Jeśli aplikacja działa na .NET Framework 4,6, ale jest przeznaczona dla starszej wersji, przełącznik domyślnie zostanie `true`. W takim przypadku należy jawnie ustawić ją na `false`.

`DontEnableSchUseStrongCrypto` powinna mieć wartość `true`, jeśli konieczne jest połączenie ze starszymi usługami, które nie obsługują silnej kryptografii i nie można ich uaktualnić.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Wartość `false` dla `Switch.System.Net.DontEnableSystemDefaultTlsVersions` powoduje, że aplikacja zezwala na wybór protokołu przez system operacyjny. Wartość `true` powoduje, że aplikacja korzysta z protokołów pobranych przez .NET Framework.

Jeśli aplikacja jest przeznaczona dla .NET Framework 4,7 lub nowszej wersji, ten przełącznik jest domyślnie `false`. Jest to bezpieczne domyślne zalecane przez nas. Jeśli aplikacja działa w .NET Framework 4,7 lub w nowszej wersji, ale jest przeznaczona dla starszej wersji, przełącznik domyślnie jest `true`. W takim przypadku należy jawnie ustawić ją na `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Wartość `false` dla `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` powoduje, że aplikacja używa wartości zdefiniowanej w `ServicePointManager.SecurityProtocols` do zabezpieczenia komunikatów przy użyciu poświadczeń certyfikatu. Wartość `true` używa najwyższego dostępnego protokołu, do TLS 1.0

Dla aplikacji przeznaczonych dla .NET Framework 4,7 i nowszych wersji ta wartość jest domyślnie `false`. Dla aplikacji przeznaczonych dla .NET Framework 4.6.2 i starszych wartość domyślna to `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Wartość `false` dla `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` ustawia konfigurację domyślną zezwalającą systemowi operacyjnemu na wybór protokołu. Wartość `true` ustawia domyślny dostęp do najwyższego dostępnego protokołu do protokołu TLS 1.2.

W przypadku aplikacji przeznaczonych do .NET Framework 4.7.1 i nowszych wersji ta wartość jest równa `false`. Dla aplikacji przeznaczonych dla .NET Framework 4,7 i starszych wartość domyślna to `true`.

Aby uzyskać więcej informacji na temat protokołów TLS, zobacz [ograniczenia: protokoły TLS](../migration-guide/mitigation-tls-protocols.md). Aby uzyskać więcej informacji na temat przełączników `AppContext`, zobacz [`<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Konfigurowanie zabezpieczeń za pośrednictwem rejestru systemu Windows

> [!WARNING]
> Ustawienie kluczy rejestru ma wpływ na wszystkie aplikacje w systemie. Użyj tej opcji tylko wtedy, gdy masz pełną kontrolę nad komputerem i można kontrolować zmiany w rejestrze.

Jeśli ustawienie jeden lub oba przełączniki `AppContext` nie jest opcją, można kontrolować protokoły zabezpieczeń używane przez aplikację z kluczami rejestru systemu Windows opisanymi w tej sekcji. Jeśli aplikacja działa w .NET Framework 4.5.2 lub wcześniejszych wersjach lub nie można edytować pliku konfiguracji, może być niemożliwe użycie jednego lub obu przełączników `AppContext`. Jeśli chcesz skonfigurować zabezpieczenia z rejestrem, nie określaj wartości protokołu zabezpieczeń w kodzie. spowoduje to zastąpienie ustawienia rejestru.

Nazwy kluczy rejestru są podobne do nazw odpowiednich `AppContext` przełączników, ale bez `DontEnable` poprzedzone nazwą. Na przykład przełącznik `AppContext` `DontEnableSchUseStrongCrypto` jest kluczem rejestru o nazwie [schusestrongcrypto we](#schusestrongcrypto).

Te klucze są dostępne we wszystkich wersjach .NET Framework, dla których istnieje Najnowsza Poprawka zabezpieczeń. Zobacz [aktualizacje zabezpieczeń](#security-updates).

Wszystkie klucze rejestru opisane poniżej mają taki sam skutek, niezależnie od tego, czy używasz sieci HTTP (<xref:System.Net.ServicePointManager>) czy sieci TCP Sockets (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

Klucz rejestru `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` ma wartość typu DWORD. Wartość 1 powoduje, że aplikacja korzysta z mocnej kryptografii. Silne Kryptografia korzysta z bezpieczniejszych protokołów sieciowych (TLS 1,2, TLS 1,1 i TLS 1,0) i blokuje protokoły, które nie są bezpieczne. Wartość 0 powoduje wyłączenie silnej kryptografii. Aby uzyskać więcej informacji, zobacz [flagę SCH_USE_STRONG_CRYPTO](#the-sch_use_strong_crypto-flag).

Jeśli aplikacja jest przeznaczona dla .NET Framework 4,6 lub nowszej wersji, ten klucz domyślnie przyjmuje wartość 1. Jest to bezpieczne domyślne zalecane przez nas. Jeśli aplikacja działa na .NET Framework 4,6, ale jest przeznaczona dla starszej wersji, wartość klucza wynosi 0. W takim przypadku należy jawnie ustawić jego wartość na 1.

Ten klucz powinien mieć wartość 0, jeśli chcesz nawiązać połączenie ze starszymi usługami, które nie obsługują mocnej kryptografii i nie można go uaktualnić.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

Klucz rejestru `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` ma wartość typu DWORD. Wartość 1 powoduje, że aplikacja zezwala na wybór protokołu przez system operacyjny. Wartość 0 powoduje, że aplikacja korzysta z protokołów pobranych przez .NET Framework.

`<VERSION>` musi mieć 4.0.30319 v (dla .NET Framework 4 i wyższych) lub 2.0.50727 (dla .NET Framework 3,5).

Jeśli aplikacja jest przeznaczona dla .NET Framework 4,7 lub nowszej wersji, ten klucz domyślnie przyjmuje wartość 1. Jest to bezpieczne domyślne zalecane przez nas. Jeśli aplikacja działa w .NET Framework 4,7 lub w nowszej wersji, ale jest przeznaczona dla starszej wersji, klucz domyślnie przyjmuje wartość 0. W takim przypadku należy jawnie ustawić jego wartość na 1.

Aby uzyskać więcej informacji, zobacz [zbiorczej aktualizacji dla systemu Windows 10 w wersji 1511 i systemu Windows Server 2016 Technical Preview 4: 10 maja 2016 r.](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016)

Aby uzyskać więcej informacji na temat programu .NET Framework 3.5.1, zobacz [obsługiwane wersje systemu TLS .NET Framework w systemie Windows 7 z dodatkiem SP1 i Server 2008 R2 z dodatkiem SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Poniżej _. Plik REG_ ustawia klucze rejestru i ich warianty do najbardziej bezpiecznych wartości:

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

Rejestru można użyć do precyzyjnej kontroli nad protokołami negocjowanymi przez klienta i/lub aplikację serwerową. Sieć aplikacji przechodzi przez kanał Schannel (czyli inną nazwę dla [bezpiecznego kanału](/windows/desktop/SecAuthN/secure-channel). Konfigurując `Schannel`, można skonfigurować zachowanie aplikacji.

Zacznij od `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` klucz rejestru. W tym kluczu można utworzyć dowolne podklucze w zestawie `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1`i `TLS 1.2`. W każdym z tych podkluczy można utworzyć podklucze `Client` i/lub `Server`. W obszarze `Client` i `Server`można utworzyć wartości DWORD `DisabledByDefault` (0 lub 1) i `Enabled` (0 lub 0xFFFFFFFF).

## <a name="the-sch_use_strong_crypto-flag"></a>Flaga SCH_USE_STRONG_CRYPTO

Jeśli jest włączona (domyślnie przez przełącznik `AppContext` lub przez rejestr systemu Windows), .NET Framework używa flagi `SCH_USE_STRONG_CRYPTO`, gdy aplikacja zażąda protokołu zabezpieczeń TLS. Flaga `SCH_USE_STRONG_CRYPTO` może być domyślnie włączona z przełącznikiem `AppContext` lub z rejestrem. System operacyjny przekazuje flagę do `Schannel`w celu wyłączania znanych niesłabych algorytmów kryptograficznych, mechanizmów szyfrowania i protokołów TLS/SSL, które mogą być włączone w taki sposób, aby zapewnić lepszą współdziałanie. Aby uzyskać więcej informacji, zobacz:

- [Bezpieczny kanał](/windows/desktop/SecAuthN/secure-channel)
- [Struktura SCHANNEL_CRED](/windows/win32/api/schannel/ns-schannel-schannel_cred)

Flaga `SCH_USE_STRONG_CRYPTO` jest również przenoszona do `Schannel`, gdy jawnie używasz `Tls` (TLS 1,0), `Tls11`lub `Tls12` wyliczonych wartości <xref:System.Net.SecurityProtocolType> lub <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Aktualizacje zabezpieczeń

Najlepsze rozwiązania w tym artykule zależą od zainstalowanych najnowszych aktualizacji zabezpieczeń. Te aktualizacje obejmują możliwość korzystania z zaawansowanych funkcji .NET Framework 4,7 i nowszych. Najnowsze aktualizacje zabezpieczeń są ważne, jeśli aplikacja działa w .NET Framework 4,7 i nowszych wersjach (nawet jeśli jest przeznaczona do wcześniejszej wersji).

Aby zaktualizować .NET Framework, aby umożliwić systemowi operacyjnemu wybranie najlepszej wersji protokołu TLS do użycia, należy zainstalować co najmniej:

- [Wersja Zapoznawcza .NET Framework sierpnia 2017](https://devblogs.microsoft.com/dotnet/net-framework-august-2017-preview-of-quality-rollup/).
- **Lub** [.NET Framework wrzesień 2017](https://devblogs.microsoft.com/dotnet/net-framework-september-2017-security-and-quality-rollup/).

Patrz również:

- [Wersje i zależności platformy .NET Framework](../migration-guide/versions-and-dependencies.md)
- [Instrukcje: Określanie, które wersje .NET Framework są zainstalowane](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>Obsługa protokołu TLS 1.2

Aby aplikacja negocjowała protokół TLS 1,2, system operacyjny i wersja .NET Framework muszą obsługiwać protokół TLS 1,2.

**Wymagania dotyczące systemu operacyjnego do obsługi protokołu TLS 1,2**

Aby włączyć lub ponownie włączyć protokół TLS 1,2 i/lub TLS 1,1 w systemie, który je obsługuje, zobacz [Ustawienia rejestru Transport Layer Security (TLS)](/windows-server/security/tls/tls-registry-settings).

| **OS** | **Obsługa protokołu TLS 1,2** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | Obsługiwane i domyślnie włączona. |
| Windows 8.1<br>Windows Server 2012 z dodatkiem R2 | Obsługiwane i domyślnie włączona. |
| Windows 8.0<br>Windows Server 2012 | Obsługiwane i domyślnie włączona. |
| Dodatek SP1 dla systemu Windows 7<br>Windows Server 2008 R2 SP1 | Obsługiwane, ale nie jest włączony domyślnie. Aby uzyskać szczegółowe informacje na temat włączania protokołu TLS 1,2, zobacz stronę internetową [Ustawienia rejestru Transport Layer Security (TLS)](/windows-server/security/tls/tls-registry-settings) . |
| Windows Server 2008 | Obsługa protokołu TLS 1,2 i TLS 1,1 wymaga aktualizacji. Zobacz [Aktualizacja, aby dodać obsługę protokołów tls 1,1 i tls 1,2 w systemie Windows Server 2008 SP2](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Nieobsługiwane. |

Aby uzyskać informacje o tym, które protokoły TLS/SSL są domyślnie włączone w każdej wersji systemu Windows, zobacz [protokoły w protokole TLS/SSL (Dostawca SSP Schannel)](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).

**Wymagania dotyczące obsługi protokołu TLS 1,2 z .NET Framework 3,5**

W tej tabeli przedstawiono aktualizację systemu operacyjnego, która będzie potrzebna do obsługi protokołu TLS 1,2 z .NET Framework 3,5. Zalecamy stosowanie wszystkich aktualizacji systemu operacyjnego.

| **OS** | **Minimalna aktualizacja wymagana do obsługi protokołu TLS 1,2 z .NET Framework 3,5** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | [Aktualizacja zbiorcza dla systemu Windows 10 w wersji 1511 i Windows Server 2016 Technical Preview 4: maj 10, 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1<br>Windows Server 2012 z dodatkiem R2 | [Obsługa domyślnych wersji systemu TLS uwzględnionych w .NET Framework 3,5 w systemach Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0<br>Windows Server 2012 | [Obsługa domyślnych wersji systemu TLS uwzględnionych w .NET Framework 3,5 w systemie Windows Server 2012](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Dodatek SP1 dla systemu Windows 7<br>Windows Server 2008 R2 SP1 | [Obsługa domyślnych wersji systemu TLS uwzględnionych w .NET Framework 3.5.1 w systemach Windows 7 z dodatkiem SP1 i Server 2008 R2 z dodatkiem SP1](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Obsługa domyślnych wersji systemu TLS uwzględnionych w .NET Framework 2,0 SP2 w systemie Windows Vista z dodatkiem SP2 i Server 2008 z dodatkiem SP2](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Nieobsługiwane |

## <a name="azure-cloud-services"></a>Usługi w chmurze platformy Azure

Jeśli używasz ról Sieć Web i proces roboczy [platformy Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) , aby hostować i uruchamiać aplikację, należy wziąć pod uwagę pewne kwestie dotyczące obsługi protokołu TLS 1,2.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>.NET Framework 4,7 nie jest domyślnie zainstalowany w systemie operacyjnym gościa platformy Azure

Najnowsza wersja zainstalowana w najnowszej wersji rodziny systemów operacyjnych gościa platformy Azure 5 (Windows Server 2016) to 4.6.2. Aby sprawdzić, które wersje .NET Framework są zainstalowane w każdym systemie operacyjnym gościa platformy Azure, zapoznaj się z tematem wersje [systemu operacyjnego gościa platformy Azure i macierz zgodności zestawu SDK](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Jeśli aplikacja jest przeznaczona dla .NET Framework wersji, która nie jest dostępna w wersji systemu operacyjnego gościa platformy Azure, należy ją zainstalować samodzielnie. Zobacz [Instalowanie platformy .NET w rolach usługi w chmurze platformy Azure](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Jeśli instalacja struktury wymaga ponownego uruchomienia, role usługi mogą być również ponownie uruchomione przed wprowadzeniem stanu gotowości.

### <a name="azure-guest-os-registry-settings"></a>Ustawienia rejestru systemu operacyjnego gościa platformy Azure

Obraz rodziny systemów operacyjnych gościa platformy Azure 5 dla [platformy azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) ma już klucz rejestru `SchUseStrongCrypto` ustawiony na wartość 1. Aby uzyskać więcej informacji, zobacz [schusestrongcrypto we](#schusestrongcrypto).

Ustaw klucz rejestru [SystemDefaultTlsVersions](#systemdefaulttlsversions) na 1. Zobacz [Konfigurowanie zabezpieczeń za pośrednictwem rejestru systemu Windows](#configuring-security-via-the-windows-registry).
