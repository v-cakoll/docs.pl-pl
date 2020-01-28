---
title: 'Instrukcje: Zmienianie wyglądu tekstu i obrazów elementu ToolStrip'
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
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746598"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Porady: zmienianie wyglądu tekstu i obrazów elementów ToolStrip w formularzach systemu Windows
Można kontrolować, czy tekst i obrazy są wyświetlane na <xref:System.Windows.Forms.ToolStripItem> oraz jak są wyrównane względem siebie i <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Aby zdefiniować elementy, które są wyświetlane w elementach ToolStripItem  
  
- Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na żądaną wartość. Możliwości są `Image`, `ImageAndText`, `None`i `Text`. Wartość domyślna to `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Aby wyrównać tekst na ToolStripItem  
  
- Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> na żądaną wartość. Możliwości są dowolną kombinacją górnego, środkowego i dolnego z lewej, środkową i prawą. Wartość domyślna to `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Aby wyrównać obraz na element ToolStripItem  
  
- Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> na żądaną wartość. Możliwości są dowolną kombinacją górnego, środkowego i dolnego z lewej, środkową i prawą. Wartość domyślna to `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Aby określić sposób wyświetlania tekstu i obrazów elementu ToolStripItem względem siebie  
  
- Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> na żądaną wartość. Możliwe są `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`i `TextBeforeImage`. Wartość domyślna to `ImageBeforeText`.  
  
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
