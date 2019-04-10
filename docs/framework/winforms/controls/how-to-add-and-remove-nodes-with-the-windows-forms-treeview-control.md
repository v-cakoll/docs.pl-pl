---
title: 'Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows'
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
ms.openlocfilehash: 4cbb5fbdb24790a7ddbce5c38060703c7ba7024a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326895"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="71484-102">Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="71484-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="71484-103">Formularze Windows <xref:System.Windows.Forms.TreeView> formant przechowuje węzłów najwyższego poziomu w jego <xref:System.Windows.Forms.TreeView.Nodes%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="71484-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="71484-104">Każdy <xref:System.Windows.Forms.TreeNode> ma również swój własny <xref:System.Windows.Forms.TreeNode.Nodes%2A> kolekcji do przechowywania jego węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="71484-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="71484-105">Obie te właściwości kolekcji mają wartości typu <xref:System.Windows.Forms.TreeNodeCollection>, udostępniającej elementy członkowskie kolekcji standardowych, które pozwalają na dodawanie, usuwanie i rozmieszczanie węzłów o jeden poziom w hierarchii węzła.</span><span class="sxs-lookup"><span data-stu-id="71484-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="71484-106">Aby programowo dodać węzły</span><span class="sxs-lookup"><span data-stu-id="71484-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="71484-107">Użyj <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metoda widok drzewa <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="71484-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
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
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="71484-108">Aby programowo usunąć węzły</span><span class="sxs-lookup"><span data-stu-id="71484-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="71484-109">Użyj <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metoda widok drzewa <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości do usunięcia jeden węzeł lub <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> metodę, aby wyczyścić wszystkie węzły.</span><span class="sxs-lookup"><span data-stu-id="71484-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="71484-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71484-110">See also</span></span>

- [<span data-ttu-id="71484-111">TreeView — Formant</span><span class="sxs-lookup"><span data-stu-id="71484-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="71484-112">TreeView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="71484-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="71484-113">Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="71484-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="71484-114">Instrukcje: iterowanie wszystkich węzłów kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="71484-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="71484-115">Instrukcje: określanie, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="71484-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="71484-116">Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="71484-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
