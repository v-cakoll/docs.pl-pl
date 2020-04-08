---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888140"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia

A <xref:System.Windows.Forms.DataGridView> pokazuje teraz tekst i etykietki błędów komórki po umieszczeniu wskaźnika myszy i wybraniu za pomocą klawiatury. Jeśli etykietka narzędzia jest <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> wyświetlana, zdarzenie nie jest wywoływane.

#### <a name="change-description"></a>Zmień opis

Przed .NET Core 3.1, <xref:System.Windows.Forms.DataGridView> a, który miał <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> ustawioną właściwość, aby `true` wyświetlić etykietkę narzędzia dla tekstu komórki i błędy, gdy komórka została naniesione przez mysz. Etykietki narzędzi nie były wyświetlane, gdy komórka została wybrana za pomocą klawiatury (na przykład za pomocą klawisza Tab, klawiszy skrótów lub nawigacji strzałką). Jeśli użytkownik edytował komórkę, a <xref:System.Windows.Forms.DataGridView> następnie, gdy był jeszcze w trybie edycji, najechał kursorem na komórkę, która nie miała ustawionego <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> właściwości, <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie zostało podniesione w celu sformaowania tekstu komórki do wyświetlenia w komórce.

Aby spełnić standardy ułatwień dostępu, począwszy od <xref:System.Windows.Forms.DataGridView> .NET <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> Core `true` 3.1, a, który ma właściwość ustawioną na wyświetla etykietki dla tekstu komórki i błędy nie tylko po umieszczeniu komórki, ale także wtedy, gdy jest zaznaczona za pomocą klawiatury. W wyniku tej zmiany <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie *nie* jest wywoływane, gdy <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> komórki, które nie <xref:System.Windows.Forms.DataGridView> mają zestawu właściwości są najechane, gdy jest w trybie edycji. Zdarzenie nie jest wywoływane, ponieważ zawartość aktywowanej komórki jest wyświetlana jako etykietka narzędzia, a nie wyświetlana w komórce.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.1

#### <a name="recommended-action"></a>Zalecana akcja

Refaktoryzuje dowolny <xref:System.Windows.Forms.DataGridView.CellFormatting> kod, <xref:System.Windows.Forms.DataGridView> który zależy od zdarzenia, gdy jest w trybie edycji.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
