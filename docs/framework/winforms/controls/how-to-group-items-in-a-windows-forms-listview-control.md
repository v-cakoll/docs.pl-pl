---
title: Grupuj elementy w formancie ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: 45846751780f433c29b186fe8b9a908f5d295ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736626"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="e7b03-102">Porady: grupowanie elementów w formancie ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e7b03-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="e7b03-103">Za pomocą funkcji grupowania kontrolki <xref:System.Windows.Forms.ListView> można wyświetlić powiązane zestawy elementów w grupach.</span><span class="sxs-lookup"><span data-stu-id="e7b03-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="e7b03-104">Te grupy są rozdzielane na ekranie przez nagłówki grup poziomych, które zawierają tytuły grup.</span><span class="sxs-lookup"><span data-stu-id="e7b03-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="e7b03-105">Korzystając z grup <xref:System.Windows.Forms.ListView>, można ułatwić nawigację dużych list, grupując elementy alfabetycznie według daty lub przez inne grupowanie logiczne.</span><span class="sxs-lookup"><span data-stu-id="e7b03-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="e7b03-106">Na poniższej ilustracji przedstawiono niektóre zgrupowane elementy.</span><span class="sxs-lookup"><span data-stu-id="e7b03-106">The following image shows some grouped items.</span></span>  
  
 ![Zrzut ekranu przedstawiający nieparzystą i parzystą grupę ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="e7b03-108">Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jedną grupę w projektancie lub programowo.</span><span class="sxs-lookup"><span data-stu-id="e7b03-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="e7b03-109">Po zdefiniowaniu grupy można przypisać elementy <xref:System.Windows.Forms.ListView> do grup.</span><span class="sxs-lookup"><span data-stu-id="e7b03-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="e7b03-110">Możesz również przenieść elementy z jednej grupy do innej programistycznie.</span><span class="sxs-lookup"><span data-stu-id="e7b03-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="e7b03-111">Aby dodać grupy</span><span class="sxs-lookup"><span data-stu-id="e7b03-111">To add groups</span></span>  
  
1. <span data-ttu-id="e7b03-112">Użyj metody <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> kolekcji <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7b03-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="e7b03-113">Aby usunąć grupy</span><span class="sxs-lookup"><span data-stu-id="e7b03-113">To remove groups</span></span>  
  
1. <span data-ttu-id="e7b03-114">Użyj metody <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> lub <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> kolekcji <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7b03-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="e7b03-115">Metoda <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> usuwa pojedynczą grupę; Metoda <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> usuwa wszystkie grupy z listy.</span><span class="sxs-lookup"><span data-stu-id="e7b03-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e7b03-116">Usunięcie grupy nie powoduje usunięcia elementów należących do tej grupy.</span><span class="sxs-lookup"><span data-stu-id="e7b03-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="e7b03-117">Aby przypisać elementy do grup lub przenosić elementy między grupami</span><span class="sxs-lookup"><span data-stu-id="e7b03-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="e7b03-118">Ustaw właściwość <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> poszczególnych elementów.</span><span class="sxs-lookup"><span data-stu-id="e7b03-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="e7b03-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7b03-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="e7b03-120">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="e7b03-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="e7b03-121">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="e7b03-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="e7b03-122">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7b03-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
