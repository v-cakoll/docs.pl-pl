---
title: 'Porady: iterowanie wszystkich węzłów kontrolki TreeView formularzy systemu Windows'
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
ms.openlocfilehash: 89a2c1411ab64b4a20ad291165cfa6d83511c4c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532759"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>Porady: iterowanie wszystkich węzłów kontrolki TreeView formularzy systemu Windows
Czasami jest przydatne do sprawdzenia każdego węzła w formularzach systemu Windows <xref:System.Windows.Forms.TreeView> kontroli w celu wykonywania pewnych obliczeń na wartości węzła. Można wykonać tej operacji przy użyciu procedury cykliczne (metoda rekursywna w języku C# i C++), który iteruje po każdym węźle w każdej kolekcji drzewa.  
  
 Każdy <xref:System.Windows.Forms.TreeNode> obiekt w widoku drzewa ma właściwości, których można używać do nawigacji w widoku drzewa: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, i <xref:System.Windows.Forms.TreeNode.Parent%2A>. Wartość <xref:System.Windows.Forms.TreeNode.Parent%2A> właściwość jest węzła nadrzędnego bieżącego węzła. Węzły podrzędne bieżącego węzła, jeśli istnieją, są wyświetlane w jego <xref:System.Windows.Forms.TreeNode.Nodes%2A> właściwości. <xref:System.Windows.Forms.TreeView> Samego formantu ma <xref:System.Windows.Forms.TreeView.TopNode%2A> właściwość, która jest węzła głównego drzewa całego widoku.  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>Aby Iterowanie wszystkich węzłów formantu TreeView  
  
1.  Tworzenie procedury cykliczne (metoda rekursywna w języku C# i C++), która testów każdego węzła.  
  
2.  Wywołania tej procedury.  
  
     Poniższy przykład przedstawia sposób drukowania każdego <xref:System.Windows.Forms.TreeNode> obiektu <xref:System.Windows.Forms.TreeNode.Text%2A> właściwości:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Procedury rekursywne](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
