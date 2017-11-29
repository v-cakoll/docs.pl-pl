---
title: "Porady: zmienianie wyglądu tekstu i obrazów elementów ToolStrip w formularzach systemu Windows"
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
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d926ce74db9723b6248dbb123513ca38d4adb1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Porady: zmienianie wyglądu tekstu i obrazów elementów ToolStrip w formularzach systemu Windows
Można kontrolować, czy tekst i obrazy są wyświetlane na <xref:System.Windows.Forms.ToolStripItem> i jak są wyrównane względem siebie i <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Aby zdefiniować, co jest wyświetlane na element ToolStripItem  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na żądaną wartość. Możliwości są `Image`, `ImageAndText`, `None`, i `Text`. Wartość domyślna to `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Wyrównanie tekstu na element ToolStripItem  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> na żądaną wartość. Możliwości są dowolną kombinację góry, drugie i u dołu po lewej, wyśrodkowanie i po prawej. Wartość domyślna to `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Aby wyrównać obraz na element ToolStripItem  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> na żądaną wartość. Możliwości są dowolną kombinację góry, drugie i u dołu po lewej, wyśrodkowanie i po prawej. Wartość domyślna to `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Aby zdefiniować sposób wyświetlania ToolStripItem tekst i obrazy względem siebie  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> na żądaną wartość. Możliwości są `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, i `TextBeforeImage`. Wartość domyślna to `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStrip>  
 [Informacje o formancie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip — architektura formantu](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Podsumowanie technologii formantów ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
