---
title: 'Zadanie 2: Host projektanta przepływów pracy'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 8ac6b3590d146909c1cb9fd8cf9cae2352b0155b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519067"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="804e6-102">Zadanie 2: Host projektanta przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="804e6-102">Task 2: Host the Workflow Designer</span></span>
<span data-ttu-id="804e6-103">W tym temacie opisano procedurę obsługi wystąpienia [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="804e6-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="804e6-104">Procedura powoduje skonfigurowanie **siatki** formant, który zawiera projektancie programowo tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner> zawierający domyślne <xref:System.Activities.Statements.Sequence> działania, rejestruje projektanta metadanych w celu zapewnienia projektanta obsługę wszystkich wbudowane działania i hosty [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="804e6-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span></span>  
  
### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="804e6-105">Do obsługi projektanta przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="804e6-105">To host the workflow designer</span></span>  
  
1.  <span data-ttu-id="804e6-106">Otwórz HostingApplication projektu utworzonego w [zadanie 1: Tworzenie nowej aplikacji systemu Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="804e6-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span></span>  
  
2.  <span data-ttu-id="804e6-107">Dopasuj rozmiar okna, aby ułatwić korzystanie [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="804e6-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="804e6-108">Aby to zrobić, wybierz **właściwości MainWindow** w projektancie, naciśnij klawisz F4, aby wyświetlić **właściwości** okna i w **układu** Brak sekcji, ustaw **szerokość** na wartość 600 i **wysokość** wartość 350.</span><span class="sxs-lookup"><span data-stu-id="804e6-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>  
  
3.  <span data-ttu-id="804e6-109">Ustaw nazwę siatki, wybierając **siatki** panelu w Projektancie (kliknij pole wewnątrz **właściwości MainWindow**) i ustawienie **nazwa** właściwość w górnej części  **Właściwości** okna "grid1".</span><span class="sxs-lookup"><span data-stu-id="804e6-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>  
  
4.  <span data-ttu-id="804e6-110">W **właściwości** okna, kliknij przycisk wielokropka (**...** ) obok pozycji `ColumnDefinitions` właściwości, aby otworzyć **edytora kolekcji** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="804e6-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="804e6-111">W **edytora kolekcji** okno dialogowe, kliknij przycisk **Dodaj** przycisk trzy razy, aby wstawić trzy kolumny do układu.</span><span class="sxs-lookup"><span data-stu-id="804e6-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="804e6-112">Pierwsza kolumna będzie zawierać **przybornika**, druga kolumna będzie obsługiwać [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], i trzecia kolumna będzie służyć do Inspektora właściwości.</span><span class="sxs-lookup"><span data-stu-id="804e6-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>  
  
6.  <span data-ttu-id="804e6-113">Ustaw `Width` właściwości środkowej kolumny, która ma wartość "4 \*".</span><span class="sxs-lookup"><span data-stu-id="804e6-113">Set the `Width` property of the middle column to the value "4\*".</span></span>  
  
7.  <span data-ttu-id="804e6-114">Kliknij przycisk **OK** , aby zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="804e6-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="804e6-115">Następujące XAML został dodany do pliku MainWindow.xaml:</span><span class="sxs-lookup"><span data-stu-id="804e6-115">The following XAML is added to your MainWindow.xaml file:</span></span>  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  <span data-ttu-id="804e6-116">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy MainWindow.xaml i wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="804e6-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="804e6-117">Zmodyfikuj kod, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="804e6-117">Modify the code by following these steps:</span></span>  
  
    1.  <span data-ttu-id="804e6-118">Dodaj następujących przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="804e6-118">Add the following namespaces:</span></span>  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  <span data-ttu-id="804e6-119">Aby zadeklarować pole prywatnego elementu członkowskiego, aby pomieścić wystąpienia <xref:System.Activities.Presentation.WorkflowDesigner>, Dodaj następujący kod do `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="804e6-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>  
  
        ```csharp  
        public partial class MainWindow : Window  
        {  
            private WorkflowDesigner wd;  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
        }  
        ```  
  
    3.  <span data-ttu-id="804e6-120">Dodaj następujące `AddDesigner` metody `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="804e6-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="804e6-121">Implementacja tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, dodaje <xref:System.Activities.Statements.Sequence> działania i umieszcza je w środkowej kolumnie grid1 **siatki**.</span><span class="sxs-lookup"><span data-stu-id="804e6-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>  
  
        ```csharp  
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
        ```  
  
    4.  <span data-ttu-id="804e6-122">Zarejestruj projektanta metadane w celu dodania obsługi projektanta dla wszystkich działań wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="804e6-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="804e6-123">Dzięki temu można porzucić działań z przybornika do oryginalnej <xref:System.Activities.Statements.Sequence> działania w [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="804e6-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="804e6-124">Aby to zrobić, należy dodać `RegisterMetadata` metody `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="804e6-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         <span data-ttu-id="804e6-125">Aby uzyskać więcej informacji o rejestrowaniu projektantów działań, zobacz [jak: utworzyć Designer działania niestandardowe](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="804e6-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span></span>  
  
    5.  <span data-ttu-id="804e6-126">W `MainWindow` Konstruktor klasy, Dodaj wywołania metod poprzednio zadeklarowany rejestrowanie metadanych dla wsparcia projektanta i utworzyć <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="804e6-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>  
  
        ```csharp  
        public MainWindow()  
        {  
            InitializeComponent();  
  
            // Register the metadata  
            RegisterMetadata();  
  
            // Add the WFF Designer  
            AddDesigner();  
        }  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="804e6-127">`RegisterMetadata` Metoda rejestruje projektanta metadane działań wbudowanych, łącznie z <xref:System.Activities.Statements.Sequence> działania.</span><span class="sxs-lookup"><span data-stu-id="804e6-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="804e6-128">Ponieważ `AddDesigner` używa metody <xref:System.Activities.Statements.Sequence> działania, `RegisterMetadata` najpierw musi zostać wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="804e6-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>  
  
9. <span data-ttu-id="804e6-129">Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="804e6-129">Press F5 to build and run the solution.</span></span>  
  
10. <span data-ttu-id="804e6-130">Zobacz [zadanie 3: tworzenie przybornika i okienka PropertyGrid](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) Aby dowiedzieć się, jak dodać **przybornika** i **PropertyGrid** obsługiwać z projektantem rehosted przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="804e6-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804e6-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="804e6-131">See Also</span></span>  
 [<span data-ttu-id="804e6-132">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="804e6-132">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="804e6-133">Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="804e6-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [<span data-ttu-id="804e6-134">Zadanie 3: Tworzenie okienka PropertyGrid i przybornika</span><span class="sxs-lookup"><span data-stu-id="804e6-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
