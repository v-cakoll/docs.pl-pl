---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615697"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Tylko protokoły TLS 1,0, 1,1 i 1,2 obsługiwane w systemie .NET. ServicePointManager i system .NET. Security. SslStream

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,6, <xref:System.Net.ServicePointManager> klasy i mogą <xref:System.Net.Security.SslStream> korzystać tylko z jednego z następujących trzech protokołów: TLS 1.0, TLS 1.1 lub TLS 1.2. Protokół SSL 3.0 i szyfr RC4 nie są obsługiwane.

#### <a name="suggestion"></a>Sugestia

Zalecane jest, aby uaktualnić aplikację po stronie serwera do protokołu TLS 1.0, TLS 1.1 lub TLS 1.2. Jeśli nie jest to możliwe, lub jeśli aplikacje klienckie są uszkodzone, <xref:System.AppContext?displayProperty=fullName> można użyć klasy, aby zrezygnować z tej funkcji na dwa sposoby:

- Przez programowe ustawianie przełączników zgodności w programie <xref:System.AppContext?displayProperty=fullName> , jak wyjaśniono [tutaj](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).
- Dodając następujący wiersz do `<runtime>` sekcji pliku app.config:

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>
