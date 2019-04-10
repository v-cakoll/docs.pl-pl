---
ms.openlocfilehash: 63101fb127c84de21d165994bba85a2753e97344
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236610"
---
### <a name="resizing-a-grid-can-hang"></a>Zmiany rozmiaru siatki może zostać zawieszone.

|   |   |
|---|---|
|Szczegóły|Wejścia w nieskończoną pętlę mogą wystąpić podczas układ <code>T:System.Windows.Controls.Grid</code> w następujących okolicznościach:<ul><li>Definicje wiersz zawiera dwa *-wiersze z obu deklarowanie MinHeight i MaxHeight.</li><li>Zawartość *-wierszy nie może przekraczać odpowiedniego MaxHeight</li><li>Pierwszy MinHeight przekracza dostępny wysokość siatki (oraz wszelkich innych ustalony rozmiar lub Auto wierszy)</li><li>Aplikacja jest przeznaczony dla .NET Framework 4.7 lub powoduje zasubskrybowanie algorytmu 4,7 alokacji, ustawiając <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Pętla również się stanie z więcej niż dwóch wierszy lub w przypadku analogiczne dla kolumn. Problem został rozwiązany w programie .NET Framework 4.7.1.|
|Sugestia|Uaktualnianie do programu .NET Framework 4.7.1.  Alternatywnie Jeśli nie potrzebujesz algorytmu 4,7 alokacji służy następujące ustawienie konfiguracji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
