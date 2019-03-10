---
title: 'Instrukcje: Zmienianie wyglądu ToolStrip tekstu i obrazów w formularzach Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: cd15e581e646f53ed56af654917c7543bf18617e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705405"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Instrukcje: Zmienianie wyglądu ToolStrip tekstu i obrazów w formularzach Windows Forms
Można kontrolować, czy tekst i obrazy są wyświetlane na <xref:System.Windows.Forms.ToolStripItem> i jak są wyrównane względem siebie i <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Aby zdefiniować, co jest wyświetlane na elementu ToolStripItem  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości na żądaną wartość. Możliwości są `Image`, `ImageAndText`, `None`, i `Text`. Wartość domyślna to `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Aby wyrównać tekst na elementu ToolStripItem  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> właściwości na żądaną wartość. Możliwości są dowolną kombinację początku, środka i na dole z lewej strony, wyśrodkowanie i po prawej stronie. Wartość domyślna to `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Aby wyrównać obrazu elementu ToolStripItem  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> właściwości na żądaną wartość. Możliwości są dowolną kombinację początku, środka i na dole z lewej strony, wyśrodkowanie i po prawej stronie. Wartość domyślna to `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Aby zdefiniować sposób wyświetlania ToolStripItem tekst i obrazy względem siebie  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> właściwości na żądaną wartość. Możliwości są `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, i `TextBeforeImage`. Wartość domyślna to `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ToolStrip>
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip, kontrolka — architektura](toolstrip-control-architecture.md)
- [ToolStrip — podsumowanie informacji o technologii](toolstrip-technology-summary.md)
