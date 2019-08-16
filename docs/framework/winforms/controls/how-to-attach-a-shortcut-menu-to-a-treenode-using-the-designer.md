---
title: 'Instrukcje: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040447"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="5ffc3-102">Instrukcje: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="5ffc3-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="5ffc3-103">Kontrolka <xref:System.Windows.Forms.TreeView> Windows Forms Wyświetla hierarchię węzłów, podobnie jak pliki i foldery wyświetlane w lewym okienku funkcji Eksplorator Windows w systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="5ffc3-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="5ffc3-104">Ustawiając <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość, można zapewnić użytkownikowi operacje zależne od kontekstu po <xref:System.Windows.Forms.TreeView> kliknięciu kontrolki prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="5ffc3-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="5ffc3-105">Kojarząc <xref:System.Windows.Forms.ContextMenuStrip> składnik z poszczególnymi <xref:System.Windows.Forms.TreeNode> elementami, można dodać dostosowany poziom funkcji menu <xref:System.Windows.Forms.TreeView> skrótów do kontrolek.</span><span class="sxs-lookup"><span data-stu-id="5ffc3-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="5ffc3-106">Aby skojarzyć menu skrótów z elementem TreeNode w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="5ffc3-106">To associate a shortcut menu with a TreeNode at design time</span></span>

1. <span data-ttu-id="5ffc3-107">Dodaj kontrolkę do formularza, a następnie Dodaj do niej <xref:System.Windows.Forms.TreeView> węzły. <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="5ffc3-107">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="5ffc3-108">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie węzłów za pomocą kontrolki](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)TreeView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5ffc3-108">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>

2. <span data-ttu-id="5ffc3-109"><xref:System.Windows.Forms.ContextMenuStrip> Dodaj składnik do formularza, a następnie Dodaj elementy menu do menu skrótów, które reprezentuje operacje na poziomie węzła, które mają być dostępne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5ffc3-109">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="5ffc3-110">Aby uzyskać więcej informacji, zobacz [jak: Dodaj elementy menu do ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).</span><span class="sxs-lookup"><span data-stu-id="5ffc3-110">For more information, see [How to: Add Menu Items to a ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>

3. <span data-ttu-id="5ffc3-111">Otwórz ponownie okno dialogowe **TreeNodeEditor** dla <xref:System.Windows.Forms.TreeView> kontrolki, wybierz węzeł do edycji i ustaw jego <xref:System.Windows.Forms.ContextMenuStrip> właściwość na dodane menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="5ffc3-111">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>

4. <span data-ttu-id="5ffc3-112">Gdy ta właściwość jest ustawiona, menu skrótów będzie wyświetlane po kliknięciu prawym przyciskiem myszy węzła.</span><span class="sxs-lookup"><span data-stu-id="5ffc3-112">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>

     <span data-ttu-id="5ffc3-113">Ponadto należy napisać kod, aby obsłużyć <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla tych elementów menu.</span><span class="sxs-lookup"><span data-stu-id="5ffc3-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ffc3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ffc3-114">See also</span></span>

- [<span data-ttu-id="5ffc3-115">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5ffc3-115">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="5ffc3-116">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="5ffc3-116">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="5ffc3-117">ContextMenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5ffc3-117">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
