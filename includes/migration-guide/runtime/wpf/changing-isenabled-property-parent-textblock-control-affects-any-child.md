---
ms.openlocfilehash: 735278848cb7399e414a128afc650a0a1f882337
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857561"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Zmiana właściwości IsEnabled nadrzędnego formantu TextBlock wpływa na wszystkie formanty podrzędne

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.6.2, zmiana <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> właściwości <xref:System.Windows.Controls.TextBlock?displayProperty=name> nadrzędnego formantu wpływa na wszelkie formanty <xref:System.Windows.Controls.TextBlock?displayProperty=name> podrzędne (takie jak hiperłącza i przyciski) formantu. W .NET Framework 4.6.1 i wcześniejszych <xref:System.Windows.Controls.TextBlock?displayProperty=name> wersjach formanty wewnątrz <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> nie <xref:System.Windows.Controls.TextBlock?displayProperty=name> zawsze odzwierciedla stan właściwości nadrzędnego.|
|Sugestia|Brak. Ta zmiana jest zgodna z oczekiwanym <xref:System.Windows.Controls.TextBlock?displayProperty=name> zachowaniem formanty wewnątrz formantu.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
