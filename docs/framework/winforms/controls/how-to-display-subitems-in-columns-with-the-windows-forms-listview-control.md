---
title: Wyświetlanie elementów SubItems w kolumnach z kontrolką ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745547"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="4940c-102">Porady: wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4940c-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="4940c-103">Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms może wyświetlać dodatkowy tekst lub podelementy dla każdego elementu w widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="4940c-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="4940c-104">W pierwszej kolumnie jest wyświetlany tekst elementu, na przykład numer pracownika.</span><span class="sxs-lookup"><span data-stu-id="4940c-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="4940c-105">Druga, trzecia i kolejne kolumny wyświetlają pierwszy, drugi i kolejne skojarzone elementy.</span><span class="sxs-lookup"><span data-stu-id="4940c-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="4940c-106">Aby dodać elementy podelementowe do elementu listy</span><span class="sxs-lookup"><span data-stu-id="4940c-106">To add subitems to a list item</span></span>  
  
1. <span data-ttu-id="4940c-107">Dodaj wszystkie potrzebne kolumny.</span><span class="sxs-lookup"><span data-stu-id="4940c-107">Add any columns needed.</span></span> <span data-ttu-id="4940c-108">Ponieważ w pierwszej kolumnie będzie wyświetlana właściwość <xref:System.Windows.Forms.ListView.Text%2A> elementu, potrzebna jest jeszcze jedna kolumna niż w przypadku elementów SubItems.</span><span class="sxs-lookup"><span data-stu-id="4940c-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="4940c-109">Aby uzyskać więcej informacji na temat dodawania kolumn, zobacz [jak to zrobić: Dodawanie kolumn do kontrolki ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="4940c-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2. <span data-ttu-id="4940c-110">Wywołaj metodę <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> kolekcji zwróconej przez właściwość <xref:System.Windows.Forms.ListViewItem.SubItems%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="4940c-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="4940c-111">Poniższy przykład kodu ustawia nazwę pracownika i dział dla elementu listy.</span><span class="sxs-lookup"><span data-stu-id="4940c-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="4940c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4940c-112">See also</span></span>

- [<span data-ttu-id="4940c-113">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="4940c-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="4940c-114">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4940c-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4940c-115">Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4940c-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4940c-116">Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4940c-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4940c-117">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4940c-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
