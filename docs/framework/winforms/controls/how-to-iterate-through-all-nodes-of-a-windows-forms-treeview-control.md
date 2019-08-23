---
title: 'Instrukcje: iterowanie wszystkich węzłów kontrolki TreeView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
ms.openlocfilehash: 00a0f19803967f02795e3eade767786eecc1f4dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966550"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="5c411-102">Instrukcje: iterowanie wszystkich węzłów kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5c411-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="5c411-103">Czasami warto przeanalizować każdy węzeł w kontrolce Windows Forms <xref:System.Windows.Forms.TreeView> w celu wykonania obliczeń na wartościach węzła.</span><span class="sxs-lookup"><span data-stu-id="5c411-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="5c411-104">Tę operację można wykonać przy użyciu procedury cyklicznej (Metoda cykliczna C# w C++i), która iteruje przez każdy węzeł w każdej kolekcji drzewa.</span><span class="sxs-lookup"><span data-stu-id="5c411-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="5c411-105">Każdy <xref:System.Windows.Forms.TreeNode> obiekt w widoku drzewa ma właściwości, których można użyć do nawigowania w widoku drzewa: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A> <xref:System.Windows.Forms.TreeNode.NextNode%2A> <xref:System.Windows.Forms.TreeNode.PrevNode%2A>,,, i <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c411-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="5c411-106">Wartość <xref:System.Windows.Forms.TreeNode.Parent%2A> właściwości jest węzłem nadrzędnym bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="5c411-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="5c411-107">Węzły podrzędne bieżącego węzła, jeśli istnieją, są wyświetlane w jego <xref:System.Windows.Forms.TreeNode.Nodes%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5c411-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="5c411-108">Sama kontrolka <xref:System.Windows.Forms.TreeView.TopNode%2A> ma właściwość, która jest węzłem głównym całego widoku drzewa. <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="5c411-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="5c411-109">Aby wykonać iterację wszystkich węzłów kontrolki TreeView</span><span class="sxs-lookup"><span data-stu-id="5c411-109">To iterate through all nodes of the TreeView control</span></span>  
  
1. <span data-ttu-id="5c411-110">Utwórz procedurę cykliczną (metodę C# rekursywną C++w i), która testuje każdy węzeł.</span><span class="sxs-lookup"><span data-stu-id="5c411-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2. <span data-ttu-id="5c411-111">Wywołaj procedurę.</span><span class="sxs-lookup"><span data-stu-id="5c411-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="5c411-112">Poniższy przykład pokazuje, jak drukować <xref:System.Windows.Forms.TreeNode> <xref:System.Windows.Forms.TreeNode.Text%2A> właściwości poszczególnych obiektów:</span><span class="sxs-lookup"><span data-stu-id="5c411-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
    ```vb  
    Private Sub PrintRecursive(ByVal n As TreeNode)  
       System.Diagnostics.Debug.WriteLine(n.Text)  
       MessageBox.Show(n.Text)  
       Dim aNode As TreeNode  
       For Each aNode In n.Nodes  
          PrintRecursive(aNode)  
       Next  
    End Sub  
  
    ' Call the procedure using the top nodes of the treeview.  
    Private Sub CallRecursive(ByVal aTreeView As TreeView)  
       Dim n As TreeNode  
       For Each n In aTreeView.Nodes  
          PrintRecursive(n)  
       Next  
    End Sub  
    ```  
  
    ```csharp  
    private void PrintRecursive(TreeNode treeNode)  
    {  
       // Print the node.  
       System.Diagnostics.Debug.WriteLine(treeNode.Text);  
       MessageBox.Show(treeNode.Text);  
       // Print each node recursively.  
       foreach (TreeNode tn in treeNode.Nodes)  
       {  
          PrintRecursive(tn);  
       }  
    }  
  
    // Call the procedure using the TreeView.  
    private void CallRecursive(TreeView treeView)  
    {  
       // Print each node recursively.  
       TreeNodeCollection nodes = treeView.Nodes;  
       foreach (TreeNode n in nodes)  
       {  
          PrintRecursive(n);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void PrintRecursive( TreeNode^ treeNode )  
       {  
          // Print the node.  
          System::Diagnostics::Debug::WriteLine( treeNode->Text );  
          MessageBox::Show( treeNode->Text );  
  
          // Print each node recursively.  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(treeNode->Nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ tn = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( tn );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
  
       // Call the procedure using the TreeView.  
       void CallRecursive( TreeView^ treeView )  
       {  
          // Print each node recursively.  
          TreeNodeCollection^ nodes = treeView->Nodes;  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ n = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( n );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5c411-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c411-113">See also</span></span>

- [<span data-ttu-id="5c411-114">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5c411-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="5c411-115">Procedury rekursywne</span><span class="sxs-lookup"><span data-stu-id="5c411-115">Recursive Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
