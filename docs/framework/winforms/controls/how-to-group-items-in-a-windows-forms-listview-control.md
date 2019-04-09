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
ms.openlocfilehash: 3a070db6c580f0f3798e52b1afbe0ee36947aeb1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091541"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="6d752-102">Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6d752-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="6d752-103">Z funkcji grupowania <xref:System.Windows.Forms.ListView> kontrolki, można wyświetlić powiązane zestawy elementów w grupach.</span><span class="sxs-lookup"><span data-stu-id="6d752-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="6d752-104">Te grupy są oddzielone na ekranie nagłówków grup poziomej, zawierające tytułów grup.</span><span class="sxs-lookup"><span data-stu-id="6d752-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="6d752-105">Możesz użyć <xref:System.Windows.Forms.ListView> grup, aby upewnić się, przechodząc duże listy łatwiejsze przez grupowanie elementów w kolejności alfabetycznej, według daty lub przez inne logiczne grupowanie.</span><span class="sxs-lookup"><span data-stu-id="6d752-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="6d752-106">Na poniższej ilustracji przedstawiono niektóre zgrupowanych elementów.</span><span class="sxs-lookup"><span data-stu-id="6d752-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="6d752-107">![Grupy ListView](./media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="6d752-107">![ListView Groups](./media/listviewgroups.gif "ListViewGroups")</span></span>  
<span data-ttu-id="6d752-108">ListView pogrupowanymi elementami</span><span class="sxs-lookup"><span data-stu-id="6d752-108">ListView grouped items</span></span>  
  
 <span data-ttu-id="6d752-109">Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jedną grupę w Projektancie lub programowo.</span><span class="sxs-lookup"><span data-stu-id="6d752-109">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="6d752-110">Po zdefiniowaniu grupy można przypisać <xref:System.Windows.Forms.ListView> elementów do grupy.</span><span class="sxs-lookup"><span data-stu-id="6d752-110">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="6d752-111">To może również przenieść elementy z jednej grupy do innego programowo.</span><span class="sxs-lookup"><span data-stu-id="6d752-111">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> <span data-ttu-id="6d752-112">grupy są dostępne tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6d752-112">groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6d752-113">W starszych systemach operacyjnych jakiegokolwiek kodu dotyczące grup nie ma wpływu, a grupy nie będą widoczne.</span><span class="sxs-lookup"><span data-stu-id="6d752-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="6d752-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d752-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="6d752-115">Aby dodać grupy</span><span class="sxs-lookup"><span data-stu-id="6d752-115">To add groups</span></span>  
  
1.  <span data-ttu-id="6d752-116">Użyj <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> metody <xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d752-116">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="6d752-117">Aby usunąć grupy</span><span class="sxs-lookup"><span data-stu-id="6d752-117">To remove groups</span></span>  
  
1.  <span data-ttu-id="6d752-118">Użyj <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> lub <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metody <xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d752-118">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="6d752-119"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Metoda usuwa pojedynczą grupę; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metoda usuwa wszystkie grupy z listy.</span><span class="sxs-lookup"><span data-stu-id="6d752-119">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d752-120">Usunięcie grupy nie powoduje usunięcia elementów zawartych w tej grupie.</span><span class="sxs-lookup"><span data-stu-id="6d752-120">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="6d752-121">Przypisywanie elementów do grupy lub przenosić elementy między grupami</span><span class="sxs-lookup"><span data-stu-id="6d752-121">To assign items to groups or move items between groups</span></span>  
  
1.  <span data-ttu-id="6d752-122">Ustaw <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> właściwości poszczególnych elementów.</span><span class="sxs-lookup"><span data-stu-id="6d752-122">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="6d752-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d752-123">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="6d752-124">ListView — Formant</span><span class="sxs-lookup"><span data-stu-id="6d752-124">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="6d752-125">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6d752-125">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="6d752-126">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6d752-126">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
