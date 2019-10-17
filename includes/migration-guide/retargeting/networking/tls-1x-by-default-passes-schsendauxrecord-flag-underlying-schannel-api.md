---
ms.openlocfilehash: fc17efbad63ee43ddcdfd14e2fbd1557d2b3d31c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72424789"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>Protokół TLS 1. x domyślnie przekazuje flagę SCH_SEND_AUX_RECORD do źródłowego interfejsu API SCHANNEL

|   |   |
|---|---|
|Szczegóły|W przypadku korzystania z protokołu TLS 1. x .NET Framework opiera się na źródłowym interfejsie API SCHANNEL systemu Windows. Począwszy od .NET Framework 4,6, flaga [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) jest domyślnie przenoszona do kanału Schannel. Powoduje to, że SCHANNEL dzieli dane tak, aby były szyfrowane do dwóch oddzielnych rekordów, pierwszy jako jeden bajt, a drugi jako <em>n</em>-1 b. W rzadkich przypadkach powoduje to przerwanie komunikacji między klientami a istniejącymi serwerami, które zakładają, że dane znajdują się w pojedynczym rekordzie.|
|Sugestia|Jeśli ta zmiana powoduje przerwanie komunikacji z istniejącym serwerem, można wyłączyć wysyłanie flagi [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) i przywrócić poprzednie zachowanie niedzielenia danych na oddzielne rekordy, dodając następujący przełącznik do [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element w sekcji [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] To ustawienie jest dostępne wyłącznie w celu zapewnienia zgodności z poprzednimi wersjami. Jego użycie nie jest zalecane.</blockquote> |
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
