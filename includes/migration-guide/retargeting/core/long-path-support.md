---
ms.openlocfilehash: 506218195417548880a9d8d10508a570a7769682
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859355"
---
### <a name="long-path-support"></a>Obsługa długich ścieżek

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji docelowych .NET Framework 4.6.2, obsługiwane są długie ścieżki (maksymalnie 32K znaków), a <code>MAX_PATH</code>260-znakowe (lub) ograniczenie długości ścieżki zostało usunięte. W przypadku aplikacji, które są ponownie kompilowane do celu .NET Framework 4.6.2, ścieżki kodu, który wcześniej <xref:System.IO.PathTooLongException?displayProperty=name> <xref:System.IO.PathTooLongException?displayProperty=name> rzucił, ponieważ ścieżka przekroczona 260 znaków będzie teraz zgłosić tylko w następujących warunkach:<ul><li>Długość ścieżki jest większa <xref:System.Int16.MaxValue> niż (32 767) znaków.</li><li>System operacyjny <code>COR_E_PATHTOOLONG</code> zwraca lub jego odpowiednik.</li></ul>W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.6.1 i <xref:System.IO.PathTooLongException?displayProperty=name> wcześniejszych wersji środowisko wykonawcze automatycznie zgłasza, gdy ścieżka przekracza 260 znaków.|
|Sugestia|W przypadku aplikacji przeznaczonych dla programu .NET Framework 4.6.2 można zrezygnować z obsługi długiej <code>&lt;runtime&gt;</code> ścieżki, <code>app.config</code> jeśli nie jest to pożądane, dodając do sekcji pliku następujące elementy:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>W przypadku aplikacji przeznaczonych dla starszych wersji programu .NET Framework, ale uruchamianych w programie .NET Framework 4.6.2 lub nowszym, można zdecydować się na obsługę długiej ścieżki, dodając do <code>&lt;runtime&gt;</code> sekcji <code>app.config</code> pliku następujące elementy:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|
