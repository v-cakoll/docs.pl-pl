---
title: "Porady: wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be1b055c8ea0e7a7c6466033735431a17ecc32f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="75c36-102">Porady: wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="75c36-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="75c36-103">Formularze systemu Windows <xref:System.Windows.Forms.ListView> formant może wyświetlać dodatkowy tekst lub podrzędnych, dla każdego elementu w widoku Details.</span><span class="sxs-lookup"><span data-stu-id="75c36-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="75c36-104">Pierwsza kolumna Wyświetla tekst elementu, na przykład numer pracownika.</span><span class="sxs-lookup"><span data-stu-id="75c36-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="75c36-105">Druga Strona, kolumny trzeci i kolejne zawierają pierwszy, drugi i kolejne skojarzone elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="75c36-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="75c36-106">Aby dodać elementy podrzędne elementu listy</span><span class="sxs-lookup"><span data-stu-id="75c36-106">To add subitems to a list item</span></span>  
  
1.  <span data-ttu-id="75c36-107">Dodawanie kolumn potrzebne.</span><span class="sxs-lookup"><span data-stu-id="75c36-107">Add any columns needed.</span></span> <span data-ttu-id="75c36-108">Ponieważ pierwszej kolumny spowoduje wyświetlenie elementu <xref:System.Windows.Forms.ListView.Text%2A> właściwość, należy jedną kolumnę więcej niż elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="75c36-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="75c36-109">Aby uzyskać więcej informacji na temat dodawania kolumny, zobacz [porady: Dodawanie kolumn do formantu ListView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="75c36-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2.  <span data-ttu-id="75c36-110">Wywołanie <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> metody kolekcji zwróconej przez <xref:System.Windows.Forms.ListViewItem.SubItems%2A> właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="75c36-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="75c36-111">W poniższym przykładzie kodu ustawia nazwę pracowników i działu dla elementu listy.</span><span class="sxs-lookup"><span data-stu-id="75c36-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="75c36-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75c36-112">See Also</span></span>  
 [<span data-ttu-id="75c36-113">Informacje o formancie ListView</span><span class="sxs-lookup"><span data-stu-id="75c36-113">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="75c36-114">Porady: Dodawanie i usuwanie elementów za pomocą systemu Windows formantu ListView formularzy</span><span class="sxs-lookup"><span data-stu-id="75c36-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="75c36-115">Porady: Dodawanie kolumn do systemu Windows formantu ListView formularzy</span><span class="sxs-lookup"><span data-stu-id="75c36-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="75c36-116">Porady: wyświetlanie ikon dla formantu ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="75c36-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="75c36-117">Porady: Dodawanie niestandardowych informacji do formantu TreeView lub ListView (formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="75c36-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
