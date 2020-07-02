---
ms.openlocfilehash: 86169b5c9a20678647153c951550e590a5bce588
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622266"
---
### <a name="resizing-a-grid-can-hang"></a>Zmienianie rozmiarów siatki może się zawiesić

#### <a name="details"></a>Szczegóły

Pętla nieskończona może wystąpić podczas układu w <code>T:System.Windows.Controls.Grid</code> następujących okolicznościach:<ul><li>Definicje wierszy zawierają dwa \* wiersze, deklarując MinHeight i MaxHeight.</li><li>Zawartość \* wierszy nie przekracza odpowiedniego MaxHeight</li><li>Dostępna wysokość siatki jest przekraczana przez pierwszy MinHeight (plus wszystkie inne stałe lub autowiersze)</li><li>Aplikacja jest przeznaczona dla .NET Framework 4,7 lub jest docelowa do algorytmu alokacji 4,7 przez ustawienie<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Pętla również występuje z więcej niż dwoma wierszami lub analogicznie do kolumn. Problem został rozwiązany w .NET Framework 4.7.1.

#### <a name="suggestion"></a>Sugestia

Uaktualnij do .NET Framework 4.7.1.  Alternatywnie, jeśli nie jest potrzebny algorytm alokacji 4,7, można użyć następującego ustawienia konfiguracji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4,7|
|Typ|Środowisko uruchomieniowe|
