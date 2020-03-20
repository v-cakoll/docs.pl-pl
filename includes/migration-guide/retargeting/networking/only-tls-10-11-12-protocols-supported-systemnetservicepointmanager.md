---
ms.openlocfilehash: 5b531dc23feb311a797823dfa2a4d853859f9e18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235551"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Tylko protokoły Tls 1.0, 1.1 i 1.2 obsługiwane w system.net.ServicePointManager i System.Net.Security.SslStream

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.6 <xref:System.Net.ServicePointManager> i <xref:System.Net.Security.SslStream> klasy mogą używać tylko jeden z następujących trzech protokołów: Tls1.0, Tls1.1 lub Tls1.2. Protokół SSL3.0 i szyfr RC4 nie są obsługiwane.|
|Sugestia|Zalecane ograniczenie jest uaktualnienie aplikacji po stronie sever do Tls1.0, Tls1.1 lub Tls1.2. Jeśli nie jest to możliwe lub jeśli aplikacje klienckie są uszkodzone, <xref:System.AppContext?displayProperty=name> klasa może służyć do rezygnacji z tej funkcji na dwa sposoby:<ol><li>Poprzez programowe ustawienie przełączników compat na <xref:System.AppContext?displayProperty=name>, jak wyjaśniono [tutaj](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku app.config:</li></ol><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|
