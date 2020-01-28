---
title: Wykonaj iterację wszystkich węzłów kontrolki TreeView
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
ms.openlocfilehash: 010932fa3fdfaa907325b9934682dcbf889265c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736366"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="eb7bd-102">Porady: iterowanie wszystkich węzłów kontrolki TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="eb7bd-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="eb7bd-103">Czasami warto przeanalizować każdy węzeł w kontrolce <xref:System.Windows.Forms.TreeView> Windows Forms w celu wykonania obliczeń na wartościach węzła.</span><span class="sxs-lookup"><span data-stu-id="eb7bd-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="eb7bd-104">Tę operację można wykonać przy użyciu procedury cyklicznej (Metoda cykliczna C# w C++i), która iteruje przez każdy węzeł w każdej kolekcji drzewa.</span><span class="sxs-lookup"><span data-stu-id="eb7bd-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="eb7bd-105">Każdy obiekt <xref:System.Windows.Forms.TreeNode> w widoku drzewa ma właściwości, których można użyć do nawigowania w widoku drzewa: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>i <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span><span class="sxs-lookup"><span data-stu-id="eb7bd-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="eb7bd-106">Wartość właściwości <xref:System.Windows.Forms.TreeNode.Parent%2A> jest węzłem nadrzędnym bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="eb7bd-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="eb7bd-107">Węzły podrzędne bieżącego węzła, jeśli istnieją, są wymienione w jego właściwości <xref:System.Windows.Forms.TreeNode.Nodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="eb7bd-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="eb7bd-108">Sama kontrolka <xref:System.Windows.Forms.TreeView> ma właściwość <xref:System.Windows.Forms.TreeView.TopNode%2A>, która jest węzłem głównym całego widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="eb7bd-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="eb7bd-109">Aby wykonać iterację wszystkich węzłów kontrolki TreeView</span><span class="sxs-lookup"><span data-stu-id="eb7bd-109">To iterate through all nodes of the TreeView control</span></span>  
  
1. <span data-ttu-id="eb7bd-110">Utwórz procedurę cykliczną (metodę C# rekursywną C++w i), która testuje każdy węzeł.</span><span class="sxs-lookup"><span data-stu-id="eb7bd-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2. <span data-ttu-id="eb7bd-111">Wywołaj procedurę.</span><span class="sxs-lookup"><span data-stu-id="eb7bd-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="eb7bd-112">Poniższy przykład pokazuje, jak drukować każdą właściwość <xref:System.Windows.Forms.TreeNode.Text%2A> obiektu <xref:System.Windows.Forms.TreeNode>:</span><span class="sxs-lookup"><span data-stu-id="eb7bd-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb7bd-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb7bd-113">See also</span></span>

- [<span data-ttu-id="eb7bd-114">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="eb7bd-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="eb7bd-115">Procedury rekursywne</span><span class="sxs-lookup"><span data-stu-id="eb7bd-115">Recursive Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
