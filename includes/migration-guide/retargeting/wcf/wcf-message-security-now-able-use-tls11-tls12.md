---
ms.openlocfilehash: 3b7b50700541649a785fa9bbe3ecc56c2697fbfc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859074"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>Zabezpieczenie wiadomości WCF teraz jest w stanie używać TLS1.1 i TLS1.2

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7, klienci mogą skonfigurować TLS1.1 lub TLS1.2 w ramach zabezpieczeń komunikatów WCF oprócz SSL3.0 i TLS1.0 przy użyciu ustawień konfiguracji aplikacji.|
|Sugestia|W programie .NET Framework 4.7 Obsługa TLS1.1 i TLS1.2 w ramach zabezpieczeń komunikatów WCF jest domyślnie wyłączona. Możesz je włączyć, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config lub web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Krawędź|
|Wersja|4.7|
|Typ|Przekierowanie|

