---
ms.openlocfilehash: 506218195417548880a9d8d10508a570a7769682
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640113"
---
### <a name="long-path-support"></a>Obsługa długich ścieżek

|   |   |
|---|---|
|Szczegóły|Uruchamianie aplikacji, których platformą docelową .NET Framework 4.6.2, długich ścieżek (maksymalnie 32 znaków K) są obsługiwane i 260 znaków (lub <code>MAX_PATH</code>) ograniczenia długości ścieżki została usunięta. W przypadku aplikacji, które są ponownie kompilowane pod kątem programu .NET Framework 4.6.2, kod ścieżek, które wcześniej zgłosił <xref:System.IO.PathTooLongException?displayProperty=name> ponieważ ścieżki przekracza 260 znaków, teraz spowoduje zgłoszenie <xref:System.IO.PathTooLongException?displayProperty=name> tylko w następujących warunkach:<ul><li>Długość ścieżki jest większa niż <xref:System.Int16.MaxValue> (32 767) znaków.</li><li>System operacyjny zwraca <code>COR_E_PATHTOOLONG</code> lub równoważnym.</li></ul>W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.6.1 i wcześniejszymi wersjami, środowisko wykonawcze automatycznie zgłasza <xref:System.IO.PathTooLongException?displayProperty=name> zawsze, gdy długość ścieżki przekracza 260 znaków.|
|Sugestia|W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.6.2, można zrezygnować z długą ścieżką pomocy technicznej, jeśli nie jest pożądane, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> części Twojej <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Dla aplikacji przeznaczonych dla wcześniejszych wersji programu .NET Framework jednak uruchomić w środowisku .NET Framework 4.6.2 lub później, można włączyć długie ścieżki pomocy technicznej, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> części Twojej <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|
