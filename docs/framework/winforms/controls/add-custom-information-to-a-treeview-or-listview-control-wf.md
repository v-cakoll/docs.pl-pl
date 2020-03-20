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
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="d4542-102">Porady: dodawanie niestandardowych informacji do formantu TreeView lub ListView (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="d4542-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="d4542-103">Węzeł pochodny można utworzyć w <xref:System.Windows.Forms.TreeView> formancie Windows Forms <xref:System.Windows.Forms.ListView> lub element pochodny w formancie.</span><span class="sxs-lookup"><span data-stu-id="d4542-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="d4542-104">Wyprowadzanie umożliwia dodawanie wszystkich pól, które są wymagane, a także niestandardowych metod i konstruktorów do ich obsługi.</span><span class="sxs-lookup"><span data-stu-id="d4542-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="d4542-105">Jednym z zastosowań tej funkcji jest dołączenie customer obiektu do każdego węzła drzewa lub elementu listy.</span><span class="sxs-lookup"><span data-stu-id="d4542-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="d4542-106">Przykłady w tym <xref:System.Windows.Forms.TreeView> miejscu są formantu, ale <xref:System.Windows.Forms.ListView> to samo podejście może służyć do formantu.</span><span class="sxs-lookup"><span data-stu-id="d4542-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="d4542-107">Aby wyprowadzić węzeł drzewa</span><span class="sxs-lookup"><span data-stu-id="d4542-107">To derive a tree node</span></span>  
  
- <span data-ttu-id="d4542-108">Utwórz nową klasę węzła, <xref:System.Windows.Forms.TreeNode> wywodzącą się z klasy, która ma pole niestandardowe do rejestrowania ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="d4542-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="d4542-109">Aby użyć węzła drzewa pochodnego</span><span class="sxs-lookup"><span data-stu-id="d4542-109">To use a derived tree node</span></span>  
  
1. <span data-ttu-id="d4542-110">Można użyć nowego węzła drzewa pochodnego jako parametru do wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d4542-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="d4542-111">W poniższym przykładzie ścieżką ustawioną dla lokalizacji pliku tekstowego jest folder Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d4542-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="d4542-112">Odbywa się to, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog.</span><span class="sxs-lookup"><span data-stu-id="d4542-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="d4542-113">Umożliwia to również użytkownikom z minimalnymi poziomami dostępu do systemu bezpieczne uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d4542-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
  
2. <span data-ttu-id="d4542-114">Jeśli zostanie przekazany węzeł drzewa i jest <xref:System.Windows.Forms.TreeNode> wpisany jako klasa, następnie należy rzutować do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="d4542-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="d4542-115">Rzutowanie jest jawną konwersją z jednego typu obiektu na inny.</span><span class="sxs-lookup"><span data-stu-id="d4542-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="d4542-116">Aby uzyskać więcej informacji na temat rzutowania, zobacz [konwersje niejawne i jawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [rzutowanie i konwersje typu](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#) lub [Operator rzutowania: ()](/cpp/cpp/cast-operator-parens) (Visual C++).</span><span class="sxs-lookup"><span data-stu-id="d4542-116">For more information on casting, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [Casting and type conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) (Visual C++).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4542-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4542-117">See also</span></span>

- [<span data-ttu-id="d4542-118">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d4542-118">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="d4542-119">ListView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d4542-119">ListView Control</span></span>](listview-control-windows-forms.md)
