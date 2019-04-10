---
title: 'Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy systemu Windows'
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
ms.openlocfilehash: 318521cc1377be89ef54706d80c8b2990a6ba1b8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339297"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="4fcf7-102">Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4fcf7-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="4fcf7-103">Formularze Windows <xref:System.Windows.Forms.ListView> formant może wyświetlić dodatkowy tekst lub podrzędnych dla każdego elementu w widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="4fcf7-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="4fcf7-104">Pierwsza kolumna Wyświetla tekst elementu, na przykład numer pracownika.</span><span class="sxs-lookup"><span data-stu-id="4fcf7-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="4fcf7-105">Drugi, trzeci i kolejnych kolumn wyświetlany jako pierwszy, drugi i kolejne skojarzone elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="4fcf7-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="4fcf7-106">Aby dodać elementy podrzędne elementu listy</span><span class="sxs-lookup"><span data-stu-id="4fcf7-106">To add subitems to a list item</span></span>  
  
1. <span data-ttu-id="4fcf7-107">Dodaj potrzebne kolumny.</span><span class="sxs-lookup"><span data-stu-id="4fcf7-107">Add any columns needed.</span></span> <span data-ttu-id="4fcf7-108">Ponieważ pierwszej kolumny spowoduje wyświetlenie elementu <xref:System.Windows.Forms.ListView.Text%2A> właściwość, należy jedną kolumnę więcej niż elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="4fcf7-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="4fcf7-109">Aby uzyskać więcej informacji na temat dodawania kolumn, zobacz [jak: Dodawanie kolumn do Windows formantu ListView formularzy](how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="4fcf7-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2. <span data-ttu-id="4fcf7-110">Wywołaj <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> metoda zbiorze zwróconym przez <xref:System.Windows.Forms.ListViewItem.SubItems%2A> właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="4fcf7-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="4fcf7-111">Poniższy przykładowy kod ustawia nazwiska pracownika i działu dla elementu listy.</span><span class="sxs-lookup"><span data-stu-id="4fcf7-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="4fcf7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fcf7-112">See also</span></span>

- [<span data-ttu-id="4fcf7-113">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="4fcf7-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="4fcf7-114">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4fcf7-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4fcf7-115">Instrukcje: dodawanie kolumn do kontrolki ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4fcf7-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4fcf7-116">Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4fcf7-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4fcf7-117">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="4fcf7-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
