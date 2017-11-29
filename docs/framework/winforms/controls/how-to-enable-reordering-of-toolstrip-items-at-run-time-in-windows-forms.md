---
title: "Porady: włączenie zmiany kolejności elementów ToolStrip w czasie wykonywania w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 73ea6d3615780c8def31b7dbdcf870020a106e80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Informacje o formancie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip — architektura formantu](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Podsumowanie technologii formantów ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
