---
ms.openlocfilehash: fc17efbad63ee43ddcdfd14e2fbd1557d2b3d31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72424789"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>Protokół TLS 1.x domyślnie przekazuje flagę SCH_SEND_AUX_RECORD do bazowego interfejsu API SCHANNEL

|   |   |
|---|---|
|Szczegóły|Podczas korzystania z protokołu TLS 1.x program .NET Framework opiera się na podstawowym interfejsie API SCHANNEL systemu Windows. Począwszy od programu .NET Framework 4.6, flaga [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) jest przekazywana domyślnie do pliku SCHANNEL. Powoduje to, że SCHANNEL do dzielenia danych do szyfrowania na dwa oddzielne rekordy, pierwszy jako pojedynczy bajt, a drugi jako <em>n</em>-1 bajtów. W rzadkich przypadkach ta przerywa komunikację między klientami a istniejącymi serwerami, które zakładają, że dane znajdują się w jednym rekordzie.|
|Sugestia|Jeśli ta zmiana przerywa komunikację z istniejącym serwerem, można wyłączyć wysyłanie flagi [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) i przywrócić poprzednie zachowanie nie [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dzielenia [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) danych na oddzielne rekordy, dodając następujący przełącznik do elementu w sekcji pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] To ustawienie jest dostępne tylko w przypadku zgodności z przeszywnie. Jego stosowanie nie jest zalecane.</blockquote> |
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
