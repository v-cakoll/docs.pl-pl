---
title: 'Porady: zarządzanie przepełnieniem elementu ToolStrip'
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
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736149"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Porady: zarządzanie przepełnieniem elementu ToolStrip w formularzach systemu Windows

Gdy wszystkie elementy w formancie <xref:System.Windows.Forms.ToolStrip> nie mieszczą się w wyznaczonym miejscu, można włączyć funkcję przepełniania na <xref:System.Windows.Forms.ToolStrip> i określić zachowanie przepełnienia dla konkretnych <xref:System.Windows.Forms.ToolStripItem>s.

Po dodaniu <xref:System.Windows.Forms.ToolStripItem>s, które wymagają więcej miejsca niż jest przydzielony do <xref:System.Windows.Forms.ToolStrip> o bieżącym rozmiarze formularza, <xref:System.Windows.Forms.ToolStripOverflowButton> automatycznie pojawia się na <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.ToolStripOverflowButton> pojawia się, a elementy z obsługą przepełnienia są przenoszone do menu przepełnienie rozwijane. Umożliwia to dostosowanie i ustalanie priorytetów, jak elementy <xref:System.Windows.Forms.ToolStrip> prawidłowo dostosowują się do różnych rozmiarów. Możesz również zmienić wygląd elementów po ich przepełnieniu przy użyciu właściwości <xref:System.Windows.Forms.ToolStripItem.Placement%2A> i <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> oraz zdarzenia <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>. W przypadku powiększania formularza w czasie projektowania lub czasu wykonywania więcej <xref:System.Windows.Forms.ToolStripItem>s można wyświetlić na głównym <xref:System.Windows.Forms.ToolStrip>, a <xref:System.Windows.Forms.ToolStripOverflowButton> może nawet zniknąć do momentu zmniejszenia rozmiaru formularza.

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>Aby włączyć przepełnienie na formancie ToolStrip

- Upewnij się, że właściwość <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> nie jest ustawiona na `false` dla <xref:System.Windows.Forms.ToolStrip>. Wartość domyślna to `True`.

     Gdy <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> jest `True` (domyślnie), <xref:System.Windows.Forms.ToolStripItem> jest wysyłana do menu przepełnienia listy rozwijanej, gdy zawartość <xref:System.Windows.Forms.ToolStripItem> przekroczy szerokość <xref:System.Windows.Forms.ToolStrip> poziomej lub wysokość <xref:System.Windows.Forms.ToolStrip>pionowej.

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Aby określić zachowanie przepełnienia dla określonego elementu ToolStripItem

- Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> <xref:System.Windows.Forms.ToolStripItem> na żądaną wartość. Możliwości są `Always`, `Never`i `AsNeeded`. Wartość domyślna to `AsNeeded`.

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
