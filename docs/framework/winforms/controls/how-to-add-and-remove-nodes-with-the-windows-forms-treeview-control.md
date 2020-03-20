---
title: Dodawanie i usuwanie węzłów za pomocą kontrolki TreeView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
ms.openlocfilehash: f1e74e6d2f827167c32a6955b3010b59cb2f85b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142215"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="73438-102">Porady: dodawanie i usuwanie węzłów za pomocą formantu TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="73438-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="73438-103">Formant <xref:System.Windows.Forms.TreeView> Formularze systemu Windows przechowuje <xref:System.Windows.Forms.TreeView.Nodes%2A> węzły najwyższego poziomu w swojej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="73438-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="73438-104">Każdy <xref:System.Windows.Forms.TreeNode> ma również <xref:System.Windows.Forms.TreeNode.Nodes%2A> własną kolekcję do przechowywania jego węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="73438-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="73438-105">Obie właściwości kolekcji <xref:System.Windows.Forms.TreeNodeCollection>są typu , który zapewnia standardowe elementy członkowskie kolekcji, które umożliwiają dodawanie, usuwanie i zmienianie rozmieszczenia węzłów na jednym poziomie hierarchii węzłów.</span><span class="sxs-lookup"><span data-stu-id="73438-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="73438-106">Aby programowo dodać węzły</span><span class="sxs-lookup"><span data-stu-id="73438-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="73438-107">Użyj <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metody <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="73438-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="73438-108">Aby programowo usunąć węzły</span><span class="sxs-lookup"><span data-stu-id="73438-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="73438-109">Użyj <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metody <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości widoku drzewa, aby usunąć pojedynczy węzeł <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> lub metodę, aby wyczyścić wszystkie węzły.</span><span class="sxs-lookup"><span data-stu-id="73438-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="73438-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73438-110">See also</span></span>

- [<span data-ttu-id="73438-111">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="73438-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="73438-112">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="73438-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="73438-113">Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73438-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="73438-114">Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73438-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="73438-115">Instrukcje: określanie, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="73438-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="73438-116">Porady: dodawanie niestandardowych informacji do formantu TreeView lub ListView (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="73438-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
