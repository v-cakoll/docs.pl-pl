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
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>Porady: iterowanie wszystkich węzłów kontrolki TreeView formularzy systemu Windows
Czasami warto przeanalizować każdy węzeł w kontrolce <xref:System.Windows.Forms.TreeView> Windows Forms w celu wykonania obliczeń na wartościach węzła. Tę operację można wykonać przy użyciu procedury cyklicznej (Metoda cykliczna C# w C++i), która iteruje przez każdy węzeł w każdej kolekcji drzewa.  
  
 Każdy obiekt <xref:System.Windows.Forms.TreeNode> w widoku drzewa ma właściwości, których można użyć do nawigowania w widoku drzewa: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>i <xref:System.Windows.Forms.TreeNode.Parent%2A>. Wartość właściwości <xref:System.Windows.Forms.TreeNode.Parent%2A> jest węzłem nadrzędnym bieżącego węzła. Węzły podrzędne bieżącego węzła, jeśli istnieją, są wymienione w jego właściwości <xref:System.Windows.Forms.TreeNode.Nodes%2A>. Sama kontrolka <xref:System.Windows.Forms.TreeView> ma właściwość <xref:System.Windows.Forms.TreeView.TopNode%2A>, która jest węzłem głównym całego widoku drzewa.  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>Aby wykonać iterację wszystkich węzłów kontrolki TreeView  
  
1. Utwórz procedurę cykliczną (metodę C# rekursywną C++w i), która testuje każdy węzeł.  
  
2. Wywołaj procedurę.  
  
     Poniższy przykład pokazuje, jak drukować każdą właściwość <xref:System.Windows.Forms.TreeNode.Text%2A> obiektu <xref:System.Windows.Forms.TreeNode>:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [Procedury rekursywne](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
