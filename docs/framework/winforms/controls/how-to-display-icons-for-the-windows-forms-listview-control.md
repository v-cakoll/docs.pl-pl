---
title: 'Instrukcje: Wyświetlanie ikon dla kontrolki ListView formularzy Windows'
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
ms.openlocfilehash: 3c3df1fb38c9fbcf672e9ffcd8c0aa3c881be00b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510627"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="eb7e8-102">Instrukcje: Wyświetlanie ikon dla kontrolki ListView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="eb7e8-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="eb7e8-103">Formularze Windows <xref:System.Windows.Forms.ListView> formant może wyświetlać ikony z trzema list obrazów.</span><span class="sxs-lookup"><span data-stu-id="eb7e8-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="eb7e8-104">Widoki List, szczegóły i SmallIcon wyświetlanie obrazów z listy obrazów, określone w <xref:System.Windows.Forms.ListView.SmallImageList%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb7e8-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="eb7e8-105">Wyświetl LargeIcon wyświetla obrazy z listy obrazów, określone w <xref:System.Windows.Forms.ListView.LargeImageList%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb7e8-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="eb7e8-106">Widok listy można także wyświetlać dodatkowego zestawu ikon w <xref:System.Windows.Forms.ListView.StateImageList%2A> właściwości obok duże lub małe ikony.</span><span class="sxs-lookup"><span data-stu-id="eb7e8-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="eb7e8-107">Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnika ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) i [jak: Dodawanie lub usuwanie obrazów za pomocą Windows składnika ImageList formularzy](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e8-107">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="eb7e8-108">Aby wyświetlić obrazy w widoku listy</span><span class="sxs-lookup"><span data-stu-id="eb7e8-108">To display images in a list view</span></span>  
  
1.  <span data-ttu-id="eb7e8-109">Ustawić właściwość odpowiednie —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, lub <xref:System.Windows.Forms.ListView.StateImageList%2A>— do istniejącego <xref:System.Windows.Forms.ImageList> składników, które chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="eb7e8-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="eb7e8-110">Te właściwości można ustawić w projektancie w oknie właściwości lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="eb7e8-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  <span data-ttu-id="eb7e8-111">Ustaw <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> lub <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> właściwości dla każdego elementu listy, który zawiera ikonę skojarzone.</span><span class="sxs-lookup"><span data-stu-id="eb7e8-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="eb7e8-112">Te właściwości można ustawić w kodzie lub w ramach **ListViewItem — Edytor kolekcji**.</span><span class="sxs-lookup"><span data-stu-id="eb7e8-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="eb7e8-113">Aby otworzyć **ListViewItem — Edytor kolekcji**, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok <xref:System.Windows.Forms.ListView.Items%2A>właściwość **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="eb7e8-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="eb7e8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb7e8-114">See also</span></span>
- [<span data-ttu-id="eb7e8-115">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="eb7e8-115">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [<span data-ttu-id="eb7e8-116">Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="eb7e8-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="eb7e8-117">Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="eb7e8-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="eb7e8-118">Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="eb7e8-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="eb7e8-119">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="eb7e8-119">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
