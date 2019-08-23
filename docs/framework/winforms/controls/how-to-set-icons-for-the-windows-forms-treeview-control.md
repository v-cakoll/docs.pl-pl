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
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909809"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="4758a-102">Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4758a-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="4758a-103">Kontrolka <xref:System.Windows.Forms.TreeView> Windows Forms może wyświetlać ikony obok każdego węzła.</span><span class="sxs-lookup"><span data-stu-id="4758a-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="4758a-104">Ikony są umieszczane bezpośrednio po lewej stronie tekstu węzła.</span><span class="sxs-lookup"><span data-stu-id="4758a-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="4758a-105">Aby wyświetlić te ikony, należy skojarzyć widok drzewa z <xref:System.Windows.Forms.ImageList> kontrolką.</span><span class="sxs-lookup"><span data-stu-id="4758a-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="4758a-106">Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnik ImageList](imagelist-component-windows-forms.md) i [instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)ImageList Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4758a-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4758a-107">Usterka w programie Microsoft .NET Framework w wersji 1,1 uniemożliwia wyświetlanie obrazów <xref:System.Windows.Forms.TreeView> w węzłach, gdy <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>aplikacja jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="4758a-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4758a-108">Aby obejść ten błąd, wywołaj <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> `Main` metodę natychmiast po wywołaniu <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="4758a-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="4758a-109">Ta usterka została naprawiona w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="4758a-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="4758a-110">Aby wyświetlić obrazy w widoku drzewa</span><span class="sxs-lookup"><span data-stu-id="4758a-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="4758a-111"><xref:System.Windows.Forms.TreeView> Ustaw Właściwość<xref:System.Windows.Forms.TreeView.ImageList%2A> kontrolki na istniejącą <xref:System.Windows.Forms.ImageList> kontrolkę, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="4758a-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="4758a-112">Te właściwości można ustawić w projektancie przy użyciu okno Właściwości lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4758a-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="4758a-113">Ustaw właściwości węzła <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> i <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> .</span><span class="sxs-lookup"><span data-stu-id="4758a-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="4758a-114">Właściwość określa obraz wyświetlany dla Stanów normalne i rozwinięte węzła, <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> a właściwość określa obraz wyświetlany dla wybranego stanu węzła. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A></span><span class="sxs-lookup"><span data-stu-id="4758a-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="4758a-115">Te właściwości można ustawić w kodzie lub w edytorze TreeNode.</span><span class="sxs-lookup"><span data-stu-id="4758a-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="4758a-116">Aby otworzyć Edytor TreeNode, kliknij przycisk wielokropka ( ![przycisk wielokropka (...) w okno właściwości programu Visual](./media/visual-studio-ellipsis-button.png)Studio) obok <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="4758a-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4758a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4758a-117">See also</span></span>

- [<span data-ttu-id="4758a-118">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="4758a-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="4758a-119">Instrukcje: Dodawanie i usuwanie węzłów za pomocą kontrolki TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4758a-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="4758a-120">Instrukcje: Wykonaj iterację wszystkich węzłów kontrolki Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="4758a-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="4758a-121">Instrukcje: Określ, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="4758a-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="4758a-122">Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4758a-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
