---
ms.openlocfilehash: eb3cfdfd39444536f423b65166a3413db67a0e01
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802934"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Element przewijania płaskiej listy elementów różnych wysokość pikseli

|   |   |
|---|---|
|Szczegóły|Gdy <xref:System.Windows.Controls.ItemsControl?displayProperty=name> wyświetlająca kolekcję przy użyciu wirtualizacji (<code>IsVirtualizing=true</code>) i element przewijania (<code>ScrollUnit=Item</code>), i gdy formant, który przewija widok do wyświetlania elementów, których wysokość w pikselach, który różni się od jego sąsiadami <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> wykonuje iterację na wszystkich elementy w kolekcji. Interfejs użytkownika nie odpowiada podczas tej iteracji; Jeśli kolekcja jest duży, to może być uważane za zawieszenie. Iteracji odbywa się w innych okolicznościach, nawet w poprzednich wersjach systemu .NET Framework. Na przykład występuje podczas przewijania pikseli (<code>ScrollUnit=Pixel</code>) razie napotkania o różnych pikseli wysokości i elementu podczas przewijania elementu danych hierarchicznych (takie jak <xref:System.Windows.Controls.TreeView?displayProperty=name> lub <xref:System.Windows.Controls.ItemsControl?displayProperty=name> grupowanie włączone) po napotkaniu elementu z inną liczbę elementów podrzędnych, niż jego sąsiadami. W przypadku wysokość pikseli przesuwania elementów i w różnych iteracji została wprowadzona w programie .NET Framework 4.6.1 do usuwania błędów w układzie danych hierarchicznych.  Nie jest wymagana, jeśli dane są płaskie (Brak hierarchii) i .NET Framework 4.6.2 nie działa on w takiej sytuacji.|
|Sugestia|Jeśli iteracji, która występuje w programie .NET Framework 4.6.1, ale nie we wcześniejszych wersjach — oznacza to, jeśli <xref:System.Windows.Controls.ItemsControl?displayProperty=name> ma element przewijania płaska lista z elementami o różnych pikseli wysokości — istnieją dwa środki zaradcze:<ol><li>Zainstaluj program .NET Framework 4.6.2.</li><li>Zainstaluj poprawkę HR 1605 programu .NET Framework 4.6.1.</li></ol>|
|Scope|Mały|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|

