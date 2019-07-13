---
ms.openlocfilehash: f672645fb98f511f7e1326c9c584b287a0fae7dc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859355"
---
### <a name="long-path-support"></a>Obsługa długich ścieżek

|   |   |
|---|---|
|Szczegóły|Uruchamianie aplikacji, których platformą docelową .NET Framework 4.6.2, długich ścieżek (maksymalnie 32 znaków K) są obsługiwane i 260 znaków (lub <code>MAX_PATH</code>) ograniczenia długości ścieżki została usunięta. W przypadku aplikacji, które są ponownie kompilowane pod kątem programu .NET Framework 4.6.2, kod ścieżek, które wcześniej zgłosił <xref:System.IO.PathTooLongException?displayProperty=name> ponieważ ścieżki przekracza 260 znaków, teraz spowoduje zgłoszenie <xref:System.IO.PathTooLongException?displayProperty=name> tylko w następujących warunkach:<ul><li>Długość ścieżki jest większa niż <xref:System.Int16.MaxValue> (32 767) znaków.</li><li>System operacyjny zwraca <code>COR_E_PATHTOOLONG</code> lub równoważnym.</li></ul>W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.6.1 i wcześniejszymi wersjami, środowisko wykonawcze automatycznie zgłasza <xref:System.IO.PathTooLongException?displayProperty=name> zawsze, gdy długość ścieżki przekracza 260 znaków.|
|Sugestia|W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.6.2, można zrezygnować z długą ścieżką pomocy technicznej, jeśli nie jest pożądane, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> części Twojej <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Dla aplikacji przeznaczonych dla wcześniejszych wersji programu .NET Framework jednak uruchomić w środowisku .NET Framework 4.6.2 lub później, można włączyć długie ścieżki pomocy technicznej, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> części Twojej <code>app.config</code> pliku:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|

