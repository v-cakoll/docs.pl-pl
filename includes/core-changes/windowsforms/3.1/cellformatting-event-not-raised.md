---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721671"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Zdarzenie CellFormatting nie zostało zgłoszone, jeśli jest wyświetlana etykietka narzędzia

<xref:System.Windows.Forms.DataGridView>Po umieszczeniu wskaźnika myszy i wybraniu za pośrednictwem klawiatury jest teraz wyświetlana etykietka tekstowa i błędów w komórce. Jeśli zostanie wyświetlona etykietka narzędzia, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzenie nie zostanie zgłoszone.

#### <a name="change-description"></a>Zmień opis

Przed platformą .NET Core 3,1, <xref:System.Windows.Forms.DataGridView> która ma <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> ustawioną właściwość, aby była `true` wyświetlana etykietka narzędzia dla tekstu i błędów komórki, gdy komórka została aktywowana przez mysz. Etykietki narzędzi nie były wyświetlane, gdy komórka została wybrana za pośrednictwem klawiatury (na przykład za pomocą klawisza Tab, klawiszy skrótów lub nawigacji strzałek). Jeśli użytkownik edytował komórkę, a następnie, gdy <xref:System.Windows.Forms.DataGridView> był nadal w trybie edycji, przesuwa się nad komórką, która nie ma <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> ustawionej właściwości, <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie zostało wywołane w celu sformatowania tekstu komórki na potrzeby wyświetlania w komórce.

Aby spełnić standardy dostępności, począwszy od platformy .NET Core 3,1, <xref:System.Windows.Forms.DataGridView> która ma <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> ustawioną właściwość `true` pokazującą etykietki narzędzi dla tekstu i błędów w komórce, nie tylko wtedy, gdy komórka jest aktywowany, ale również gdy jest zaznaczona za pomocą klawiatury. W związku z tą zmianą <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie *nie* jest zgłaszane, gdy komórki, które nie mają <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> ustawionej właściwości są przesuwane, gdy <xref:System.Windows.Forms.DataGridView> jest w trybie edycji. Zdarzenie nie zostało zgłoszone, ponieważ zawartość przesuwanej komórki jest pokazywana jako etykietka narzędzia, a nie wyświetlana w komórce.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,1

#### <a name="recommended-action"></a>Zalecana akcja

Refaktoryzacja dowolnego kodu, który zależy od zdarzenia, <xref:System.Windows.Forms.DataGridView.CellFormatting> podczas gdy <xref:System.Windows.Forms.DataGridView> jest w trybie edycji.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
