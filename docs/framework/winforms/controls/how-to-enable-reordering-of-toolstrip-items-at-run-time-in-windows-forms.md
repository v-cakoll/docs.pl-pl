---
title: 'Instrukcje: Włączanie zmiany kolejności elementów ToolStrip w czasie wykonywania w formularzach Windows Forms'
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
ms.openlocfilehash: daff9d6d351db514d552225853f977775f8e3204
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220412"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Instrukcje: Włączanie zmiany kolejności elementów ToolStrip w czasie wykonywania w formularzach Windows Forms
Można włączyć użytkownika do zmiany rozmieszczenia <xref:System.Windows.Forms.ToolStripItem> formantów na <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Aby włączyć rozmieszczania ToolStripItem w czasie wykonywania  
  
-   Ustaw <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> właściwość `true`. Domyślnie <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> jest `false`.  
  
     W czasie wykonywania, użytkownik posiada naciśnięty klawisz ALT i lewego przycisku myszy przeciągnij <xref:System.Windows.Forms.ToolStripItem> do innej lokalizacji na <xref:System.Windows.Forms.ToolStrip>.  
  
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
