---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567374"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia

A <xref:System.Windows.Forms.DataGridView> pokazuje teraz tekst komórki i etykietki narzędzi błędów po najechaniu kursorem myszy i wybraniu za pomocą klawiatury. Jeśli zostanie wyświetlona <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> etykietka narzędzia, zdarzenie nie zostanie podniesione.

#### <a name="change-description"></a>Zmień opis

Przed .NET Core 3.1, <xref:System.Windows.Forms.DataGridView> który <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> miał `true` właściwość ustawić, aby pokazał etykietkę narzędzia dla komórki tekstu i błędów, gdy komórka została unosząca się kursorem myszy. Etykietki narzędzi nie były wyświetlane, gdy komórka została wybrana za pomocą klawiatury (na przykład za pomocą klawisza Tab, klawiszy skrótów lub nawigacji po strzałkach). Jeśli użytkownik edytował komórkę, a <xref:System.Windows.Forms.DataGridView> następnie, gdy był jeszcze w trybie edycji, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> najechał <xref:System.Windows.Forms.DataGridView.CellFormatting> na komórkę, która nie miała ustawionej właściwości, zdarzenie zostało podniesione w celu sformatowania tekstu komórki do wyświetlenia w komórce.

Aby spełnić standardy ułatwień dostępu, począwszy <xref:System.Windows.Forms.DataGridView> od <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> .NET `true` Core 3.1, a, który ma właściwość ustawioną na pokazuje etykietki narzędzi dla tekstu komórki i błędy nie tylko po umieszczeniu komórki, ale także wtedy, gdy jest zaznaczona za pomocą klawiatury. W wyniku tej zmiany <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie *nie* jest wywoływane, gdy <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> komórki, które nie <xref:System.Windows.Forms.DataGridView> mają ustawionej właściwości są unoszące się podczas trybu edycji. Zdarzenie nie jest wywoływane, ponieważ zawartość unoszącej się komórki jest wyświetlana jako etykietka narzędzia, a nie wyświetlana w komórce.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.1

#### <a name="recommended-action"></a>Zalecana akcja

Refaktoryzuj dowolny kod, który zależy od <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenia, <xref:System.Windows.Forms.DataGridView> gdy jest w trybie edycji.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Nie wykrywalne za pomocą analizy Interfejsu API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
