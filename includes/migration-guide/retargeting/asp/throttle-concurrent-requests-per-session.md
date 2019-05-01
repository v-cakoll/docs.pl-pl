---
ms.openlocfilehash: 9c3eedb7f7d4cd030a12c141b8630876c1ffdb4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759525"
---
### <a name="throttle-concurrent-requests-per-session"></a>Ograniczenie przepustowości równoczesnych żądań na sesję

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 wcześniej ASP.NET sekwencyjnie wykonuje żądania z tego samego identyfikatora sesji i ASP.NET zawsze generuje Sessionid za pomocą plików cookie domyślnie. Jeśli strona zajmuje długi czas odpowiedzi, znacznie zmniejszy to wydajność serwera po prostu przez naciśnięcie klawisza F5 w przeglądarce. Poprawka dodaliśmy licznika do śledzenia żądań w kolejce i kończenia żądań, po przekroczeniu przez określony limit. Wartością domyślną jest 50. W przypadku osiągnięcia limitu ostrzeżenie będą rejestrowane w zdarzeń dziennika i odpowiedź HTTP 500, które mogą być rejestrowane w dzienniku usług IIS.|
|Sugestia|Aby przywrócić starsze zachowanie, można dodać następujące ustawienie do pliku web.config, aby zrezygnować z nowego zachowania.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Przekierowanie|
