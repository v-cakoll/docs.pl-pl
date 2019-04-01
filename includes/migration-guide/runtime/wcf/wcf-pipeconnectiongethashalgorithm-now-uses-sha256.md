---
ms.openlocfilehash: 71f61f23a8b17459610d253766a99e594f09428e
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760454"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>Usługi WCF PipeConnection.GetHashAlgorithm używa teraz SHA256

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1 Windows Communication Foundation używa skrót SHA256 do wygenerowania losowych nazw dla nazwanych potoków. W .NET Framework 4.7 i wcześniejszych wersjach on Skrót SHA1.|
|Sugestia|Jeśli napotkasz problem ze zgodnością za pomocą tej zmiany w środowisku .NET Framework 4.7.1 lub później, użytkownik może zrezygnować go, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Środowisko uruchomieniowe|

