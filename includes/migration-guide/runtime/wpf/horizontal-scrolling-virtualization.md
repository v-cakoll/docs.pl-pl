---
ms.openlocfilehash: 0825233c0dae131fa9d00565348fac6fdf0be063
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760660"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Przewijanie w poziomie i wirtualizacji

|   |   |
|---|---|
|Szczegóły|Ta zmiana dotyczy <xref:System.Windows.Controls.ItemsControl?displayProperty=name> wykonujący swój własny wirtualizacji w kierunku prostopadły głównego kierunek przewijania (główny przykład <xref:System.Windows.Controls.DataGrid?displayProperty=name> EnableColumnVirtualization =&quot;True&quot;).  Wynik określonych operacji w poziomie przewijania został zmieniony w celu uzyskania wyników, które są bardziej intuicyjne i bardziej analogiczne do wyników porównywalne operacji pionowy.<p/>Operacje obejmują &quot;przewijania w tym miejscu&quot; i &quot;prawą krawędź&quot;, aby użyć nazwy z menu uzyskanych przez kliknięcie prawym przyciskiem myszy poziomy pasek przewijania.  Oba te obliczenia przesunięcia Release candidate i wywołanie <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.<p/>Po przewinięcie do nowego przesunięcie pojęcie &quot;tutaj&quot; lub &quot;prawej krawędzi&quot; mógł ulec zmianie, ponieważ nowo cofnąć zwirtualizowanych zawartości została zmieniona wartość <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>.<p/>Przed .NET Framework 4.6.2, przewijania operacja po prostu wykorzystuje przesunięcie Release candidate, mimo że nie może być &quot;tutaj&quot; lub &quot;prawej krawędzi&quot; więcej.  Skutkuje to efektów, jak &quot;odbijania&quot; przewijania przycisku suwaka, najlepsze przedstawionymi w przykładzie. Załóżmy, że <xref:System.Windows.Controls.DataGrid?displayProperty=name> ma ExtentWidth = 1000 i szerokość = 200.  Przewiń do &quot;prawą krawędź&quot; Release candidate używa przesunięcie 1000 – 200 = 800.  Podczas przewijania, do tego przesunięcia, są nowe kolumny de-zwirtualizowanych; Załóżmy, że są one bardzo szeroki, tak aby <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> zmiany do 2000.  Przewijania kończy HorizontalOffset = 800 i przycisku suwaka &quot;odbija&quot; do pobliżu środka paska przewijania - dokładnie w 800/2000 = 40%.<p/>Zmiana jest ponownie obliczyć nowego przesunięcie Release candidate, gdy ta sytuacja występuje i spróbuj ponownie. (Jest to, jak przewijanie działa już.) <p/>Zmiana daje bardziej przewidywalna i intuicyjnym środowisku pracy użytkownika końcowego, ale także mogą wpłynąć na dowolną aplikację, która jest zależna od dokładna wartość <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> po przewijać poziomej, czy wywołana przez użytkownika końcowego lub przez jawne wywołanie <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>.|
|Sugestia|Aplikację, która używa wartości prognozowanej na <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> powinna zostać zmieniona można pobrać wartość rzeczywista (i wartość <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name>) po przewijania poziomego, które mogą ulec zmianie <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> z powodu cofnięcia wirtualizacji.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|

