---
ms.openlocfilehash: 19dcdf006de0bfa7c6b0a8127612a49a66a24802
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804609"
---
### <a name="tls-1x-by-default-passes-the-schsendauxrecord-flag-to-the-underlying-schannel-api"></a>TLS 1.x domyślnie przekazuje flagę SCH_SEND_AUX_RECORD podstawowego interfejsu API kanału SCHANNEL

|   |   |
|---|---|
|Szczegóły|Korzystając z protokołu TLS 1.x, .NET Framework zależy od bazowego API Windows w dostawcy SCHANNEL. Począwszy od programu .NET Framework 4.6, [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) flaga jest przekazywany domyślnie do dostawcy SCHANNEL. Powoduje to, że dostawcę SCHANNEL, aby podzielić dane były szyfrowane na dwa osobne rekordy, pierwszy jako pojedynczych bajtów, a drugi jako <em>n</em>b-1. W rzadkich przypadkach to spowoduje przerwanie komunikacji między klientami a serwerami istniejącego, składające się na założeniu, że dane znajdują się w jednym rekordzie.|
|Sugestia|Jeśli ta zmiana powoduje przerwanie komunikacji z istniejącego serwera, możesz wyłączyć wysyłanie [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) Flaga, a następnie przywrócić poprzednie zachowanie nie dzielenia danych na osobne rekordy, dodając następujące Przełącz do [ < ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ < ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] To ustawienie jest dostępne tylko w przypadku zgodności z poprzednimi wersjami. W przeciwnym razie jego użycie nie jest zalecane.</blockquote> |
|Scope|Krawędź|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

