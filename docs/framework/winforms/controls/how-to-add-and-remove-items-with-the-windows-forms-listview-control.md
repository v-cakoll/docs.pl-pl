---
title: Dodawanie i usuwanie elementów z kontrolką ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: bbfe99db857ebe3a80bf99926f3ce0bec38a1f3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743139"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="e69e8-102">Porady: dodawanie i usuwanie elementów za pomocą formantu ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e69e8-102">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="e69e8-103">Proces dodawania elementu do kontrolki <xref:System.Windows.Forms.ListView> Windows Forms składa się głównie z określania elementu i przypisywania do niego właściwości.</span><span class="sxs-lookup"><span data-stu-id="e69e8-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="e69e8-104">Dodawanie lub usuwanie elementów listy można wykonać w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="e69e8-104">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="e69e8-105">Aby programowo dodać elementy</span><span class="sxs-lookup"><span data-stu-id="e69e8-105">To add items programmatically</span></span>  
  
1. <span data-ttu-id="e69e8-106">Użyj metody <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> właściwości <xref:System.Windows.Forms.ListView.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="e69e8-106">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="e69e8-107">Aby programowo usunąć elementy</span><span class="sxs-lookup"><span data-stu-id="e69e8-107">To remove items programmatically</span></span>  
  
1. <span data-ttu-id="e69e8-108">Użyj metody <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> lub <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> właściwości <xref:System.Windows.Forms.ListView.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="e69e8-108">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="e69e8-109">Metoda <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> usuwa pojedynczy element; Metoda <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> usuwa wszystkie elementy z listy.</span><span class="sxs-lookup"><span data-stu-id="e69e8-109">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="e69e8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e69e8-110">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="e69e8-111">ListView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e69e8-111">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="e69e8-112">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="e69e8-112">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
