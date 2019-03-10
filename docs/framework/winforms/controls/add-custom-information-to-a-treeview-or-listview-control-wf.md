---
title: 'Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)'
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
ms.openlocfilehash: 40ac3fb3a148c351cf5acca235569e2a1a439a3e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709679"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)
Można utworzyć pochodnej węzeł w formularzach Windows <xref:System.Windows.Forms.TreeView> formantu lub pochodny element w <xref:System.Windows.Forms.ListView> kontroli. Tworzenie wartości pochodnych umożliwia Dodaj dowolne pola, które są wymagane, a także niestandardowych metod i konstruktorów do ich obsługi. Jest jedno użycie tej funkcji można dołączyć obiektu klienta do każdego elementu węzła lub listy drzewa. Podane tutaj przykłady dotyczą <xref:System.Windows.Forms.TreeView> kontroli, ale to samo podejście pozwala <xref:System.Windows.Forms.ListView> kontroli.  
  
### <a name="to-derive-a-tree-node"></a>Aby uzyskać pochodny węzeł drzewa  
  
-   Utwórz nową klasę węzła pochodną <xref:System.Windows.Forms.TreeNode> klasy, która zawiera pole niestandardowe do rejestrowania ścieżki do pliku.  
  
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
  
1.  Nowy węzeł drzewa pochodnej służy jako parametr do wywołania funkcji.  
  
     W poniższym przykładzie ścieżka lokalizacji pliku tekstowego jest folder Moje dokumenty. Można to zrobić, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu. Ponadto pozwala to użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.  
  
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
  
2.  Jeśli są przekazywane węzła drzewa, a ma <xref:System.Windows.Forms.TreeNode> klasy, musisz wykonać rzutowanie do klasy pochodnej. Rzutowanie jest jawna konwersja z jednego typu obiektu do drugiego. Aby uzyskać więcej informacji na temat rzutowania, zobacz [Konwersje jawne i niejawne](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [— Operator ()](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#), lub [Operator rzutowania: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) .  
  
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
  
## <a name="see-also"></a>Zobacz także
- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [Kontrolka ListView](listview-control-windows-forms.md)
