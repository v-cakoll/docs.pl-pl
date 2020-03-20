---
ms.openlocfilehash: 9c3eedb7f7d4cd030a12c141b8630876c1ffdb4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859141"
---
### <a name="throttle-concurrent-requests-per-session"></a>Ograniczanie równoczesnych żądań na sesję

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6.2 i wcześniejszych ASP.NET wykonuje żądania z tym samym Sessionid sekwencyjnie i ASP.NET zawsze wystawia Sessionid za pośrednictwem plików cookie domyślnie. Jeśli strona zajmuje dużo czasu, aby odpowiedzieć, znacznie obniży wydajność serwera tylko naciskając klawisz F5 w przeglądarce. W poprawce dodaliśmy licznik do śledzenia żądań w kolejce i zakończenia żądań, gdy przekraczają określony limit. Wartość domyślna to 50. Jeśli limit zostanie osiągnięty, ostrzeżenie zostanie zarejestrowane w dzienniku zdarzeń, a odpowiedź HTTP 500 może zostać zarejestrowana w dzienniku usługi IIS.|
|Sugestia|Aby przywrócić stare zachowanie, można dodać następujące ustawienie do pliku web.config, aby zrezygnować z nowego zachowania.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.7|
|Typ|Przekierowanie|
