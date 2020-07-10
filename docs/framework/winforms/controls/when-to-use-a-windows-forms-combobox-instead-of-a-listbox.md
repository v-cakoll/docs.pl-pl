---
title: ComboBox a ListBox
description: Dowiedz się więcej o używaniu Windows Forms ComboBox i Windows Forms ListBox i Dowiedz się, jak określić, kiedy jedna lub druga jest bardziej odpowiednia dla zadania.
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
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174422"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="a377e-103">Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox</span><span class="sxs-lookup"><span data-stu-id="a377e-103">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="a377e-104"><xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ListBox> Formanty i mają podobne zachowania, a w niektórych przypadkach mogą być zamienne.</span><span class="sxs-lookup"><span data-stu-id="a377e-104">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="a377e-105">Istnieją jednak przypadki, gdy jedna lub druga jest bardziej odpowiednia dla zadania.</span><span class="sxs-lookup"><span data-stu-id="a377e-105">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="a377e-106">Ogólnie rzecz biorąc, pole kombi jest odpowiednie, gdy istnieje lista sugerowanych opcji, a pole listy jest odpowiednie, gdy chcesz ograniczyć dane wejściowe do listy.</span><span class="sxs-lookup"><span data-stu-id="a377e-106">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="a377e-107">Pole kombi zawiera pole tekstowe, dlatego wybory, które nie znajdują się na liście, można wpisać w.</span><span class="sxs-lookup"><span data-stu-id="a377e-107">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="a377e-108">Wyjątek występuje, gdy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> Właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> .</span><span class="sxs-lookup"><span data-stu-id="a377e-108">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="a377e-109">W takim przypadku kontrolka wybierze element w przypadku wpisania jego pierwszej litery.</span><span class="sxs-lookup"><span data-stu-id="a377e-109">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="a377e-110">Ponadto pola kombi oszczędzają miejsce w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a377e-110">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="a377e-111">Ponieważ pełna lista nie jest wyświetlana, dopóki użytkownik nie kliknie strzałkę w dół, pole kombi może łatwo zmieścić się w niewielkim miejscu, w którym pole listy nie zmieści się.</span><span class="sxs-lookup"><span data-stu-id="a377e-111">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="a377e-112">Wyjątek występuje <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> , gdy właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.Simple> : wyświetlana jest pełna lista, a pole kombi zajmuje więcej miejsca niż pole listy.</span><span class="sxs-lookup"><span data-stu-id="a377e-112">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a377e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a377e-113">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="a377e-114">Porady: dodawanie i usuwanie elementów za pomocą formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a377e-114">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="a377e-115">Porady: sortowanie zawartości formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a377e-115">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="a377e-116">Formanty formularzy systemu Windows używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="a377e-116">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
