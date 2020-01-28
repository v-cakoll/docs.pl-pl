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
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Porady: dodawanie i usuwanie węzłów za pomocą formantu TreeView formularzy systemu Windows
Formant Windows Forms <xref:System.Windows.Forms.TreeView> przechowuje węzły najwyższego poziomu w swojej kolekcji <xref:System.Windows.Forms.TreeView.Nodes%2A>. Każdy <xref:System.Windows.Forms.TreeNode> również ma własną kolekcję <xref:System.Windows.Forms.TreeNode.Nodes%2A> do przechowywania węzłów podrzędnych. Obie właściwości kolekcji są typu <xref:System.Windows.Forms.TreeNodeCollection>, który zawiera standardowe elementy kolekcji, które umożliwiają dodawanie, usuwanie i zmienianie układu węzłów na jednym poziomie hierarchii węzłów.  
  
### <a name="to-add-nodes-programmatically"></a>Aby programowo dodać węzły  
  
1. Użyj metody <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> właściwości <xref:System.Windows.Forms.TreeView.Nodes%2A> widoku drzewa.  
  
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
  
1. Użyj metody <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> właściwości <xref:System.Windows.Forms.TreeView.Nodes%2A> widoku drzewa, aby usunąć pojedynczy węzeł, lub metodę <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A>, aby wyczyścić wszystkie węzły.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [TreeView, kontrolka — omówienie](treeview-control-overview-windows-forms.md)
- [Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: określanie, który węzeł TreeView został kliknięty](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
