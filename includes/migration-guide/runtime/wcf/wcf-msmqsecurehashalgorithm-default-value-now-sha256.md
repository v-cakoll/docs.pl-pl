---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857270"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm wartość domyślna jest teraz SHA256

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.7.1, domyślny algorytm podpisywania wiadomości w WCF dla komunikatów Msmq jest SHA256. W .NET Framework 4.7 i wcześniejszych wersjach domyślny algorytm podpisywania wiadomości jest SHA1.|
|Sugestia|Jeśli napotkasz problemy ze zgodnością z tą zmianą w programie .NET Framework 4.7.1 lub <code>&lt;runtime&gt;</code>nowszym, możesz zrezygnować ze zmiany, dodając następujący wiersz do sekcji pliku app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Środowisko uruchomieniowe|
