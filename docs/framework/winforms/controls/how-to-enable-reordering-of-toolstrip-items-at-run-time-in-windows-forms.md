---
title: 'Porady: włączenie zmiany kolejności elementów ToolStrip w czasie wykonywania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
ms.openlocfilehash: 44b52bf997819f090569d08eb395d8af18f61370
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745476"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Porady: włączenie zmiany kolejności elementów ToolStrip w czasie wykonywania w formularzach systemu Windows
Można umożliwić użytkownikowi zmianę rozmieszczenia formantów <xref:System.Windows.Forms.ToolStripItem> w <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Aby włączyć ponowne rozmieszczanie elementu ToolStripItem w czasie wykonywania  
  
- Ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> na `true`. Domyślnie <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> jest `false`.  
  
     W czasie wykonywania użytkownik ma wciśnięty klawisz ALT i lewy przycisk myszy, aby przeciągnąć <xref:System.Windows.Forms.ToolStripItem> do innej lokalizacji na <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip, kontrolka — architektura](toolstrip-control-architecture.md)
- [ToolStrip — podsumowanie informacji o technologii](toolstrip-technology-summary.md)
