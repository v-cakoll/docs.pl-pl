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
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="37c40-102">Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="37c40-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="37c40-103">Można utworzyć pochodnej węzeł w formularzach Windows <xref:System.Windows.Forms.TreeView> formantu lub pochodny element w <xref:System.Windows.Forms.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="37c40-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="37c40-104">Tworzenie wartości pochodnych umożliwia Dodaj dowolne pola, które są wymagane, a także niestandardowych metod i konstruktorów do ich obsługi.</span><span class="sxs-lookup"><span data-stu-id="37c40-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="37c40-105">Jest jedno użycie tej funkcji można dołączyć obiektu klienta do każdego elementu węzła lub listy drzewa.</span><span class="sxs-lookup"><span data-stu-id="37c40-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="37c40-106">Podane tutaj przykłady dotyczą <xref:System.Windows.Forms.TreeView> kontroli, ale to samo podejście pozwala <xref:System.Windows.Forms.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="37c40-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="37c40-107">Aby uzyskać pochodny węzeł drzewa</span><span class="sxs-lookup"><span data-stu-id="37c40-107">To derive a tree node</span></span>  
  
-   <span data-ttu-id="37c40-108">Utwórz nową klasę węzła pochodną <xref:System.Windows.Forms.TreeNode> klasy, która zawiera pole niestandardowe do rejestrowania ścieżki do pliku.</span><span class="sxs-lookup"><span data-stu-id="37c40-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="37c40-109">Aby użyć węzła drzewa pochodne</span><span class="sxs-lookup"><span data-stu-id="37c40-109">To use a derived tree node</span></span>  
  
1.  <span data-ttu-id="37c40-110">Nowy węzeł drzewa pochodnej służy jako parametr do wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="37c40-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="37c40-111">W poniższym przykładzie ścieżka lokalizacji pliku tekstowego jest folder Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="37c40-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="37c40-112">Można to zrobić, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="37c40-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="37c40-113">Ponadto pozwala to użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37c40-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
  
2.  <span data-ttu-id="37c40-114">Jeśli są przekazywane węzła drzewa, a ma <xref:System.Windows.Forms.TreeNode> klasy, musisz wykonać rzutowanie do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="37c40-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="37c40-115">Rzutowanie jest jawna konwersja z jednego typu obiektu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="37c40-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="37c40-116">Aby uzyskać więcej informacji na temat rzutowania, zobacz [Konwersje jawne i niejawne](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [— Operator ()](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#), lub [Operator rzutowania: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) .</span><span class="sxs-lookup"><span data-stu-id="37c40-116">For more information on casting, see [Implicit and Explicit Conversions](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [() Operator](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37c40-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37c40-117">See also</span></span>
- [<span data-ttu-id="37c40-118">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="37c40-118">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="37c40-119">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="37c40-119">ListView Control</span></span>](listview-control-windows-forms.md)
