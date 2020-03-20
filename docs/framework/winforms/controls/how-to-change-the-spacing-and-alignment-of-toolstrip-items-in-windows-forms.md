---
title: 'Jak: Zmiana odstępów i wyrównania elementów Paska narzędzi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182229"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Porady: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows
Formant <xref:System.Windows.Forms.ToolStrip> w pełni obsługuje funkcje układu, <xref:System.Windows.Forms.ToolStripItem> takie jak zmiana rozmiaru, odstępy <xref:System.Windows.Forms.ToolStrip>formantów względem siebie, rozmieszczenie formantów na , i odstępy formantów względem <xref:System.Windows.Forms.ToolStrip>.  
  
 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> Ponieważ domyślną wartością `true`właściwości jest , formanty <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> są `false`zmieniane automatycznie, chyba że właściwość zostanie ustawiona na .  
  
### <a name="to-manually-size-a-toolstripitem"></a>Aby ręcznie rozmiar ToolStripItem  
  
1. Ustaw <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość `false` na skojarzony formant.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. Ustaw <xref:System.Windows.Forms.ToolStripItem.Size%2A> właściwość w odpowiedni sposób <xref:System.Windows.Forms.ToolStripItem>dla skojarzonego .  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Aby ustawić odstępy między narzędziami ToolStripItem  
  
1. Wstaw żądane wartości w pikselach do <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości skojarzonego formantu.  
  
     Wartości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości określają odstępy między elementem a sąsiednimi elementami w następującej kolejności: Lewy, U góry, Prawy i Dolny.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Aby wyrównać narzędzie ToolStripItem do prawej strony paska narzędzi  
  
1. Ustaw <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> właściwość <xref:System.Windows.Forms.ToolStripItemAlignment.Right> na skojarzony formant. Domyślnie <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> jest ustawiona na <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, która wyrównuje formanty do lewej strony pliku <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Aby rozmieścić elementy Paska narzędzi na pasie narzędziowym  
  
- Ustaw <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> właściwość na <xref:System.Windows.Forms.ToolStripLayoutStyle> żądaną wartość.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip — Informacje o formancie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip — Architektura formantu](toolstrip-control-architecture.md)
- [Podsumowanie informacji o technologii formantów ToolStrip](toolstrip-technology-summary.md)
