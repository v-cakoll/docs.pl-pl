---
ms.openlocfilehash: 1e4c0ac1f0f9011f4b8fc136ec2e383d38567355
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83435438"
---
### <a name="resizing-a-grid-can-hang"></a>Zmienianie rozmiarów siatki może się zawiesić

|   |   |
|---|---|
|Szczegóły|Pętla nieskończona może wystąpić podczas układu w <code>T:System.Windows.Controls.Grid</code> następujących okolicznościach:<ul><li>Definicje wierszy zawierają dwa \* wiersze, deklarując MinHeight i MaxHeight.</li><li>Zawartość \* wierszy nie przekracza odpowiedniego MaxHeight</li><li>Dostępna wysokość siatki jest przekraczana przez pierwszy MinHeight (plus wszystkie inne stałe lub autowiersze)</li><li>Aplikacja jest przeznaczona dla .NET Framework 4,7 lub jest docelowa do algorytmu alokacji 4,7 przez ustawienie<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Pętla również występuje z więcej niż dwoma wierszami lub analogicznie do kolumn. Problem został rozwiązany w .NET Framework 4.7.1.|
|Sugestia|Uaktualnij do .NET Framework 4.7.1.  Alternatywnie, jeśli nie jest potrzebny algorytm alokacji 4,7, można użyć następującego ustawienia konfiguracji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Edge|
|Wersja|4,7|
|Typ|Środowisko uruchomieniowe|
