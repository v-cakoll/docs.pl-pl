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
ms.openlocfilehash: db411023ad624e4c3d60b09bdbd588c85f8e22d1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745504"
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a><span data-ttu-id="ef384-102">Porady: włączanie funkcji AutoComplete w formantach ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ef384-102">How to: Enable AutoComplete in ToolStrip Controls in Windows Forms</span></span>
<span data-ttu-id="ef384-103">Poniższa procedura łączy <xref:System.Windows.Forms.ToolStripLabel> z <xref:System.Windows.Forms.ToolStripComboBox>, które mogą zostać usunięte, aby wyświetlić listę elementów, takich jak ostatnio odwiedzone witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ef384-103">The following procedure combines a <xref:System.Windows.Forms.ToolStripLabel> with a <xref:System.Windows.Forms.ToolStripComboBox> that can be dropped down to show a list of items, such as recently visited Web sites.</span></span> <span data-ttu-id="ef384-104">Jeśli użytkownik wpisze znak pasujący do pierwszego znaku jednego z elementów na liście, element zostanie natychmiast wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="ef384-104">If the user types a character that matches the first character of one of the items in the list, the item is immediately displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef384-105">Automatyczne uzupełnianie działa z kontrolkami `ToolStrip` w taki sam sposób, w jaki działa z tradycyjnymi kontrolkami, takimi jak <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="ef384-105">Automatic completion works with `ToolStrip` controls in the same way that it works with traditional controls such as <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a><span data-ttu-id="ef384-106">Aby włączyć Autouzupełnianie w formancie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ef384-106">To enable AutoComplete in a ToolStrip control</span></span>  
  
1. <span data-ttu-id="ef384-107">Utwórz kontrolkę <xref:System.Windows.Forms.ToolStrip> i Dodaj do niej elementy.</span><span class="sxs-lookup"><span data-stu-id="ef384-107">Create a <xref:System.Windows.Forms.ToolStrip> control and add items to it.</span></span>  
  
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
  
2. <span data-ttu-id="ef384-108">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> etykiety i pola kombi na <xref:System.Windows.Forms.ToolStripItemOverflow.Never>, aby lista była zawsze dostępna niezależnie od rozmiaru formularza.</span><span class="sxs-lookup"><span data-stu-id="ef384-108">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the label and the combo box to <xref:System.Windows.Forms.ToolStripItemOverflow.Never> so that the list is always available regardless of the form's size.</span></span>  
  
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
  
3. <span data-ttu-id="ef384-109">Dodaj wyrazy do kolekcji Items formantu <xref:System.Windows.Forms.ToolStripComboBox>.</span><span class="sxs-lookup"><span data-stu-id="ef384-109">Add words to the Items collection of the <xref:System.Windows.Forms.ToolStripComboBox> control.</span></span>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4. <span data-ttu-id="ef384-110">Ustaw właściwość <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> pola kombi na <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span><span class="sxs-lookup"><span data-stu-id="ef384-110">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5. <span data-ttu-id="ef384-111">Ustaw właściwość <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> pola kombi na <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span><span class="sxs-lookup"><span data-stu-id="ef384-111">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ef384-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef384-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripLabel>
- <xref:System.Windows.Forms.ToolStripComboBox>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>
- <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>
- [<span data-ttu-id="ef384-113">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="ef384-113">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="ef384-114">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="ef384-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="ef384-115">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="ef384-115">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
