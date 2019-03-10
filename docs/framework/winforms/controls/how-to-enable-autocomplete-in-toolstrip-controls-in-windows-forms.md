---
title: 'Instrukcje: Włączanie funkcji AutoComplete w formantach ToolStrip w formularzach Windows Forms'
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
ms.openlocfilehash: 0e44b2944a24ea4201fda2f0891d74c672a64a4a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718947"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Instrukcje: Włączanie funkcji AutoComplete w formantach ToolStrip w formularzach Windows Forms
Poniższa procedura łączy <xref:System.Windows.Forms.ToolStripLabel> z <xref:System.Windows.Forms.ToolStripComboBox> który można upuszczać w dół do wyświetlenia listy elementów, takich jak ostatnio odwiedzane witryny sieci Web. Jeśli użytkownik wpisze znak, który pasuje do pierwszego znaku, jednego z elementów na liście, element natychmiast jest wyświetlany.  
  
> [!NOTE]
>  Automatyczne uzupełnianie w programach `ToolStrip` kontrolek w taki sam sposób, który współdziała ona z tradycyjnych formantów takich jak <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Aby włączyć automatycznego uzupełniania w formancie ToolStrip  
  
1.  Utwórz <xref:System.Windows.Forms.ToolStrip> kontroli i dodać elementy do niego.  
  
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
  
2.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> właściwości etykiety i pola kombi <xref:System.Windows.Forms.ToolStripItemOverflow.Never> tak, że listy są zawsze dostępne bez względu na rozmiar formularza.  
  
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
  
3.  Dodawanie wyrazów do kolekcji elementów <xref:System.Windows.Forms.ToolStripComboBox> kontroli.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4.  Ustaw <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> właściwości pola kombi <xref:System.Windows.Forms.AutoCompleteMode.Append>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5.  Ustaw <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> właściwości pola kombi <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip, kontrolka — architektura](toolstrip-control-architecture.md)
- [ToolStrip — podsumowanie informacji o technologii](toolstrip-technology-summary.md)
