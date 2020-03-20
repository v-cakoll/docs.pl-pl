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
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Porady: dodawanie i usuwanie węzłów za pomocą formantu TreeView formularzy systemu Windows
Formant <xref:System.Windows.Forms.TreeView> Formularze systemu Windows przechowuje <xref:System.Windows.Forms.TreeView.Nodes%2A> węzły najwyższego poziomu w swojej kolekcji. Każdy <xref:System.Windows.Forms.TreeNode> ma również <xref:System.Windows.Forms.TreeNode.Nodes%2A> własną kolekcję do przechowywania jego węzłów podrzędnych. Obie właściwości kolekcji <xref:System.Windows.Forms.TreeNodeCollection>są typu , który zapewnia standardowe elementy członkowskie kolekcji, które umożliwiają dodawanie, usuwanie i zmienianie rozmieszczenia węzłów na jednym poziomie hierarchii węzłów.  
  
### <a name="to-add-nodes-programmatically"></a>Aby programowo dodać węzły  
  
1. Użyj <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metody <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości widoku drzewa.  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>Aby programowo usunąć węzły  
  
1. Użyj <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metody <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości widoku drzewa, aby usunąć pojedynczy węzeł <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> lub metodę, aby wyczyścić wszystkie węzły.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [TreeView, kontrolka — omówienie](treeview-control-overview-windows-forms.md)
- [Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: określanie, który węzeł TreeView został kliknięty](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Porady: dodawanie niestandardowych informacji do formantu TreeView lub ListView (Formularze systemu Windows)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
