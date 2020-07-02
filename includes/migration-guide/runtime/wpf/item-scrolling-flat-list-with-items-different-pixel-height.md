---
ms.openlocfilehash: fbf3c0c8f1d11f9f5997a4d1027242c4710c7107
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621829"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Element — przewijanie płaskiej listy z elementami o różnej wysokości pikseli

#### <a name="details"></a>Szczegóły

Gdy <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> zostanie wyświetlona kolekcja używająca wirtualizacji ( <code>IsVirtualizing=true</code> ) i przewijania elementów ( <code>ScrollUnit=Item</code> ) i gdy kontrolka przewinie się w celu wyświetlenia elementu, którego wysokość w pikselach różni się od sąsiadów, <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> wykonuje iterację wszystkich elementów w kolekcji. Interfejs użytkownika nie odpowiada podczas tej iteracji; Jeśli kolekcja jest duża, może to być postrzegane jako zawieszenie. Iteracja występuje w innych sytuacjach, nawet w poprzednich wersjach .NET Framework. Na przykład występuje w przypadku przewijania do pikseli () w przypadku <code>ScrollUnit=Pixel</code> napotkania elementu o różnej wysokości pikseli, a po przejściu danych hierarchicznych (takich jak <xref:System.Windows.Controls.TreeView?displayProperty=fullName> lub <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> z włączonym grupowaniem) w przypadku napotkania elementu z inną liczbą elementów podrzędnych niż jego sąsiedzi. W przypadku przewijania elementów i o różnej wysokości pikseli iteracja została wprowadzona w .NET Framework 4.6.1, aby naprawić błędy w układzie danych hierarchicznych.  Nie jest to konieczne, jeśli dane są płaskie (bez hierarchii), a .NET Framework 4.6.2 nie robi w tym przypadku.

#### <a name="suggestion"></a>Sugestia

Jeśli iteracja występuje w .NET Framework 4.6.1, ale nie w starszych wersjach — to oznacza, że jeśli <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> element jest przewijaną listą z elementami o różnej wysokości pikseli — istnieją dwie metody zaradcze:<ol><li>Zainstaluj .NET Framework 4.6.2.</li><li>Zainstaluj poprawkę HR 1605 dla .NET Framework 4.6.1.</li></ol>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
