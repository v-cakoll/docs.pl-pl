---
ms.openlocfilehash: 38dd0b33202b8e8f1708ebec689333bd5367c93f
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760681"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Zmiana właściwości IsEnabled elementu nadrzędnego formant TextBlock wpływa formanty podrzędne

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2, zmieniając <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> właściwości elementu nadrzędnego <xref:System.Windows.Controls.TextBlock?displayProperty=name> kontroli ma wpływ na formanty podrzędne (takie jak hiperłącza i przyciski) z <xref:System.Windows.Controls.TextBlock?displayProperty=name> kontroli. W .NET Framework 4.6.1 i wcześniejszych wersjach, kontroluje wewnątrz <xref:System.Windows.Controls.TextBlock?displayProperty=name> nie zawsze odzwierciedlają stan <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> właściwość <xref:System.Windows.Controls.TextBlock?displayProperty=name> nadrzędnej.|
|Sugestia|Brak. Ta zmiana jest zgodny z oczekiwane zachowanie formanty <xref:System.Windows.Controls.TextBlock?displayProperty=name> kontroli.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

