---
title: 'Instrukcje: Zmienianie odstępów i wyrównania elementów ToolStrip w formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 2c9c60a3bfd78b7111b9cdff6a791d70c8e53c82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685066"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Instrukcje: Zmienianie odstępów i wyrównania elementów ToolStrip w formularzach Windows Forms
<xref:System.Windows.Forms.ToolStrip> Kontroli w pełni obsługuje układ funkcje, takie jak rozmiary, odstępy między <xref:System.Windows.Forms.ToolStripItem> formantów względem siebie, rozmieszczenie kontrolek w <xref:System.Windows.Forms.ToolStrip>i odstępy kontroli względem <xref:System.Windows.Forms.ToolStrip>.  
  
 Ponieważ wartość domyślną <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość `true`, formanty mają rozmiar automatycznie, chyba że <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Aby ręcznie rozmiar elementu ToolStripItem  
  
1.  Ustaw <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość `false` skojarzonego formantu.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Size%2A> właściwości w sposób skojarzonych z nim <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Aby ustawić odstępy elementu ToolStripItem  
  
1.  Wstawianie odpowiednie wartości, w pikselach, <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości skojarzonego formantu.  
  
     Wartości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwość Określ odstępy między elementem a sąsiadujących elementów w następującej kolejności: Po lewej stronie, górnej, prawej strony i dolnej.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Aby wyrównać elementu ToolStripItem w prawą stronę ToolStrip  
  
1.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> właściwość <xref:System.Windows.Forms.ToolStripItemAlignment.Right> skojarzonego formantu. Domyślnie <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> ustawiono <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, która wyrównuje kontrolki do lewej części <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Aby rozmieścić elementy paska narzędzi na pasku narzędzi  
  
-   Ustaw <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> właściwości na wartość <xref:System.Windows.Forms.ToolStripLayoutStyle> przewidzianą.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [ToolStrip, kontrolka — architektura](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [ToolStrip — podsumowanie informacji o technologii](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
