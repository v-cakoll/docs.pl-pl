---
title: Wyświetl ikony dla kontrolki ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744505"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="2278e-102">Porady: wyświetlanie ikon dla formantu ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2278e-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="2278e-103">Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms może wyświetlać ikony z trzech list obrazów.</span><span class="sxs-lookup"><span data-stu-id="2278e-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="2278e-104">Widoki list, szczegółów i SmallIcon wyświetlają obrazy z listy obrazów określonych we właściwości <xref:System.Windows.Forms.ListView.SmallImageList%2A>.</span><span class="sxs-lookup"><span data-stu-id="2278e-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="2278e-105">Widok widoku LargeIcon wyświetla obrazy z listy obrazów określony we właściwości <xref:System.Windows.Forms.ListView.LargeImageList%2A>.</span><span class="sxs-lookup"><span data-stu-id="2278e-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="2278e-106">W widoku listy można także wyświetlić dodatkowy zestaw ikon ustawionych we właściwości <xref:System.Windows.Forms.ListView.StateImageList%2A> obok wielkich lub małych ikon.</span><span class="sxs-lookup"><span data-stu-id="2278e-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="2278e-107">Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnik ImageList](imagelist-component-windows-forms.md) i [instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="2278e-107">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="2278e-108">Aby wyświetlić obrazy w widoku listy</span><span class="sxs-lookup"><span data-stu-id="2278e-108">To display images in a list view</span></span>  
  
1. <span data-ttu-id="2278e-109">Ustaw odpowiednią właściwość —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>lub <xref:System.Windows.Forms.ListView.StateImageList%2A>— na istniejący składnik <xref:System.Windows.Forms.ImageList>, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="2278e-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="2278e-110">Te właściwości można ustawić w projektancie przy użyciu okno Właściwości lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2278e-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. <span data-ttu-id="2278e-111">Ustaw właściwość <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> lub <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> dla każdego elementu listy, który ma skojarzoną ikonę.</span><span class="sxs-lookup"><span data-stu-id="2278e-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="2278e-112">Te właściwości można ustawić w kodzie lub w **edytorze kolekcji ListViewItem**.</span><span class="sxs-lookup"><span data-stu-id="2278e-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="2278e-113">Aby otworzyć **Edytor kolekcji ListViewItem**, kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ListView.Items%2A> w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="2278e-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="2278e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2278e-114">See also</span></span>

- [<span data-ttu-id="2278e-115">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2278e-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="2278e-116">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2278e-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="2278e-117">Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2278e-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="2278e-118">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2278e-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="2278e-119">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="2278e-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
