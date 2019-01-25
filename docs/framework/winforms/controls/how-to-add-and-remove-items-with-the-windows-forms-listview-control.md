---
title: 'Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: 7a4083d54ea85ff7a2e18f7e448f2b967317ac25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544526"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="fc503-102">Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="fc503-102">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="fc503-103">Proces dodawania elementu do formularzy Windows <xref:System.Windows.Forms.ListView> kontroli składa się przede wszystkim określenie elementu i przypisywanie właściwości do niego.</span><span class="sxs-lookup"><span data-stu-id="fc503-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="fc503-104">Dodawanie lub usuwanie pozycji listy może odbywać się w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="fc503-104">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="fc503-105">Aby programowo dodać elementy</span><span class="sxs-lookup"><span data-stu-id="fc503-105">To add items programmatically</span></span>  
  
1.  <span data-ttu-id="fc503-106">Użyj <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> metody <xref:System.Windows.Forms.ListView.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc503-106">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="fc503-107">Aby programowo usunąć elementy</span><span class="sxs-lookup"><span data-stu-id="fc503-107">To remove items programmatically</span></span>  
  
1.  <span data-ttu-id="fc503-108">Użyj <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> lub <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> metody <xref:System.Windows.Forms.ListView.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc503-108">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="fc503-109"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> Metoda usuwa pojedynczy element; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> metoda usuwa wszystkie elementy z listy.</span><span class="sxs-lookup"><span data-stu-id="fc503-109">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="fc503-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc503-110">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="fc503-111">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="fc503-111">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="fc503-112">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="fc503-112">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
