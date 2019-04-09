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
ms.openlocfilehash: e8e5ef299ca7b5555a02e86e4422ca9f5b8a584f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199716"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>Instrukcje: iterowanie wszystkich węzłów kontrolki TreeView formularzy systemu Windows
Czasami jest to przydatne sprawdzić każdy węzeł w formularzach Windows <xref:System.Windows.Forms.TreeView> kontroli w celu wykonywania pewnych obliczeń na podstawie wartości węzła. Tę operację można wykonać przy użyciu procedury cykliczne (cykliczne method in Class metoda C# i C++) który iteruje po każdym węźle w każdej kolekcji drzewa.  
  
 Każdy <xref:System.Windows.Forms.TreeNode> obiekt w widoku drzewa ma właściwości, które umożliwiają nawigowanie w widoku drzewa: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, i <xref:System.Windows.Forms.TreeNode.Parent%2A>. Wartość <xref:System.Windows.Forms.TreeNode.Parent%2A> właściwość ma węzła nadrzędnego bieżącego węzła. Węzły podrzędne bieżącego węzła, jeśli istnieją, są wyświetlane w jego <xref:System.Windows.Forms.TreeNode.Nodes%2A> właściwości. <xref:System.Windows.Forms.TreeView> Sama kontrolka ma <xref:System.Windows.Forms.TreeView.TopNode%2A> właściwość, która jest węzeł główny w widok całego drzewa.  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>Aby Iterowanie wszystkich węzłów kontrolki TreeView  
  
1.  Tworzenie procedury cykliczne (cykliczne method in Class metoda C# i C++), które testują każdego węzła.  
  
2.  Wywołania tej procedury.  
  
     Poniższy przykład pokazuje, jak drukowanie każdego <xref:System.Windows.Forms.TreeNode> obiektu <xref:System.Windows.Forms.TreeNode.Text%2A> właściwości:  
  
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

- [TreeView — Formant](treeview-control-windows-forms.md)
- [Procedury rekursywne](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
