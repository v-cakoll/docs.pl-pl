---
ms.openlocfilehash: eff7e7cfc8fa0b4bc8ee3a64a7c60ee21d51f466
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997684"
---
### <a name="resizing-a-grid-can-hang"></a>Zmienianie rozmiarów siatki może się zawiesić

|   |   |
|---|---|
|Szczegóły|Pętla nieskończona może wystąpić podczas układu <code>T:System.Windows.Controls.Grid</code> w następujących okolicznościach:<ul><li>Definicje wierszy zawierają dwa *-wiersze, które deklarują MinHeight i MaxHeight.</li><li>Zawartość *-wierszy nie przekracza odpowiadającego MaxHeight</li><li>Dostępna wysokość siatki jest przekraczana przez pierwszy MinHeight (plus wszystkie inne stałe lub autowiersze)</li><li>Aplikacja jest przeznaczona dla .NET Framework 4,7 lub jest docelowa do algorytmu alokacji 4,7 przez ustawienie<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Pętla również występuje z więcej niż dwoma wierszami lub analogicznie do kolumn. Problem został rozwiązany w .NET Framework 4.7.1.|
|Sugestia|Uaktualnij do .NET Framework 4.7.1.  Alternatywnie, jeśli nie jest potrzebny algorytm alokacji 4,7, można użyć następującego ustawienia konfiguracji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Krawędź|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
