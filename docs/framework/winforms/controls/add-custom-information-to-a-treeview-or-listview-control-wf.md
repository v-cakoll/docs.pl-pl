---
title: 'Jak: Dodawanie informacji niestandardowych do kontrolki TreeView lub ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
ms.openlocfilehash: faed586a5814526b0169ea46c8bb452e3777d8ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182426"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Porady: dodawanie niestandardowych informacji do formantu TreeView lub ListView (Formularze systemu Windows)
Węzeł pochodny można utworzyć w <xref:System.Windows.Forms.TreeView> formancie Windows Forms <xref:System.Windows.Forms.ListView> lub element pochodny w formancie. Wyprowadzanie umożliwia dodawanie wszystkich pól, które są wymagane, a także niestandardowych metod i konstruktorów do ich obsługi. Jednym z zastosowań tej funkcji jest dołączenie customer obiektu do każdego węzła drzewa lub elementu listy. Przykłady w tym <xref:System.Windows.Forms.TreeView> miejscu są formantu, ale <xref:System.Windows.Forms.ListView> to samo podejście może służyć do formantu.  
  
### <a name="to-derive-a-tree-node"></a>Aby wyprowadzić węzeł drzewa  
  
- Utwórz nową klasę węzła, <xref:System.Windows.Forms.TreeNode> wywodzącą się z klasy, która ma pole niestandardowe do rejestrowania ścieżki pliku.  
  
    ```vb  
    Class myTreeNode  
       Inherits TreeNode  
  
       Public FilePath As String  
  
       Sub New(ByVal fp As String)  
          MyBase.New()  
          FilePath = fp  
          Me.Text = fp.Substring(fp.LastIndexOf("\"))  
       End Sub  
    End Class  
    ```  
  
    ```csharp  
    class myTreeNode : TreeNode  
    {  
       public string FilePath;  
  
       public myTreeNode(string fp)  
       {  
          FilePath = fp;  
          this.Text = fp.Substring(fp.LastIndexOf("\\"));  
       }  
    }  
    ```  
  
    ```cpp  
    ref class myTreeNode : public TreeNode  
    {  
    public:  
       System::String ^ FilePath;  
  
       myTreeNode(System::String ^ fp)  
       {  
          FilePath = fp;  
          this->Text = fp->Substring(fp->LastIndexOf("\\"));  
       }  
    };  
    ```  
  
### <a name="to-use-a-derived-tree-node"></a>Aby użyć węzła drzewa pochodnego  
  
1. Można użyć nowego węzła drzewa pochodnego jako parametru do wywołania funkcji.  
  
     W poniższym przykładzie ścieżką ustawioną dla lokalizacji pliku tekstowego jest folder Moje dokumenty. Odbywa się to, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog. Umożliwia to również użytkownikom z minimalnymi poziomami dostępu do systemu bezpieczne uruchamianie aplikacji.  
  
    ```vb  
    ' You should replace the bold text file
    ' in the sample below with a text file of your own choosing.  
    TreeView1.Nodes.Add(New myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\ TextFile.txt ") )  
    ```  
  
    ```csharp  
    // You should replace the bold text file
    // in the sample below with a text file of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    treeView1.Nodes.Add(new myTreeNode(System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\TextFile.txt") );  
    ```  
  
    ```cpp  
    // You should replace the bold text file
    // in the sample below with a text file of your own choosing.  
    treeView1->Nodes->Add(new myTreeNode(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\TextFile.txt")));  
    ```  
  
2. Jeśli zostanie przekazany węzeł drzewa i jest <xref:System.Windows.Forms.TreeNode> wpisany jako klasa, następnie należy rzutować do klasy pochodnej. Rzutowanie jest jawną konwersją z jednego typu obiektu na inny. Aby uzyskać więcej informacji na temat rzutowania, zobacz [konwersje niejawne i jawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [rzutowanie i konwersje typu](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#) lub [Operator rzutowania: ()](/cpp/cpp/cast-operator-parens) (Visual C++).  
  
    ```vb  
    Public Sub TreeView1_AfterSelect(ByVal sender As Object, ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       Dim mynode As myTreeNode  
       mynode = CType(e.node, myTreeNode)  
       MessageBox.Show("Node selected is " & mynode.filepath)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,  
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       myTreeNode myNode = (myTreeNode)e.Node;  
       MessageBox.Show("Node selected is " + myNode.FilePath);  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          myTreeNode ^ myNode = safe_cast<myTreeNode^>(e->Node);  
          MessageBox::Show(String::Concat("Node selected is ",
             myNode->FilePath));  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [ListView, kontrolka](listview-control-windows-forms.md)
