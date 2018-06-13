---
title: 'Porady: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Formularze systemu Windows)'
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
ms.openlocfilehash: b4131504e5c5d7f2075c72c72b98153c783000d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527420"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Porady: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Formularze systemu Windows)
Można utworzyć pochodnej węzeł w formularzach systemu Windows <xref:System.Windows.Forms.TreeView> formant lub pochodnego elementu w <xref:System.Windows.Forms.ListView> formantu. Tworzenie wartości pochodnych umożliwia dodanie wszystkie pola, które są wymagane, a także niestandardowe metody i konstruktory ich obsługę. Jedno użycie tej funkcji jest można dołączyć obiektu klienta do każdego drzewa węzła lub elementu listy. Przykłady w tym miejscu są dla <xref:System.Windows.Forms.TreeView> sterowania, ale same podejście może służyć do <xref:System.Windows.Forms.ListView> formantu.  
  
### <a name="to-derive-a-tree-node"></a>Do uzyskania węzeł drzewa  
  
-   Utwórz nową klasę węzeł pochodzi od <xref:System.Windows.Forms.TreeNode> klasy, która ma pole niestandardowe, aby zarejestrować ścieżkę pliku.  
  
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
  
### <a name="to-use-a-derived-tree-node"></a>Aby użyć węzła drzewa pochodne  
  
1.  Nowy węzeł drzewa pochodnej można użyć jako parametru do wywołania funkcji.  
  
     W poniższym przykładzie ścieżka zestawu dla lokalizacji pliku tekstowego jest folder Moje dokumenty. Można to zrobić, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu. To umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.  
  
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
    treeView1.Nodes.Add(new myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
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
  
2.  Jeśli węzeł drzewa są przekazywane i jest wpisana jako <xref:System.Windows.Forms.TreeNode> klasy, musisz wykonać rzutowanie do klasy pochodnej. Rzutowanie jest jawnej konwersji typu obiektu do innego. Aby uzyskać więcej informacji na rzutowanie, zobacz [Konwersje jawne i niejawne](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [(Operator)](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#), lub [Operator rzutowania: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).  
  
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
 [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
