---
title: Sortuj zawartość kontrolki ComboBox, ListBox lub CheckedListBox
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: dee969d777edf76434622fe632f7e934987a1dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742955"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="fccbc-102">Porady: sortowanie zawartości formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fccbc-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="fccbc-103">Kontrolki Windows Forms nie sortują się, gdy są powiązane z danymi.</span><span class="sxs-lookup"><span data-stu-id="fccbc-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="fccbc-104">Aby wyświetlić posortowane dane, użyj źródła danych, które obsługuje sortowanie, a następnie posortuj je ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="fccbc-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="fccbc-105">Źródłami danych, które obsługują sortowanie, są widoki danych, menedżerów widoku danych i posortowane tablice.</span><span class="sxs-lookup"><span data-stu-id="fccbc-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="fccbc-106">Jeśli formant nie jest powiązany z danymi, można go posortować.</span><span class="sxs-lookup"><span data-stu-id="fccbc-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="fccbc-107">Aby posortować listę</span><span class="sxs-lookup"><span data-stu-id="fccbc-107">To sort the list</span></span>  
  
1. <span data-ttu-id="fccbc-108">Ustaw właściwość `Sorted` na `true`.</span><span class="sxs-lookup"><span data-stu-id="fccbc-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="fccbc-109">To ustawienie zmienia położenie wszystkich istniejących elementów listy w kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="fccbc-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccbc-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fccbc-110">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="fccbc-111">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fccbc-111">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="fccbc-112">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fccbc-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="fccbc-113">Kiedy należy używać kontrolki ComboBox formularzy Windows Forms zamiast ListBox</span><span class="sxs-lookup"><span data-stu-id="fccbc-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="fccbc-114">Kontrolki formularzy Windows Forms używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="fccbc-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
