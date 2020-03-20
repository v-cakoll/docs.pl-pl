---
ms.openlocfilehash: 3a82822aae281ea7e873ba649f05b1d68686ec69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997685"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Przewijanie płaskiej listy z elementami o różnej wysokości pikseli

|   |   |
|---|---|
|Szczegóły|Gdy <xref:System.Windows.Controls.ItemsControl?displayProperty=name> wyświetla kolekcję przy<code>IsVirtualizing=true</code>użyciu wirtualizacji<code>ScrollUnit=Item</code>( ) i przewijanie elementu ( ), a gdy formant <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> przewija się, aby wyświetlić element, którego wysokość w pikselach różni się od jego sąsiadów, iteruje wszystkie elementy w kolekcji. Interfejs użytkownika nie odpowiada podczas tej iteracji; jeśli kolekcja jest duża, może to być postrzegane jako powiesić. Iteracja występuje w innych okolicznościach, nawet w poprzednich wydaniach programu .NET Framework. Na przykład występuje, gdy pixel-scrolling (<code>ScrollUnit=Pixel</code>) po napotkaniu elementu o różnej wysokości pikseli i gdy element przewijania danych hierarchicznych (takich jak <xref:System.Windows.Controls.TreeView?displayProperty=name> lub <xref:System.Windows.Controls.ItemsControl?displayProperty=name> z grupowania włączone) po napotkaniu elementu z inną liczbą elementów podrzędnych niż jego sąsiadów. W przypadku przewijania elementów i wysokości różnych pikseli iteracja została wprowadzona w .NET Framework 4.6.1, aby naprawić błędy w układzie danych hierarchicznych.  Nie jest potrzebne, jeśli dane są płaskie (bez hierarchii) i .NET Framework 4.6.2 nie robi tego w takim przypadku.|
|Sugestia|Jeśli iteracja występuje w .NET Framework 4.6.1, ale nie <xref:System.Windows.Controls.ItemsControl?displayProperty=name> we wcześniejszych wersjach - to znaczy, jeśli jest element- przewijanie płaskiej listy z elementami o różnej wysokości pikseli - istnieją dwa środki zaradcze:<ol><li>Zainstaluj program .NET Framework 4.6.2.</li><li>Zainstaluj poprawkę HR 1605 dla platformy .NET Framework 4.6.1.</li></ol>|
|Zakres|Mały|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
