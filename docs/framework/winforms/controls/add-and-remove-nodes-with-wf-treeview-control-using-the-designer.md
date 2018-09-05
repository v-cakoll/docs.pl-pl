---
title: 'Porady: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 95f3f097d8e01828f2727bac742c752b656019e5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565773"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="99719-102">Porady: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="99719-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="99719-103">Ponieważ formularzy Windows Forms <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla węzły w hierarchiczny sposób, podczas dodawania węzła należy zwrócić uwagę na to swojego węzła nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="99719-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="99719-104">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.TreeView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="99719-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="99719-105">Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="99719-105">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99719-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="99719-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="99719-107">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="99719-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="99719-108">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="99719-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="99719-109">Aby dodać lub usunąć węzły w Projektancie</span><span class="sxs-lookup"><span data-stu-id="99719-109">To add or remove nodes in the designer</span></span>  
  
1.  <span data-ttu-id="99719-110">Wybierz <xref:System.Windows.Forms.TreeView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="99719-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2.  <span data-ttu-id="99719-111">W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="99719-111">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="99719-112">**TreeNode Editor** pojawia się.</span><span class="sxs-lookup"><span data-stu-id="99719-112">The **TreeNode Editor** appears.</span></span>  
  
3.  <span data-ttu-id="99719-113">Aby dodać węzły, węzeł główny musi istnieć; Jeśli nie istnieje, należy najpierw dodać katalog główny, klikając **Dodawanie głównego** przycisku.</span><span class="sxs-lookup"><span data-stu-id="99719-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="99719-114">Następnie można dodać węzły podrzędne, wybierając głównego lub dowolnego innego węzła i klikając **Dodaj element podrzędny** przycisku.</span><span class="sxs-lookup"><span data-stu-id="99719-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4.  <span data-ttu-id="99719-115">Aby usunąć węzły, wybierz węzeł, aby usunąć, a następnie kliknij przycisk **Usuń** przycisku.</span><span class="sxs-lookup"><span data-stu-id="99719-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99719-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99719-116">See Also</span></span>  
 [<span data-ttu-id="99719-117">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="99719-117">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="99719-118">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="99719-118">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="99719-119">Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="99719-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="99719-120">Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="99719-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="99719-121">Instrukcje: określanie, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="99719-121">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="99719-122">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="99719-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
