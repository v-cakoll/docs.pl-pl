---
ms.openlocfilehash: 5df5afec17d400ed14fe9b4c03c2f754895f0dd7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378772"
---
### <a name="resizing-a-grid-can-cause-an-application-to-become-unresponsive"></a>Zmiany rozmiaru siatki może spowodować, że aplikacja przestanie odpowiadać

|   |   |
|---|---|
|Szczegóły|Wejścia w nieskończoną pętlę mogą wystąpić podczas układ <code>T:System.Windows.Controls.Grid</code> w następujących okolicznościach:<ul><li>Definicje wiersz zawiera dwa *-wiersze z obu deklarowanie MinHeight i MaxHeight.</li><li>Zawartość *-wierszy nie może przekraczać odpowiedniego MaxHeight</li><li>Pierwszy MinHeight przekracza dostępny wysokość siatki (oraz wszelkich innych ustalony rozmiar lub Auto wierszy)</li><li>Aplikacja jest przeznaczony dla .NET Framework 4.7 lub powoduje zasubskrybowanie algorytmu 4,7 alokacji, ustawiając <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Pętla również się stanie z więcej niż dwóch wierszy lub w przypadku analogiczne dla kolumn. Problem został rozwiązany w programie .NET Framework 4.7.1.|
|Sugestia|Uaktualnianie do programu .NET Framework 4.7.1.  Alternatywnie Jeśli nie potrzebujesz algorytmu 4,7 alokacji służy następujące ustawienie konfiguracji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Krawędź|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
