---
title: 'Porady: grupowanie elementów w formancie ListView formularzy systemu Windows'
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
ms.openlocfilehash: 2847b95694eefec524bee9c95b5de91fa5a03f5d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785574"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="eb85c-102">Porady: grupowanie elementów w formancie ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="eb85c-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="eb85c-103">Z funkcji grupowania <xref:System.Windows.Forms.ListView> kontrolki, można wyświetlić powiązane zestawy elementów w grupach.</span><span class="sxs-lookup"><span data-stu-id="eb85c-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="eb85c-104">Te grupy są oddzielone na ekranie nagłówków grup poziomej, zawierające tytułów grup.</span><span class="sxs-lookup"><span data-stu-id="eb85c-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="eb85c-105">Możesz użyć <xref:System.Windows.Forms.ListView> grup, aby upewnić się, przechodząc duże listy łatwiejsze przez grupowanie elementów w kolejności alfabetycznej, według daty lub przez inne logiczne grupowanie.</span><span class="sxs-lookup"><span data-stu-id="eb85c-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="eb85c-106">Na poniższej ilustracji przedstawiono niektóre zgrupowanych elementów.</span><span class="sxs-lookup"><span data-stu-id="eb85c-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="eb85c-107">![Grupy ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="eb85c-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
<span data-ttu-id="eb85c-108">ListView pogrupowanymi elementami</span><span class="sxs-lookup"><span data-stu-id="eb85c-108">ListView grouped items</span></span>  
  
 <span data-ttu-id="eb85c-109">Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jedną grupę w Projektancie lub programowo.</span><span class="sxs-lookup"><span data-stu-id="eb85c-109">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="eb85c-110">Po zdefiniowaniu grupy można przypisać <xref:System.Windows.Forms.ListView> elementów do grupy.</span><span class="sxs-lookup"><span data-stu-id="eb85c-110">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="eb85c-111">To może również przenieść elementy z jednej grupy do innego programowo.</span><span class="sxs-lookup"><span data-stu-id="eb85c-111">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb85c-112"><xref:System.Windows.Forms.ListView> grupy są dostępne tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="eb85c-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="eb85c-113">W starszych systemach operacyjnych jakiegokolwiek kodu dotyczące grup nie ma wpływu, a grupy nie będą widoczne.</span><span class="sxs-lookup"><span data-stu-id="eb85c-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="eb85c-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb85c-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="eb85c-115">Aby dodać grupy</span><span class="sxs-lookup"><span data-stu-id="eb85c-115">To add groups</span></span>  
  
1.  <span data-ttu-id="eb85c-116">Użyj <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> metody <xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="eb85c-116">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="eb85c-117">Aby usunąć grupy</span><span class="sxs-lookup"><span data-stu-id="eb85c-117">To remove groups</span></span>  
  
1.  <span data-ttu-id="eb85c-118">Użyj <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> lub <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metody <xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="eb85c-118">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="eb85c-119"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Metoda usuwa pojedynczą grupę; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metoda usuwa wszystkie grupy z listy.</span><span class="sxs-lookup"><span data-stu-id="eb85c-119">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb85c-120">Usunięcie grupy nie powoduje usunięcia elementów zawartych w tej grupie.</span><span class="sxs-lookup"><span data-stu-id="eb85c-120">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="eb85c-121">Przypisywanie elementów do grupy lub przenosić elementy między grupami</span><span class="sxs-lookup"><span data-stu-id="eb85c-121">To assign items to groups or move items between groups</span></span>  
  
1.  <span data-ttu-id="eb85c-122">Ustaw <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> właściwości poszczególnych elementów.</span><span class="sxs-lookup"><span data-stu-id="eb85c-122">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="eb85c-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb85c-123">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="eb85c-124">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="eb85c-124">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="eb85c-125">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="eb85c-125">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="eb85c-126">Funkcje systemu Windows XP i kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb85c-126">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="eb85c-127">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb85c-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
