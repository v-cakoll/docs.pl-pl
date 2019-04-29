---
title: 'Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ecf0b758a9c45a0354a68b6cbfecdb1c49ab390f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640381"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="18581-102">Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="18581-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="18581-103">Ponieważ formularzy Windows Forms <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla węzły w hierarchiczny sposób, podczas dodawania węzła należy zwrócić uwagę na to swojego węzła nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="18581-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="18581-104">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.TreeView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="18581-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="18581-105">Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="18581-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18581-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="18581-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="18581-107">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="18581-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="18581-108">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="18581-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="18581-109">Aby dodać lub usunąć węzły w Projektancie</span><span class="sxs-lookup"><span data-stu-id="18581-109">To add or remove nodes in the designer</span></span>  
  
1. <span data-ttu-id="18581-110">Wybierz <xref:System.Windows.Forms.TreeView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="18581-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2. <span data-ttu-id="18581-111">W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="18581-111">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="18581-112">**TreeNode Editor** pojawia się.</span><span class="sxs-lookup"><span data-stu-id="18581-112">The **TreeNode Editor** appears.</span></span>  
  
3. <span data-ttu-id="18581-113">Aby dodać węzły, węzeł główny musi istnieć; Jeśli nie istnieje, należy najpierw dodać katalog główny, klikając **Dodawanie głównego** przycisku.</span><span class="sxs-lookup"><span data-stu-id="18581-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="18581-114">Następnie można dodać węzły podrzędne, wybierając głównego lub dowolnego innego węzła i klikając **Dodaj element podrzędny** przycisku.</span><span class="sxs-lookup"><span data-stu-id="18581-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4. <span data-ttu-id="18581-115">Aby usunąć węzły, wybierz węzeł, aby usunąć, a następnie kliknij przycisk **Usuń** przycisku.</span><span class="sxs-lookup"><span data-stu-id="18581-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18581-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18581-116">See also</span></span>

- [<span data-ttu-id="18581-117">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="18581-117">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="18581-118">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="18581-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="18581-119">Instrukcje: Ustawienie ikon dla kontrolki TreeView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="18581-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="18581-120">Instrukcje: Iterowanie wszystkich węzłów kontrolki TreeView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="18581-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="18581-121">Instrukcje: Określanie, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="18581-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="18581-122">Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="18581-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
