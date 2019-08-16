---
title: 'Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040075"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="036f2-102">Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="036f2-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>

<span data-ttu-id="036f2-103">Ponieważ kontrolka <xref:System.Windows.Forms.TreeView> Windows Forms wyświetla węzły w sposób hierarchiczny, podczas dodawania węzła należy zwrócić uwagę na to, co jego węzeł nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="036f2-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>

<span data-ttu-id="036f2-104">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.TreeView> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="036f2-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="036f2-105">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="036f2-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="036f2-106">Aby dodać lub usunąć węzły w projektancie</span><span class="sxs-lookup"><span data-stu-id="036f2-106">To add or remove nodes in the designer</span></span>

1. <span data-ttu-id="036f2-107"><xref:System.Windows.Forms.TreeView> Zaznacz kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="036f2-107">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>

2. <span data-ttu-id="036f2-108">W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio <xref:System.Windows.Forms.TreeView.Nodes%2A> .](./media/visual-studio-ellipsis-button.png)) obok właściwości.</span><span class="sxs-lookup"><span data-stu-id="036f2-108">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>

     <span data-ttu-id="036f2-109">Zostanie wyświetlony **Edytor TreeNode** .</span><span class="sxs-lookup"><span data-stu-id="036f2-109">The **TreeNode Editor** appears.</span></span>

3. <span data-ttu-id="036f2-110">Aby dodać węzły, musi istnieć węzeł główny; Jeśli jeszcze nie istnieje, należy najpierw dodać katalog główny, klikając przycisk **Dodaj element główny** .</span><span class="sxs-lookup"><span data-stu-id="036f2-110">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="036f2-111">Następnie można dodać węzły podrzędne, wybierając główny lub inny węzeł i klikając przycisk **Dodaj element podrzędny** .</span><span class="sxs-lookup"><span data-stu-id="036f2-111">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>

4. <span data-ttu-id="036f2-112">Aby usunąć węzły, wybierz węzeł, który chcesz usunąć, a następnie kliknij przycisk **Usuń** .</span><span class="sxs-lookup"><span data-stu-id="036f2-112">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="036f2-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="036f2-113">See also</span></span>

- [<span data-ttu-id="036f2-114">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="036f2-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="036f2-115">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="036f2-115">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="036f2-116">Instrukcje: Ustawianie ikon dla formantu Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="036f2-116">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="036f2-117">Instrukcje: Wykonaj iterację wszystkich węzłów kontrolki Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="036f2-117">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="036f2-118">Instrukcje: Określ, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="036f2-118">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="036f2-119">Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="036f2-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
