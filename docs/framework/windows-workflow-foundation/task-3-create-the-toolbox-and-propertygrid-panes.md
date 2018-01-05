---
title: 'Zadanie 3: Tworzenie przybornika i PropertyGrid okienka'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90083692c2415ed6c1117185474d6bbaa9d1963b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="b5bdb-102">Zadanie 3: Tworzenie przybornika i PropertyGrid okienka</span><span class="sxs-lookup"><span data-stu-id="b5bdb-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>
<span data-ttu-id="b5bdb-103">W ramach tego zadania spowoduje utworzenie **przybornika** i **PropertyGrid** okienka i dodaj je do rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5bdb-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span>  
  
 <span data-ttu-id="b5bdb-104">Odwołania, kod, który powinien znajdować się w pliku MainWindow.xaml.cs po zakończeniu trzech zadania w programie [Rehosting projektanta przepływów pracy](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) serii tematów znajduje się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="b5bdb-105">Aby utworzyć przybornika i dodać go do siatki</span><span class="sxs-lookup"><span data-stu-id="b5bdb-105">To create the Toolbox and add it to the grid</span></span>  
  
1.  <span data-ttu-id="b5bdb-106">Otwórz projekt HostingApplication uzyskano, wykonując procedury opisane w sekcji [zadanie 2: Host projektanta przepływów pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="b5bdb-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).</span></span>  
  
2.  <span data-ttu-id="b5bdb-107">W **Eksploratora rozwiązań** okienku kliknij prawym przyciskiem myszy plik MainWindow.xaml i wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-107">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
3.  <span data-ttu-id="b5bdb-108">Dodaj `GetToolboxControl` metodę `MainWindow` klasy, która tworzy <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, dodaje nową **przybornika** kategorię, aby **przybornika**i przypisuje <xref:System.Activities.Statements.Assign> i <xref:System.Activities.Statements.Sequence> typy działań do tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4.  <span data-ttu-id="b5bdb-109">Dodaj prywatnej `AddToolbox` metodę `MainWindow` klasy, który umieszcza **przybornika** w lewej kolumnie siatki.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  <span data-ttu-id="b5bdb-110">Dodaj wywołanie do `AddToolBox` metoda `MainWindow()` konstruktora klasy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  <span data-ttu-id="b5bdb-111">Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-111">Press F5 to build and run your solution.</span></span> <span data-ttu-id="b5bdb-112">**Przybornika** zawierający <xref:System.Activities.Statements.Assign> i <xref:System.Activities.Statements.Sequence> działania powinny być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>  
  
### <a name="to-create-the-propertygrid"></a><span data-ttu-id="b5bdb-113">Aby utworzyć PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="b5bdb-113">To create the PropertyGrid</span></span>  
  
1.  <span data-ttu-id="b5bdb-114">W **Eksploratora rozwiązań** okienku kliknij prawym przyciskiem myszy plik MainWindow.xaml i wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-114">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="b5bdb-115">Dodaj `AddPropertyInspector` metodę `MainWindow` klasę, aby umieścić **PropertyGrid** okienka w ostatniej kolumnie siatki.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid.</span></span>  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  <span data-ttu-id="b5bdb-116">Dodaj wywołanie do `AddPropertyInspector` metoda `MainWindow()` konstruktora klasy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
        this.AddToolBox();  
  
        this.AddPropertyInspector();   
    }  
    ```  
  
4.  <span data-ttu-id="b5bdb-117">Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-117">Press F5 to build and run the solution.</span></span> <span data-ttu-id="b5bdb-118">**Przybornika**, kanwy projektu przepływu pracy, i **PropertyGrid** okienka powinny być wyświetlane wszystkie i przeciągnięcie <xref:System.Activities.Statements.Assign> działania lub <xref:System.Activities.Statements.Sequence> działania na kanwę projektu siatki właściwości, należy zaktualizować w zależności od wyróżnione działania.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5bdb-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5bdb-119">Example</span></span>  
 <span data-ttu-id="b5bdb-120">Plik MainWindow.xaml.cs teraz powinien zawierać następujący kod.</span><span class="sxs-lookup"><span data-stu-id="b5bdb-120">The MainWindow.xaml.cs file should now contain the following code.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
//dlls added  
using System.Activities;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation;  
using System.Activities.Presentation.Metadata;  
using System.Activities.Presentation.Toolbox;  
using System.Activities.Statements;  
using System.ComponentModel;  
  
namespace HostingApplication  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
        private WorkflowDesigner wd;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
            RegisterMetadata();  
            AddDesigner();  
            this.AddToolBox();  
            this.AddPropertyInspector();  
        }  
  
        private void AddDesigner()  
        {  
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
                typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
            // Add the Toolbox items to the category.  
            category.Add(tool1);  
            category.Add(tool2);  
  
            // Add the category to the ToolBox control.  
            ctrl.Categories.Add(category);  
            return ctrl;  
        }  
  
        private void AddToolBox()  
        {  
            ToolboxControl tc = GetToolboxControl();  
            Grid.SetColumn(tc, 0);  
            grid1.Children.Add(tc);  
        }  
  
        private void AddPropertyInspector()  
        {  
            Grid.SetColumn(wd.PropertyInspectorView, 2);  
            grid1.Children.Add(wd.PropertyInspectorView);  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5bdb-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5bdb-121">See Also</span></span>  
 [<span data-ttu-id="b5bdb-122">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b5bdb-122">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="b5bdb-123">Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="b5bdb-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [<span data-ttu-id="b5bdb-124">Zadanie 2: Hostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b5bdb-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
