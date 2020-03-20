---
ms.openlocfilehash: eff7e7cfc8fa0b4bc8ee3a64a7c60ee21d51f466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997684"
---
### <a name="resizing-a-grid-can-hang"></a>Zmiana rozmiaru siatki może się zawiesić

|   |   |
|---|---|
|Szczegóły|Nieskończona pętla <code>T:System.Windows.Controls.Grid</code> może wystąpić podczas układu a w następujących okolicznościach:<ul><li>Definicje wierszy zawierają dwa *-wiersze, oba deklarując MinHeight i MaxHeight.</li><li>Zawartość *-wierszy nie przekracza odpowiedniego maxheight</li><li>Dostępna wysokość siatki jest przekroczona przez pierwszy MinHeight (plus wszystkie inne stałe lub automatyczne wiersze)</li><li>Aplikacja jest przeznaczona dla platformy .NET Framework 4.7 lub włącza algorytm alokacji 4.7, ustawiając<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Pętla będzie również zdarzyć się z więcej niż dwa wiersze lub w analogicznym przypadku dla kolumn. Problem został rozwiązany w .NET Framework 4.7.1.|
|Sugestia|Uaktualnienie do programu .NET Framework 4.7.1.  Alternatywnie, jeśli nie potrzebujesz algorytmu alokacji 4.7, możesz użyć następującego ustawienia konfiguracji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
