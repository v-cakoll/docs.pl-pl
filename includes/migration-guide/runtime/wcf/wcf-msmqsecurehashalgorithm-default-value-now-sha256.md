---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804772"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>Wartość domyślna WCF MsmqSecureHashAlgorithm jest teraz SHA256

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1 komunikat domyślny algorytm programu WCF dla wiadomości usługi Msmq podpisywania jest algorytm SHA256. W .NET Framework 4.7 i wcześniejszych wersjach komunikat domyślny algorytm podpisywania jest algorytm SHA1.|
|Sugestia|Jeśli napotkasz problemy ze zgodnością za pomocą tej zmiany w środowisku .NET Framework 4.7.1 lub nowszej, użytkownik może zrezygnować zmiany, dodając następujący wiersz do <code>&lt;runtime&gt;</code>sekcji w pliku app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Środowisko uruchomieniowe|
