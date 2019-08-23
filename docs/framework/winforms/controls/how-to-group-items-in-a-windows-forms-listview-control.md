---
title: 'Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows'
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
ms.openlocfilehash: b4cd2b9ed23f377912270d33b1415ad39c9e80c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966632"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="05e5c-102">Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="05e5c-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="05e5c-103">Za pomocą funkcji <xref:System.Windows.Forms.ListView> grupowania formantu można wyświetlić powiązane zestawy elementów w grupach.</span><span class="sxs-lookup"><span data-stu-id="05e5c-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="05e5c-104">Te grupy są rozdzielane na ekranie przez nagłówki grup poziomych, które zawierają tytuły grup.</span><span class="sxs-lookup"><span data-stu-id="05e5c-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="05e5c-105"><xref:System.Windows.Forms.ListView> Grupy umożliwiają łatwiejsze nawigowanie po dużych listach, grupując elementy alfabetycznie według daty lub przez inne grupowanie logiczne.</span><span class="sxs-lookup"><span data-stu-id="05e5c-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="05e5c-106">Na poniższej ilustracji przedstawiono niektóre zgrupowane elementy.</span><span class="sxs-lookup"><span data-stu-id="05e5c-106">The following image shows some grouped items.</span></span>  
  
 ![Zrzut ekranu przedstawiający nieparzystą i parzystą grupę ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="05e5c-108">Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jedną grupę w projektancie lub programowo.</span><span class="sxs-lookup"><span data-stu-id="05e5c-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="05e5c-109">Po zdefiniowaniu grupy można przypisać <xref:System.Windows.Forms.ListView> elementy do grup.</span><span class="sxs-lookup"><span data-stu-id="05e5c-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="05e5c-110">Możesz również przenieść elementy z jednej grupy do innej programistycznie.</span><span class="sxs-lookup"><span data-stu-id="05e5c-110">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05e5c-111"><xref:System.Windows.Forms.ListView>grupy są dostępne tylko [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] wtedy, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> gdy aplikacja wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="05e5c-111"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="05e5c-112">We wcześniejszych systemach operacyjnych każdy kod dotyczący grup nie ma wpływu, a grupy nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="05e5c-112">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="05e5c-113">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05e5c-113">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="05e5c-114">Aby dodać grupy</span><span class="sxs-lookup"><span data-stu-id="05e5c-114">To add groups</span></span>  
  
1. <span data-ttu-id="05e5c-115"><xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> Użyj metody<xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05e5c-115">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="05e5c-116">Aby usunąć grupy</span><span class="sxs-lookup"><span data-stu-id="05e5c-116">To remove groups</span></span>  
  
1. <span data-ttu-id="05e5c-117"><xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> Użyj metody <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> lub<xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05e5c-117">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="05e5c-118">Metoda usuwa pojedynczą grupę <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> ; Metoda usuwa wszystkie grupy z listy. <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A></span><span class="sxs-lookup"><span data-stu-id="05e5c-118">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="05e5c-119">Usunięcie grupy nie powoduje usunięcia elementów należących do tej grupy.</span><span class="sxs-lookup"><span data-stu-id="05e5c-119">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="05e5c-120">Aby przypisać elementy do grup lub przenosić elementy między grupami</span><span class="sxs-lookup"><span data-stu-id="05e5c-120">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="05e5c-121"><xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> Ustaw właściwość poszczególnych elementów.</span><span class="sxs-lookup"><span data-stu-id="05e5c-121">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="05e5c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05e5c-122">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="05e5c-123">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="05e5c-123">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="05e5c-124">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="05e5c-124">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="05e5c-125">Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05e5c-125">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
