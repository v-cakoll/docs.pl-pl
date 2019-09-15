---
ms.openlocfilehash: 3a82822aae281ea7e873ba649f05b1d68686ec69
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997685"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Element — przewijanie płaskiej listy z elementami o różnej wysokości pikseli

|   |   |
|---|---|
|Szczegóły|Gdy zostanie wyświetlona kolekcja używająca<code>IsVirtualizing=true</code>wirtualizacji () i elementu do<code>ScrollUnit=Item</code>przewijania (), a gdy kontrolka przewinie się, aby wyświetlić element, którego wysokość <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> w pikselach różni się od sąsiadów, iteracje wszystkich <xref:System.Windows.Controls.ItemsControl?displayProperty=name> elementy w kolekcji. Interfejs użytkownika nie odpowiada podczas tej iteracji; Jeśli kolekcja jest duża, może to być postrzegane jako zawieszenie. Iteracja występuje w innych sytuacjach, nawet w poprzednich wersjach .NET Framework. Na przykład występuje w przypadku przewijania do pikseli (<code>ScrollUnit=Pixel</code>) w przypadku napotkania elementu o różnej wysokości pikseli, a po przejściu danych hierarchicznych (takich <xref:System.Windows.Controls.TreeView?displayProperty=name> jak lub <xref:System.Windows.Controls.ItemsControl?displayProperty=name> z włączonym grupowaniem) po napotkaniu elementu z inna liczba elementów podrzędnych niż jej sąsiedzi. W przypadku przewijania elementów i o różnej wysokości pikseli iteracja została wprowadzona w .NET Framework 4.6.1, aby naprawić błędy w układzie danych hierarchicznych.  Nie jest to konieczne, jeśli dane są płaskie (bez hierarchii), a .NET Framework 4.6.2 nie robi w tym przypadku.|
|Sugestia|Jeśli iteracja występuje w .NET Framework 4.6.1, ale nie w starszych wersjach — to oznacza, że <xref:System.Windows.Controls.ItemsControl?displayProperty=name> Jeśli element jest przewijaną listą z elementami o różnej wysokości pikseli — istnieją dwie metody zaradcze:<ol><li>Zainstaluj .NET Framework 4.6.2.</li><li>Zainstaluj poprawkę HR 1605 dla .NET Framework 4.6.1.</li></ol>|
|Scope|Mały|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
