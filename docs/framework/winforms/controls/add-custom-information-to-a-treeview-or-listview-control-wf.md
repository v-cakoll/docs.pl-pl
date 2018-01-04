---
title: 'Porady: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Formularze systemu Windows)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64e51a8911e27a612500ba222df7e3637cd24a13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="7558b-102">Porady: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="7558b-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="7558b-103">Można utworzyć pochodnej węzeł w formularzach systemu Windows <xref:System.Windows.Forms.TreeView> formant lub pochodnego elementu w <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="7558b-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="7558b-104">Tworzenie wartości pochodnych umożliwia dodanie wszystkie pola, które są wymagane, a także niestandardowe metody i konstruktory ich obsługę.</span><span class="sxs-lookup"><span data-stu-id="7558b-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="7558b-105">Jedno użycie tej funkcji jest można dołączyć obiektu klienta do każdego drzewa węzła lub elementu listy.</span><span class="sxs-lookup"><span data-stu-id="7558b-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="7558b-106">Przykłady w tym miejscu są dla <xref:System.Windows.Forms.TreeView> sterowania, ale same podejście może służyć do <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="7558b-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="7558b-107">Do uzyskania węzeł drzewa</span><span class="sxs-lookup"><span data-stu-id="7558b-107">To derive a tree node</span></span>  
  
-   <span data-ttu-id="7558b-108">Utwórz nową klasę węzeł pochodzi od <xref:System.Windows.Forms.TreeNode> klasy, która ma pole niestandardowe, aby zarejestrować ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="7558b-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="7558b-109">Aby użyć węzła drzewa pochodne</span><span class="sxs-lookup"><span data-stu-id="7558b-109">To use a derived tree node</span></span>  
  
1.  <span data-ttu-id="7558b-110">Nowy węzeł drzewa pochodnej można użyć jako parametru do wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="7558b-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="7558b-111">W poniższym przykładzie ścieżka zestawu dla lokalizacji pliku tekstowego jest folder Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="7558b-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="7558b-112">Można to zrobić, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="7558b-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="7558b-113">To umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7558b-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
  
2.  <span data-ttu-id="7558b-114">Jeśli węzeł drzewa są przekazywane i jest wpisana jako <xref:System.Windows.Forms.TreeNode> klasy, musisz wykonać rzutowanie do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7558b-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="7558b-115">Rzutowanie jest jawnej konwersji typu obiektu do innego.</span><span class="sxs-lookup"><span data-stu-id="7558b-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="7558b-116">Aby uzyskać więcej informacji na rzutowanie, zobacz [Konwersje jawne i niejawne](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]), [(Operator)](~/docs/csharp/language-reference/operators/invocation-operator.md) ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]), lub [Operator rzutowania: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) .</span><span class="sxs-lookup"><span data-stu-id="7558b-116">For more information on casting, see [Implicit and Explicit Conversions](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]), [() Operator](~/docs/csharp/language-reference/operators/invocation-operator.md) ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7558b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7558b-117">See Also</span></span>  
 [<span data-ttu-id="7558b-118">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7558b-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="7558b-119">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="7558b-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
