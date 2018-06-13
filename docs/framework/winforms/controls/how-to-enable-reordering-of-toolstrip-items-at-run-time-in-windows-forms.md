---
title: 'Porady: włączenie zmiany kolejności elementów ToolStrip w czasie wykonywania w formularzach systemu Windows'
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
ms.openlocfilehash: e3f4510071c83b9d1baab358d4962b54fb7361ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531625"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Porady: włączenie zmiany kolejności elementów ToolStrip w czasie wykonywania w formularzach systemu Windows
Umożliwia użytkownikowi rozmieszczanie <xref:System.Windows.Forms.ToolStripItem> formantów na <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Aby włączyć element ToolStripItem zmienianie rozmieszczenia obiektów w czasie wykonywania  
  
-   Ustaw <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> właściwości `true`. Domyślnie <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> jest `false`.  
  
     W czasie wykonywania, użytkownik posiada wciśnięty klawisz ALT i lewego przycisku myszy przeciągnij <xref:System.Windows.Forms.ToolStripItem> do innej lokalizacji na <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>  
 [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip, kontrolka — architektura](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip — podsumowanie informacji o technologii](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
