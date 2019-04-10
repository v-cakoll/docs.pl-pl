---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235628"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Karty strumienia WinRT nie są już wywoływać FlushAsync automatycznie przy zamykaniu

|   |   |
|---|---|
|Szczegóły|W aplikacjach Windows Store kart strumienia środowiska wykonawczego Windows nie jest już wywołać metodę FlushAsync z metody Dispose.|
|Sugestia|Ta zmiana powinny być przezroczyste. Deweloperzy mogą przywrócić poprzednie zachowanie przez pisanie kodu w następujący sposób:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
