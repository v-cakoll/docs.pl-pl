---
title: Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 5dc7778f43c01fd28a14489a7b4179dd851568b2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703000"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="10969-102">Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox</span><span class="sxs-lookup"><span data-stu-id="10969-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="10969-103"><xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> kontrolki mają podobne zachowania, a w niektórych przypadkach może być wymienne.</span><span class="sxs-lookup"><span data-stu-id="10969-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="10969-104">Brak sytuacji, gdy jednej z nich jest bardziej odpowiednie do zadania.</span><span class="sxs-lookup"><span data-stu-id="10969-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="10969-105">Ogólnie rzecz biorąc pola kombi jest odpowiednie, jeśli znajduje się lista sugerowanych dostępnych opcji i pola listy jest odpowiednia w przypadku, gdy chcesz ograniczyć dane wejściowe, co znajduje się na liście.</span><span class="sxs-lookup"><span data-stu-id="10969-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="10969-106">Pole kombi zawiera pole tekstowe, więc wpisano opcji nie ma na liście.</span><span class="sxs-lookup"><span data-stu-id="10969-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="10969-107">Wyjątkiem jest, gdy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="10969-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="10969-108">W takim przypadku formantu wybierz element, jeśli wpiszesz swojej pierwszej litery.</span><span class="sxs-lookup"><span data-stu-id="10969-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="10969-109">Ponadto pola kombi zaoszczędzić miejsce na formularzu.</span><span class="sxs-lookup"><span data-stu-id="10969-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="10969-110">Ponieważ pełnej listy nie jest wyświetlany, dopóki użytkownik kliknie strzałkę w dół, pola kombi mogą łatwo mieści się w mała ilość miejsca, gdzie pole listy nie pasuje.</span><span class="sxs-lookup"><span data-stu-id="10969-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="10969-111">Wyjątek jest, gdy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.Simple>: wyświetlana jest pełna lista i pola kombi zajmuje więcej miejsca niż będzie pola listy.</span><span class="sxs-lookup"><span data-stu-id="10969-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10969-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10969-112">See also</span></span>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="10969-113">Instrukcje: Dodawanie i usuwanie elementów z Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="10969-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="10969-114">Instrukcje: Sortowanie zawartości Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="10969-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="10969-115">Kontrolki formularzy Windows Forms używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="10969-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
