---
title: Używanie edytora wyrażeń niestandardowych
ms.date: 03/30/2017
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
ms.openlocfilehash: a1cd92766c8897868920c1465ddb3eeabae1aa97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182716"
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="d7e6d-102">Używanie edytora wyrażeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d7e6d-102">Using a Custom Expression Editor</span></span>
<span data-ttu-id="d7e6d-103">Edytor wyrażeń niestandardowych można zaimplementować, aby zapewnić bogatsze lub prostsze środowisko edycji wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-103">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="d7e6d-104">Istnieje kilka scenariuszy, w których można użyć edytora wyrażeń niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="d7e6d-104">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
- <span data-ttu-id="d7e6d-105">Aby zapewnić obsługę technologii IntelliSense i innych rozbudowanych funkcji edycji w projektancie ponownego hostowania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-105">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="d7e6d-106">Ta funkcja musi być podana, ponieważ domyślny edytor wyrażeń programu Visual Studio nie może być używany w aplikacjach rehosted.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-106">This functionality must be provided because the default Visual Studio expression editor cannot be used in rehosted applications.</span></span>  
  
- <span data-ttu-id="d7e6d-107">Aby uprościć środowisko edycji wyrażeń dla użytkowników analityków biznesowych, tak aby nie były one, na przykład, wymagane do nauki języka Visual Basic lub radzenia sobie z wyrażeniami języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-107">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn Visual Basic or deal with Visual Basic expressions.</span></span>  
  
 <span data-ttu-id="d7e6d-108">Aby zaimplementować edytor wyrażeń niestandardowych, potrzebne są trzy podstawowe kroki:</span><span class="sxs-lookup"><span data-stu-id="d7e6d-108">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1. <span data-ttu-id="d7e6d-109">Zaimplementuj interfejs <xref:System.Activities.Presentation.View.IExpressionEditorService>.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-109">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="d7e6d-110">Ten interfejs zarządza tworzeniem i niszczeniem edytorów wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-110">This interface manages the creation and destruction of expression editors.</span></span>  
  
2. <span data-ttu-id="d7e6d-111">Zaimplementuj interfejs <xref:System.Activities.Presentation.View.IExpressionEditorInstance>.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-111">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="d7e6d-112">Ten interfejs implementuje interfejsu użytkownika do edycji wyrażeń interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-112">This interface implements the UI for expression editing UI.</span></span>  
  
3. <span data-ttu-id="d7e6d-113">Opublikuj <xref:System.Activities.Presentation.View.IExpressionEditorService> w aplikacji przepływu pracy ponownie.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-113">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="d7e6d-114">Implementowanie edytora wyrażeń niestandardowych w bibliotece klas</span><span class="sxs-lookup"><span data-stu-id="d7e6d-114">Implementing a Custom Expression Editor in a Class Library</span></span>  
 <span data-ttu-id="d7e6d-115">Oto przykład kodu dla (dowód koncepcji) `MyEditorService` klasy, która <xref:System.Activities.Presentation.View.IExpressionEditorService> implementuje interfejs jest zawarty w projekcie biblioteki MyExpressionEditorService.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-115">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Activities.Presentation.View;  
using System.Activities.Presentation.Hosting;  
using System.Activities.Presentation.Model;  
  
namespace MyExpressionEditorService  
{  
    public class MyEditorService : IExpressionEditorService  
    {  
        public void CloseExpressionEditors()  
        {  
  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, System.Windows.Size initialSize)  
                {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType)  
            {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType, System.Windows.Size initialSize)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public void UpdateContext(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces)  
        {  
  
        }  
  
    }  
}  
```  
  
 <span data-ttu-id="d7e6d-116">Oto kod `MyExpressionEditorInstance` dla klasy, która <xref:System.Activities.Presentation.View.IExpressionEditorInstance> implementuje interfejs w projekcie biblioteki MyExpressionEditorService.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-116">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
```csharp  
using System;  
using System.Activities.Presentation.View;  
using System.Windows;  
using System.Reflection;  
using System.Windows.Controls;  
  
namespace MyExpressionEditorService  
{  
    public class MyExpressionEditorInstance : IExpressionEditorInstance  
    {  
        private TextBox textBox = new TextBox();  
  
        public bool AcceptsReturn { get; set; }  
        public bool AcceptsTab { get; set; }  
        public bool HasAggregateFocus {  
            get  
            {  
                return true;  
            }  
        }  
  
        public System.Windows.Controls.ScrollBarVisibility HorizontalScrollBarVisibility { get; set; }  
        public System.Windows.Controls.Control HostControl {  
            get  
            {  
                return textBox;  
            }  
        }  
        public int MaxLines { get; set; }  
        public int MinLines { get; set; }  
        public string Text { get; set; }  
        public System.Windows.Controls.ScrollBarVisibility VerticalScrollBarVisibility { get; set; }  
  
        public event EventHandler Closing;  
        public event EventHandler GotAggregateFocus;  
        public event EventHandler LostAggregateFocus;  
        public event EventHandler TextChanged;  
  
        public bool CanCompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCopy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanDecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanGlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanIncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanPaste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanQuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanRedo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanUndo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
  
        public void ClearSelection()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public void Close()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public bool CompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Copy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Cut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool DecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public void Focus()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public string GetCommittedText()  
        {  
            return "CommittedText";  
        }  
        public bool GlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool IncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool ParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Paste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool QuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Redo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Undo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
    }  
}  
```  
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="d7e6d-117">Publikowanie edytora wyrażeń niestandardowych w projekcie WPF</span><span class="sxs-lookup"><span data-stu-id="d7e6d-117">Publishing a Custom Expression Editor in a WPF Project</span></span>  
 <span data-ttu-id="d7e6d-118">Oto kod, który pokazuje, jak ponownie hostować projektanta w aplikacji WPF i jak utworzyć i opublikować `MyEditorService` usługę.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-118">Here is the code that shows how to rehost the designer in a WPF application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="d7e6d-119">Przed użyciem tego kodu należy dodać odwołanie do projektu biblioteki MyExpressionEditorService z projektu, który zawiera aplikację avalon2.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-119">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
```csharp  
using System.Windows;  
using System.Windows.Controls;  
using System.Activities.Presentation;  
using System.Activities.Statements;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation.View;  
using MyExpressionEditorService;  
  
namespace WpfApplication1  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
  
        private MyEditorService expressionEditorService;  
        public MainWindow()  
        {  
            InitializeComponent();  
            new DesignerMetadata().Register();  
            createDesigner();  
        }  
  
        public void createDesigner()  
        {  
            WorkflowDesigner designer = new WorkflowDesigner();  
            Sequence root = new Sequence()  
            {  
                Activities = {  
                new Assign(),  
                new WriteLine()}  
            };  
  
            designer.Load(root);  
  
            Grid.SetColumn(designer.View, 0);  
  
            // Create ExpressionEditorService
            this.expressionEditorService = new MyEditorService();  
  
            // Publish the instance of MyEditorService.  
            designer.Context.Services.Publish<IExpressionEditorService>(this.expressionEditorService);  
  
            MyGrid.Children.Add(designer.View);  
        }  
    }  
}  
```  
  
### <a name="notes"></a><span data-ttu-id="d7e6d-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7e6d-120">Notes</span></span>  
 <span data-ttu-id="d7e6d-121">Jeśli używasz **ExpressionTextBox** formantu w projektancie działań niestandardowych, nie <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> jest <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> konieczne <xref:System.Activities.Presentation.View.IExpressionEditorService> do tworzenia i niszczenia edytorów wyrażeń przy użyciu i metody interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-121">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="d7e6d-122">Klasa <xref:System.Activities.Presentation.View.ExpressionTextBox> zarządza tym dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="d7e6d-122">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e6d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7e6d-123">See also</span></span>

- <xref:System.Activities.Presentation.View.IExpressionEditorService>
- <xref:System.Activities.Presentation.View.IExpressionEditorInstance>
- [<span data-ttu-id="d7e6d-124">Używanie elementu ExpressionTextBox w projektancie działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d7e6d-124">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
