---
title: Dodawanie i usuwanie węzłów z kontrolką TreeView
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
ms.openlocfilehash: 02b3a7286798c6f2a6426e09c8fc6c18b74a6bf0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731958"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="8fb07-102">Porady: dodawanie i usuwanie węzłów za pomocą formantu TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8fb07-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="8fb07-103">Formant Windows Forms <xref:System.Windows.Forms.TreeView> przechowuje węzły najwyższego poziomu w swojej kolekcji <xref:System.Windows.Forms.TreeView.Nodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="8fb07-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="8fb07-104">Każdy <xref:System.Windows.Forms.TreeNode> również ma własną kolekcję <xref:System.Windows.Forms.TreeNode.Nodes%2A> do przechowywania węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="8fb07-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="8fb07-105">Obie właściwości kolekcji są typu <xref:System.Windows.Forms.TreeNodeCollection>, który zawiera standardowe elementy kolekcji, które umożliwiają dodawanie, usuwanie i zmienianie układu węzłów na jednym poziomie hierarchii węzłów.</span><span class="sxs-lookup"><span data-stu-id="8fb07-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="8fb07-106">Aby programowo dodać węzły</span><span class="sxs-lookup"><span data-stu-id="8fb07-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="8fb07-107">Użyj metody <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> właściwości <xref:System.Windows.Forms.TreeView.Nodes%2A> widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="8fb07-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
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
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="8fb07-108">Aby programowo usunąć węzły</span><span class="sxs-lookup"><span data-stu-id="8fb07-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="8fb07-109">Użyj metody <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> właściwości <xref:System.Windows.Forms.TreeView.Nodes%2A> widoku drzewa, aby usunąć pojedynczy węzeł, lub metodę <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A>, aby wyczyścić wszystkie węzły.</span><span class="sxs-lookup"><span data-stu-id="8fb07-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8fb07-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fb07-110">See also</span></span>

- [<span data-ttu-id="8fb07-111">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8fb07-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="8fb07-112">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="8fb07-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="8fb07-113">Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fb07-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="8fb07-114">Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fb07-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="8fb07-115">Instrukcje: określanie, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="8fb07-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="8fb07-116">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8fb07-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
