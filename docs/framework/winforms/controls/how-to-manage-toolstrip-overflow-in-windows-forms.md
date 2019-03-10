---
title: 'Instrukcje: Zarządzanie przepełnieniem elementu ToolStrip w formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 53f610a728925d454a8833a49e705818f027aec5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707277"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Instrukcje: Zarządzanie przepełnieniem elementu ToolStrip w formularzach Windows Forms

Gdy wszystkie elementy na <xref:System.Windows.Forms.ToolStrip> formantu nie mieszczą się w wyznaczonym miejscu, można włączyć funkcji przepełnienie w <xref:System.Windows.Forms.ToolStrip> i określić zachowanie przepełnienie konkretnych <xref:System.Windows.Forms.ToolStripItem>s.

Po dodaniu <xref:System.Windows.Forms.ToolStripItem>s, które wymagają więcej miejsca niż jest przydzielone <xref:System.Windows.Forms.ToolStrip> danego formularza bieżący rozmiar <xref:System.Windows.Forms.ToolStripOverflowButton> automatycznie pojawia się na <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.ToolStripOverflowButton> Pojawi się, i włączone przepełnienie elementy zostaną przeniesione do menu rozwijanego, przepełnieniu. Dzięki temu można dostosować i ustalić ich priorytety jak Twoje <xref:System.Windows.Forms.ToolStrip> elementy odpowiednio dostosowują się do różnych rozmiarów. Możesz również zmienić wygląd swoich elementów, gdy znajdą się one do przeciążenia przy użyciu <xref:System.Windows.Forms.ToolStripItem.Placement%2A> i <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> właściwości i <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> zdarzeń. Jeśli w czasie projektowania lub wykonywania, Powiększ bardziej formularza <xref:System.Windows.Forms.ToolStripItem>s mogą być wyświetlane w głównym <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripOverflowButton> nawet może zniknąć, dopóki nie można zmniejszyć rozmiar formularza.

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>Aby włączyć przepełnienie w formancie ToolStrip

- Upewnij się, że <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> nie ustawiono właściwości `false` dla <xref:System.Windows.Forms.ToolStrip>. Wartość domyślna to `True`.

     Gdy <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> jest `True` (ustawienie domyślne), <xref:System.Windows.Forms.ToolStripItem> są wysyłane do menu rozwijanego, przepełnieniu podczas zawartość <xref:System.Windows.Forms.ToolStripItem> przekracza szerokość poziomego <xref:System.Windows.Forms.ToolStrip> lub wysokości kontrolki w pionie <xref:System.Windows.Forms.ToolStrip>.

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Aby określić zachowanie przepełnienie określonych ToolStripItem

- Ustaw <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> właściwość <xref:System.Windows.Forms.ToolStripItem> na żądaną wartość. Możliwości są `Always`, `Never`, i `AsNeeded`. Wartość domyślna to `AsNeeded`.

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip, kontrolka — architektura](toolstrip-control-architecture.md)
- [ToolStrip — podsumowanie informacji o technologii](toolstrip-technology-summary.md)
