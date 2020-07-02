---
title: Dodawanie i usuwanie elementów z kontrolką ListView
description: Dowiedz się, jak dodać i usunąć element z kontrolką Windows Forms ListView, określając element i przypisując do niego właściwości.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618093"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="35325-103">Porady: dodawanie i usuwanie elementów za pomocą formantu ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35325-103">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="35325-104">Proces dodawania elementu do <xref:System.Windows.Forms.ListView> kontrolki Windows Forms składa się głównie z określania elementu i przypisywania do niego właściwości.</span><span class="sxs-lookup"><span data-stu-id="35325-104">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="35325-105">Dodawanie lub usuwanie elementów listy można wykonać w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="35325-105">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="35325-106">Aby programowo dodać elementy</span><span class="sxs-lookup"><span data-stu-id="35325-106">To add items programmatically</span></span>  
  
1. <span data-ttu-id="35325-107">Użyj <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> metody <xref:System.Windows.Forms.ListView.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="35325-107">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="35325-108">Aby programowo usunąć elementy</span><span class="sxs-lookup"><span data-stu-id="35325-108">To remove items programmatically</span></span>  
  
1. <span data-ttu-id="35325-109">Użyj <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> metody lub <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> <xref:System.Windows.Forms.ListView.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="35325-109">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="35325-110"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>Metoda usuwa pojedynczy element; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> Metoda usuwa wszystkie elementy z listy.</span><span class="sxs-lookup"><span data-stu-id="35325-110">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="35325-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35325-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="35325-112">ListView — Formant</span><span class="sxs-lookup"><span data-stu-id="35325-112">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="35325-113">ListView — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="35325-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
