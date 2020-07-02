---
ms.openlocfilehash: 395463225e3c1f1d168dd019ea75966ad54e5a8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621262"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Zmiana właściwości IsEnabled elementu nadrzędnego formantu TextBlock ma wpływ na wszystkie kontrolki podrzędne

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4.6.2, zmiana <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> właściwości elementu nadrzędnego <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> formantu ma wpływ na wszystkie kontrolki podrzędne (takie jak hiperłącza i przyciski) <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> formantu. W .NET Framework 4.6.1 i starszych wersji, formanty wewnątrz <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> nie zawsze odzwierciedlają stan <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> właściwości <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> elementu nadrzędnego.

#### <a name="suggestion"></a>Sugestia

Brak. Ta zmiana jest zgodna z oczekiwanym zachowaniem formantów wewnątrz <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> kontrolki.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
