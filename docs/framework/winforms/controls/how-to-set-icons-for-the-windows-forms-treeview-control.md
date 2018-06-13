---
title: 'Porady: ustawienie ikon dla kontrolki TreeView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: b732aa510be22f3cbdc5197574f1e2a825c35df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536488"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="80347-102">Porady: ustawienie ikon dla kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="80347-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="80347-103">Formularze systemu Windows <xref:System.Windows.Forms.TreeView> formant może wyświetlać ikony obok każdego węzła.</span><span class="sxs-lookup"><span data-stu-id="80347-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="80347-104">Ikony są pozycjonowane do natychmiastowego po lewej stronie tekstu węzła.</span><span class="sxs-lookup"><span data-stu-id="80347-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="80347-105">Aby wyświetlić te ikony, należy skojarzyć z widoku drzewa <xref:System.Windows.Forms.ImageList> formantu.</span><span class="sxs-lookup"><span data-stu-id="80347-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="80347-106">Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnika ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) i [porady: Dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="80347-106">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80347-107">Błąd w programie Microsoft .NET Framework w wersji 1.1 zapobiega wyświetlaniu na obrazy <xref:System.Windows.Forms.TreeView> węzłów, gdy aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80347-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80347-108">Aby obejść ten problem, należy wywołać <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> w Twojej `Main` metody natychmiast po wywołaniu <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="80347-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="80347-109">Ten problem został rozwiązany w [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="80347-109">This bug is fixed in [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="80347-110">Do wyświetlania obrazów w widoku drzewa</span><span class="sxs-lookup"><span data-stu-id="80347-110">To display images in a tree view</span></span>  
  
1.  <span data-ttu-id="80347-111">Ustaw <xref:System.Windows.Forms.TreeView> formantu <xref:System.Windows.Forms.TreeView.ImageList%2A> właściwości do istniejącej <xref:System.Windows.Forms.ImageList> formantu ma zostać użyty.</span><span class="sxs-lookup"><span data-stu-id="80347-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="80347-112">Te właściwości można ustawić w projektancie w oknie właściwości lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="80347-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  <span data-ttu-id="80347-113">Ustaw węzła <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> i <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="80347-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="80347-114"><xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Właściwość określa obraz wyświetlany dla węzła normalne i rozwinięte oraz <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> właściwość określa obraz wyświetlany dla stanu wybranego węzła.</span><span class="sxs-lookup"><span data-stu-id="80347-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="80347-115">Te właściwości można ustawić w kodzie lub edytora TreeNode.</span><span class="sxs-lookup"><span data-stu-id="80347-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="80347-116">Aby otworzyć Edytor TreeNode, kliknij przycisk oznaczony wielokropkiem ( ![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="80347-116">To open the TreeNode Editor, click the ellipsis button ( ![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="80347-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80347-117">See Also</span></span>  
 [<span data-ttu-id="80347-118">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="80347-118">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="80347-119">Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80347-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="80347-120">Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80347-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="80347-121">Instrukcje: określanie, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="80347-121">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="80347-122">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="80347-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
