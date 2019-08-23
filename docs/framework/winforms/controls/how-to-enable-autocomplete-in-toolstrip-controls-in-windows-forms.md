---
title: 'Instrukcje: Włącz Autouzupełnianie w kontrolkach ToolStrip w Windows Forms'
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
ms.openlocfilehash: 301f1b156bbaee5c5f7be95e972ee1ebaa83777f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963615"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Instrukcje: Włącz Autouzupełnianie w kontrolkach ToolStrip w Windows Forms
Poniższa procedura polega <xref:System.Windows.Forms.ToolStripLabel> na <xref:System.Windows.Forms.ToolStripComboBox> połączeniu z programem, który może zostać porzucony w celu wyświetlenia listy elementów, takich jak ostatnio odwiedzone witryny sieci Web. Jeśli użytkownik wpisze znak pasujący do pierwszego znaku jednego z elementów na liście, element zostanie natychmiast wyświetlony.  
  
> [!NOTE]
> Automatyczne uzupełnianie działa `ToolStrip` z kontrolkami w taki sam sposób, w jaki działa z tradycyjnymi <xref:System.Windows.Forms.TextBox>kontrolkami, takimi jak <xref:System.Windows.Forms.ComboBox> i.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Aby włączyć Autouzupełnianie w formancie ToolStrip  
  
1. <xref:System.Windows.Forms.ToolStrip> Utwórz kontrolkę i Dodaj do niej elementy.  
  
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
  
2. Ustaw właściwość etykiety i pola kombi na tak, aby <xref:System.Windows.Forms.ToolStripItemOverflow.Never> lista była zawsze dostępna niezależnie od rozmiaru formularza. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
  
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
  
3. Dodaj wyrazy do kolekcji <xref:System.Windows.Forms.ToolStripComboBox> Items formantu.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. Ustaw właściwość pola kombi na <xref:System.Windows.Forms.AutoCompleteMode.Append>. <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. Ustaw właściwość pola kombi na <xref:System.Windows.Forms.AutoCompleteSource.ListItems>. <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>  
  
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
