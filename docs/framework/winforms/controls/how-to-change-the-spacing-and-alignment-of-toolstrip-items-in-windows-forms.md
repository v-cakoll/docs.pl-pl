---
title: 'Instrukcje: Zmienianie odstępów i wyrównania elementów ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746562"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Porady: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows
Kontrolka <xref:System.Windows.Forms.ToolStrip> w pełni obsługuje funkcje układu, takie jak rozmiar, odstępy <xref:System.Windows.Forms.ToolStripItem> formantów względem siebie, rozmieszczenie formantów na <xref:System.Windows.Forms.ToolStrip>oraz odstępy kontrolek względem <xref:System.Windows.Forms.ToolStrip>.  
  
 Ponieważ wartość domyślna właściwości <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> jest `true`, rozmiary formantów są ustawiane automatycznie, o ile Właściwość <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> nie zostanie ustawiona na `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Aby ręcznie zmienić rozmiar elementu ToolStripItem  
  
1. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> na `false` dla skojarzonej kontrolki.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Size%2A> w odpowiedni sposób dla <xref:System.Windows.Forms.ToolStripItem>skojarzonych.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Aby ustawić odstępy elementu ToolStripItem  
  
1. Wstaw odpowiednie wartości (w pikselach) do właściwości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> skojarzonej kontrolki.  
  
     Wartości właściwości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> określają odstępy między elementem i sąsiadującymi elementami w tej kolejności: od lewej, do góry, do prawej i u dołu.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Aby wyrównać Element ToolStripItem do prawej strony elementu ToolStrip  
  
1. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> na <xref:System.Windows.Forms.ToolStripItemAlignment.Right> dla skojarzonej kontrolki. Domyślnie <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> jest ustawiona na <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, co oznacza, że kontrolki są wyrównane do lewej strony <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Aby rozmieścić elementy ToolStrip na pasku narzędzi  
  
- Ustaw właściwość <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> na wartość <xref:System.Windows.Forms.ToolStripLayoutStyle>, która ma zostać wybrana.  
  
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
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip, kontrolka — architektura](toolstrip-control-architecture.md)
- [ToolStrip — podsumowanie informacji o technologii](toolstrip-technology-summary.md)
