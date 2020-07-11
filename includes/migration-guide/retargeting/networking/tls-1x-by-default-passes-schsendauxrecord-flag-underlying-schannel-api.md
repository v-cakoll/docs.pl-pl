---
ms.openlocfilehash: 207dba9327cfd6debd15c5573697f8950b6c2c95
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86218259"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>Protokół TLS 1. x domyślnie przekazuje flagę SCH_SEND_AUX_RECORD do źródłowego interfejsu API SCHANNEL

#### <a name="details"></a>Szczegóły

W przypadku korzystania z protokołu TLS 1. x .NET Framework opiera się na źródłowym interfejsie API SCHANNEL systemu Windows. Począwszy od .NET Framework 4,6, flaga [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) jest domyślnie przenoszona do kanału Schannel. Powoduje to, że SCHANNEL dzieli dane tak, aby były szyfrowane do dwóch oddzielnych rekordów, pierwszy jako jeden bajt, a drugi jako <em>n</em>-1 b. W rzadkich przypadkach powoduje to przerwanie komunikacji między klientami a istniejącymi serwerami, które zakładają, że dane znajdują się w pojedynczym rekordzie.

#### <a name="suggestion"></a>Sugestia

Jeśli ta zmiana powoduje przerwanie komunikacji z istniejącym serwerem, można wyłączyć wysyłanie flagi [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) i przywrócić poprzednie zachowanie niedzielenia danych na oddzielne rekordy, dodając następujący przełącznik do [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu w [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> To ustawienie jest dostępne wyłącznie w celu zapewnienia zgodności z poprzednimi wersjami. Jego użycie nie jest zalecane.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Edge        |
| Wersja | 4.6         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
