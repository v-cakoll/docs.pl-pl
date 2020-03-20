---
title: 'Porady: włączanie funkcji AutoComplete w formantach ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
ms.openlocfilehash: 18b17aaea9d2354c03bb43f3fdd8d3779697cf58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142021"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Porady: włączanie funkcji AutoComplete w formantach ToolStrip w formularzach systemu Windows
Poniższa procedura łączy <xref:System.Windows.Forms.ToolStripLabel> a <xref:System.Windows.Forms.ToolStripComboBox> z a, który można upuścić w dół, aby wyświetlić listę elementów, takich jak ostatnio odwiedzone witryny sieci Web. Jeśli użytkownik wpisuje znak, który pasuje do pierwszego znaku jednego z elementów na liście, element jest natychmiast wyświetlany.  
  
> [!NOTE]
> Automatyczne uzupełnianie `ToolStrip` działa z elementami sterującymi w <xref:System.Windows.Forms.ComboBox> taki <xref:System.Windows.Forms.TextBox>sam sposób, jak z tradycyjnymi elementami sterującymi, takimi jak i .  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Aby włączyć autouzupełnianie w formancie ToolStrip  
  
1. Utwórz <xref:System.Windows.Forms.ToolStrip> formant i dodaj do niej elementy.  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2. Ustaw <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> właściwość etykiety i pola kombi tak, aby <xref:System.Windows.Forms.ToolStripItemOverflow.Never> lista była zawsze dostępna niezależnie od rozmiaru formularza.  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3. Dodaj wyrazy do kolekcji Elementy formantu. <xref:System.Windows.Forms.ToolStripComboBox>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Ustaw <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> właściwość pola kombi <xref:System.Windows.Forms.AutoCompleteMode.Append>na .  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Ustaw <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> właściwość pola kombi <xref:System.Windows.Forms.AutoCompleteSource.ListItems>na .  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [ToolStrip — Informacje o formancie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip — Architektura formantu](toolstrip-control-architecture.md)
- [Podsumowanie informacji o technologii formantów ToolStrip](toolstrip-technology-summary.md)
