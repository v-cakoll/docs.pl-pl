---
title: 'Instrukcje: Dołączanie ShortCut Menu do węzła TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: 7c9e2a2fc51628116a7762e343f36f9f7e93fe67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685207"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a><span data-ttu-id="494a1-102">Instrukcje: Dołączanie ShortCut Menu do węzła TreeView</span><span class="sxs-lookup"><span data-stu-id="494a1-102">How to: Attach a ShortCut Menu to a TreeView Node</span></span>
<span data-ttu-id="494a1-103">Formularze Windows <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla hierarchię węzłów, podobnie jak pliki i foldery, wyświetlana w okienku po lewej stronie Eksploratora Windows.</span><span class="sxs-lookup"><span data-stu-id="494a1-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of Windows Explorer.</span></span> <span data-ttu-id="494a1-104">Ustawiając <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwości, można zapewnić kontekstową operacje użytkownika po ich prawym przyciskiem myszy <xref:System.Windows.Forms.TreeView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="494a1-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="494a1-105">Kojarząc <xref:System.Windows.Forms.ContextMenuStrip> składnika za pomocą poszczególnych <xref:System.Windows.Forms.TreeNode> elementy, można dodać niestandardowe poziom funkcjonalności menu skrótów do Twojej <xref:System.Windows.Forms.TreeView> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="494a1-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a><span data-ttu-id="494a1-106">Aby programowo kojarzenie menu skrótów za pomocą elementu TreeNode</span><span class="sxs-lookup"><span data-stu-id="494a1-106">To associate a shortcut menu with a TreeNode programmatically</span></span>  
  
1.  <span data-ttu-id="494a1-107">Utwórz wystąpienie <xref:System.Windows.Forms.TreeView> sterować za pomocą właściwości, utworzenie głównego <xref:System.Windows.Forms.TreeNode>, a następnie dodaj węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="494a1-107">Instantiate a <xref:System.Windows.Forms.TreeView> control with the appropriate property settings, create a root <xref:System.Windows.Forms.TreeNode>, and then add subnodes.</span></span>  
  
2.  <span data-ttu-id="494a1-108">Utwórz wystąpienie <xref:System.Windows.Forms.ContextMenuStrip> składnik, a następnie dodaj <xref:System.Windows.Forms.ToolStripMenuItem> dla każdej operacji, które chcesz udostępnić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="494a1-108">Instantiate a <xref:System.Windows.Forms.ContextMenuStrip> component, and then add a <xref:System.Windows.Forms.ToolStripMenuItem> for each operation you want to make available at run time.</span></span>  
  
3.  <span data-ttu-id="494a1-109">Ustaw <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> własności odpowiednie <xref:System.Windows.Forms.TreeNode> do menu skrótów, możesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="494a1-109">Set the <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> property of the appropriate <xref:System.Windows.Forms.TreeNode> to the shortcut menu you create.</span></span>  
  
4.  <span data-ttu-id="494a1-110">Gdy ta właściwość jest ustawiona, zostanie wyświetlone menu skrótów, po kliknięciu prawym przyciskiem myszy węzeł.</span><span class="sxs-lookup"><span data-stu-id="494a1-110">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
 <span data-ttu-id="494a1-111">Poniższy przykład kodu tworzy podstawową <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ContextMenuStrip> skojarzonego z certyfikatem głównym <xref:System.Windows.Forms.TreeNode> z <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="494a1-111">The following code example creates a basic <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ContextMenuStrip> associated with the root <xref:System.Windows.Forms.TreeNode> of the <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="494a1-112">Trzeba będzie dostosować opcje menu do tych, które mieszczą się <xref:System.Windows.Forms.TreeView> tworzysz.</span><span class="sxs-lookup"><span data-stu-id="494a1-112">You will need to customize the menu choices to those that fit the <xref:System.Windows.Forms.TreeView> you are developing.</span></span> <span data-ttu-id="494a1-113">Ponadto, można napisać kod obsługujący <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla tych elementów menu.</span><span class="sxs-lookup"><span data-stu-id="494a1-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="494a1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="494a1-114">See also</span></span>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="494a1-115">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="494a1-115">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
