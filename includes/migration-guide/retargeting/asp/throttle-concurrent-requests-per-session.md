---
ms.openlocfilehash: db8eb017bdf166b0f1a241f5a8f7db9b9430898a
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760283"
---
### <a name="throttle-concurrent-requests-per-session"></a>Ograniczenie przepustowości równoczesnych żądań na sesję

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 wcześniej ASP.NET sekwencyjnie wykonuje żądania z tego samego identyfikatora sesji i ASP.NET zawsze generuje Sessionid za pomocą plików cookie domyślnie. Jeśli strona zajmuje długi czas odpowiedzi, znacznie zmniejszy to wydajność serwera po prostu przez naciśnięcie klawisza F5 w przeglądarce. Poprawka dodaliśmy licznika do śledzenia żądań w kolejce i kończenia żądań, po przekroczeniu przez określony limit. Wartością domyślną jest 50. W przypadku osiągnięcia limitu ostrzeżenie będą rejestrowane w zdarzeń dziennika i odpowiedź HTTP 500, które mogą być rejestrowane w dzienniku usług IIS.|
|Sugestia|Aby przywrócić starsze zachowanie, można dodać następujące ustawienie do pliku web.config, aby zrezygnować z nowego zachowania.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Przekierowanie|

