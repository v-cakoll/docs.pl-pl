---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859074"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>Zabezpieczenia wiadomości WCF mogą teraz używać TLS1.1 i TLS1.2

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7, klienci mogą konfigurować tls1.1 lub TLS1.2 w zabezpieczeniach wiadomości WCF oprócz SSL3.0 i TLS1.0 za pomocą ustawień konfiguracji aplikacji.|
|Sugestia|W .NET Framework 4.7 obsługa TLS1.1 i TLS1.2 w zabezpieczeniach komunikatów WCF jest domyślnie wyłączona. Można go włączyć, dodając następujący <code>&lt;runtime&gt;</code> wiersz do sekcji pliku app.config lub web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.7|
|Typ|Przekierowanie|
