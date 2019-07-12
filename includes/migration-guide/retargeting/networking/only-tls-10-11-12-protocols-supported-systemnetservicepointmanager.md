---
ms.openlocfilehash: 2a8f20bef8e865235b857014e6d24c625c851d83
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804427"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Tylko protokoły Tls 1.0, 1.1 i 1.2, obsługiwane w System.Net.ServicePointManager i elementu System.Net.Security.SslStream

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6 <xref:System.Net.ServicePointManager> i <xref:System.Net.Security.SslStream> klasy tylko mogą korzystać z jednego z następujących trzech protokołów: Tls1.0, Tls1.1 lub Tls1.2. Protokół SSL3.0 i szyfrowania RC4 nie są obsługiwane.|
|Sugestia|Zalecane środki zaradcze jest uaktualnienie aplikacji po stronie serwera do Tls1.0, Tls1.1 lub Tls1.2. Jeśli nie jest to możliwe, czy działają aplikacje klienckie <xref:System.AppContext?displayProperty=name> klasy można zrezygnować z tej funkcji w jednej z dwóch sposobów:<ol><li>Programowe ustawiając zgodności zmienia się <xref:System.AppContext?displayProperty=name>, zgodnie z objaśnieniem [tutaj](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config:</li></ol><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;&#13;&#10;</code></pre>|
|Scope|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|

