---
title: 'Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView'
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
ms.openlocfilehash: fe507c41de97e9332f3f27e453a476d992f86627
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732218"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Porady: dodawanie niestandardowych informacji do formantu TreeView lub ListView (Formularze systemu Windows)
Można utworzyć węzeł pochodny w kontrolce <xref:System.Windows.Forms.TreeView> Windows Forms lub element pochodny w kontrolce <xref:System.Windows.Forms.ListView>. Tworzenie wartości pochodnych pozwala na Dodawanie wymaganych pól, a także niestandardowych metod i konstruktorów do ich obsługi. Jednym z nich jest dołączenie obiektu klienta do każdego węzła drzewa lub elementu listy. Przykłady dotyczą kontrolki <xref:System.Windows.Forms.TreeView>, ale takie samo podejście może być używane w przypadku kontrolki <xref:System.Windows.Forms.ListView>.  
  
### <a name="to-derive-a-tree-node"></a>Aby utworzyć węzeł drzewa  
  
- Utwórz nową klasę węzła pochodzącą z klasy <xref:System.Windows.Forms.TreeNode>, która zawiera pole niestandardowe umożliwiające zarejestrowanie ścieżki pliku.  
  
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
  
1. Nowy węzeł drzewa pochodnego można użyć jako parametru do wywołania funkcji.  
  
     W poniższym przykładzie ścieżką ustawioną dla lokalizacji pliku tekstowego jest folder Moje dokumenty. Można to zrobić, ponieważ większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog. Pozwala to również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji.  
  
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
  
2. Jeśli przeszedł węzeł drzewa i jest on typem klasy <xref:System.Windows.Forms.TreeNode>, należy wykonać rzutowanie na klasę pochodną. Rzutowanie jest jawną konwersją z jednego typu obiektu na inny. Aby uzyskać więcej informacji na temat rzutowania, zobacz [konwersje niejawne i jawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (wizualizacja C#) lub [operator rzutowania: ()](/cpp/cpp/cast-operator-parens) (wizualizacja C++).  
  
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
- [ListView, kontrolka](listview-control-windows-forms.md)
