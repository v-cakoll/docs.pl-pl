---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567374"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Zdarzenie CellFormatting nie zostało zgłoszone, jeśli jest wyświetlana etykietka narzędzia

<xref:System.Windows.Forms.DataGridView> teraz wyświetla tekst i etykietki narzędzia błędów w komórce, gdy są przesuwane za pomocą myszy i wybierane za pomocą klawiatury. Jeśli zostanie wyświetlona etykietka narzędzia, zdarzenie <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> nie zostanie zgłoszone.

#### <a name="change-description"></a>Zmień opis

Przed uruchomieniem programu .NET Core 3,1 <xref:System.Windows.Forms.DataGridView>, który miał Właściwość <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> ustawioną na `true`, wykazał etykietkę narzędzia dla tekstu i błędów komórki, gdy komórka została zatrzymana przez mysz. Etykietki narzędzi nie były wyświetlane, gdy komórka została wybrana za pośrednictwem klawiatury (na przykład za pomocą klawisza Tab, klawiszy skrótów lub nawigacji strzałek). Jeśli użytkownik edytował komórkę, a następnie, gdy <xref:System.Windows.Forms.DataGridView> był nadal w trybie edycji, przesuwa się nad komórką, która nie ma ustawionej właściwości <xref:System.Windows.Forms.DataGridViewCell.ToolTipText>, zdarzenie <xref:System.Windows.Forms.DataGridView.CellFormatting> zostało podniesione do formatowania tekstu komórki do wyświetlania w komórce.

Aby spełnić standardy dostępności, począwszy od platformy .NET Core 3,1, <xref:System.Windows.Forms.DataGridView>, która ma właściwość <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> ustawioną na `true` wyświetla etykietki narzędzi dla tekstu i błędów w komórce, nie tylko wtedy, gdy komórka jest aktywowany, ale również gdy jest zaznaczona za pomocą klawiatury. W związku z tą zmianą zdarzenie <xref:System.Windows.Forms.DataGridView.CellFormatting> *nie* jest zgłaszane, gdy komórki, które nie mają ustawionej właściwości <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> są przesuwane, gdy <xref:System.Windows.Forms.DataGridView> jest w trybie edycji. Zdarzenie nie zostało zgłoszone, ponieważ zawartość przesuwanej komórki jest pokazywana jako etykietka narzędzia, a nie wyświetlana w komórce.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,1

#### <a name="recommended-action"></a>Zalecane działanie

Refaktoryzacja dowolnego kodu, który zależy od zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting>, podczas gdy <xref:System.Windows.Forms.DataGridView> jest w trybie edycji.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Nie wykrywalne za pośrednictwem analizy interfejsu API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
