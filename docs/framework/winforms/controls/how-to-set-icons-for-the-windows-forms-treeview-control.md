---
title: 'Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy systemu Windows'
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
ms.openlocfilehash: 12b8354890f0ba613b35615dc5cf3a5b3555e7ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097629"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="61b26-102">Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="61b26-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="61b26-103">Formularze Windows <xref:System.Windows.Forms.TreeView> formant może wyświetlać ikony obok każdego węzła.</span><span class="sxs-lookup"><span data-stu-id="61b26-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="61b26-104">Ikony są pozycjonowane natychmiastowego po lewej stronie tekstu węzła.</span><span class="sxs-lookup"><span data-stu-id="61b26-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="61b26-105">Aby wyświetlić te ikony, należy skojarzyć widok drzewa z <xref:System.Windows.Forms.ImageList> kontroli.</span><span class="sxs-lookup"><span data-stu-id="61b26-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="61b26-106">Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnika ImageList](imagelist-component-windows-forms.md) i [jak: Dodawanie lub usuwanie obrazów za pomocą Windows składnika ImageList formularzy](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="61b26-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61b26-107">Usterki programu Microsoft .NET Framework w wersji 1.1 zapobiega wyświetlaniu w obrazów <xref:System.Windows.Forms.TreeView> węzłów, gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="61b26-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="61b26-108">Aby obejść ten problem, należy wywołać <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> w swojej `Main` metoda natychmiast po wywołaniu <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="61b26-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="61b26-109">Ten problem został rozwiązany w [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61b26-109">This bug is fixed in [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="61b26-110">Aby wyświetlić obrazy w widoku drzewa</span><span class="sxs-lookup"><span data-stu-id="61b26-110">To display images in a tree view</span></span>  
  
1.  <span data-ttu-id="61b26-111">Ustaw <xref:System.Windows.Forms.TreeView> kontrolki <xref:System.Windows.Forms.TreeView.ImageList%2A> właściwości do istniejących <xref:System.Windows.Forms.ImageList> kontrolki, które chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="61b26-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="61b26-112">Te właściwości można ustawić w projektancie w oknie właściwości lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="61b26-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  <span data-ttu-id="61b26-113">Ustaw węzeł <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> i <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="61b26-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="61b26-114"><xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Właściwość określa obraz wyświetlany dla stanów normalne i rozwiniętego węzła i <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> właściwość określa obraz wyświetlany dla wybranego stanu węzła.</span><span class="sxs-lookup"><span data-stu-id="61b26-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="61b26-115">Te właściwości można ustawić w kodzie lub w obrębie elementu TreeNode Editor.</span><span class="sxs-lookup"><span data-stu-id="61b26-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="61b26-116">Aby otworzyć Edytor TreeNode, kliknij przycisk oznaczony wielokropkiem ( ![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości w oknie dialogowym właściwości.</span><span class="sxs-lookup"><span data-stu-id="61b26-116">To open the TreeNode Editor, click the ellipsis button ( ![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="61b26-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61b26-117">See also</span></span>

- [<span data-ttu-id="61b26-118">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="61b26-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="61b26-119">Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="61b26-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="61b26-120">Instrukcje: iterowanie wszystkich węzłów kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="61b26-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="61b26-121">Instrukcje: określanie, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="61b26-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="61b26-122">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="61b26-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
