---
title: Grupuj elementy w formancie Widoku listy
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
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141994"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="53b88-102">Porady: grupowanie elementów w formancie ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="53b88-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="53b88-103">Za pomocą funkcji grupowania <xref:System.Windows.Forms.ListView> formantu można wyświetlać powiązane zestawy elementów w grupach.</span><span class="sxs-lookup"><span data-stu-id="53b88-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="53b88-104">Grupy te są oddzielone na ekranie poziomymi nagłówkami grup, które zawierają tytuły grup.</span><span class="sxs-lookup"><span data-stu-id="53b88-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="53b88-105">Za pomocą <xref:System.Windows.Forms.ListView> grup można ułatwiać poruszanie się po dużych listach, grupując elementy alfabetycznie, według daty lub przez inne grupowanie logiczne.</span><span class="sxs-lookup"><span data-stu-id="53b88-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="53b88-106">Na poniższej ilustracji przedstawiono niektóre elementy zgrupowane.</span><span class="sxs-lookup"><span data-stu-id="53b88-106">The following image shows some grouped items.</span></span>  
  
 ![Zrzut ekranu przedstawiający grupy nieparzyste i parzyste ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 <span data-ttu-id="53b88-108">Aby włączyć grupowanie, należy najpierw utworzyć jedną lub więcej grup w projektancie lub programowo.</span><span class="sxs-lookup"><span data-stu-id="53b88-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="53b88-109">Po zdefiniowaniu grupy można przypisać <xref:System.Windows.Forms.ListView> elementy do grup.</span><span class="sxs-lookup"><span data-stu-id="53b88-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="53b88-110">Elementy można również programowo przenosić z jednej grupy do innej.</span><span class="sxs-lookup"><span data-stu-id="53b88-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="53b88-111">Aby dodać grupy</span><span class="sxs-lookup"><span data-stu-id="53b88-111">To add groups</span></span>  
  
1. <span data-ttu-id="53b88-112">Użyj <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> metody kolekcji. <xref:System.Windows.Forms.ListView.Groups%2A></span><span class="sxs-lookup"><span data-stu-id="53b88-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="53b88-113">Aby usunąć grupy</span><span class="sxs-lookup"><span data-stu-id="53b88-113">To remove groups</span></span>  
  
1. <span data-ttu-id="53b88-114">Użyj <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> lub <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metody <xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="53b88-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="53b88-115">Metoda <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> usuwa jedną grupę; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metoda usuwa wszystkie grupy z listy.</span><span class="sxs-lookup"><span data-stu-id="53b88-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="53b88-116">Usunięcie grupy nie powoduje usunięcia elementów z tej grupy.</span><span class="sxs-lookup"><span data-stu-id="53b88-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="53b88-117">Przypisywanie elementów do grup lub przenoszenie elementów między grupami</span><span class="sxs-lookup"><span data-stu-id="53b88-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="53b88-118">Ustaw <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> właściwość poszczególnych elementów.</span><span class="sxs-lookup"><span data-stu-id="53b88-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="53b88-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53b88-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="53b88-120">ListView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="53b88-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="53b88-121">ListView — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="53b88-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="53b88-122">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="53b88-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
