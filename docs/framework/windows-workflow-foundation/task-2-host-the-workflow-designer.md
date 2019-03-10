---
title: Zadanie 2. Hostowanie projektanta przepływu pracy
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: e02134408b38e5c9aee9c59d86b1dfce032653d1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708642"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="127c9-102">Zadanie 2. Hostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="127c9-102">Task 2: Host the Workflow Designer</span></span>
<span data-ttu-id="127c9-103">W tym temacie opisano procedurę do hostowania wystąpienia [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="127c9-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="127c9-104">Procedura umożliwia skonfigurowanie **siatki** kontrolkę zawierającą projektanta, programowo tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner> zawierający domyślne <xref:System.Activities.Statements.Sequence> działania, rejestruje metadane projektanta w celu zapewnienia wsparcie wszystkie wbudowane działania i hosty [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="127c9-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span></span>  
  
### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="127c9-105">Do obsługi projektanta przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="127c9-105">To host the workflow designer</span></span>  
  
1.  <span data-ttu-id="127c9-106">Otwórz HostingApplication projektu utworzonego w sekcji [zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="127c9-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>  
  
2.  <span data-ttu-id="127c9-107">Dopasuj rozmiar okna, aby ułatwić użyj [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="127c9-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="127c9-108">Aby to zrobić, wybierz **MainWindow** w projektancie, naciśnij klawisz F4, aby wyświetlić **właściwości** okna i w **układ** sekcji istnieje, należy ustawić **szerokość** wartość 600 i **wysokość** wartości 350.</span><span class="sxs-lookup"><span data-stu-id="127c9-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>  
  
3.  <span data-ttu-id="127c9-109">Ustaw nazwę siatki, wybierając **siatki** panelu w Projektancie (kliknij pole wewnątrz **MainWindow**) i ustawienie **nazwa** właściwość w górnej części  **Właściwości** okna "grid1".</span><span class="sxs-lookup"><span data-stu-id="127c9-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>  
  
4.  <span data-ttu-id="127c9-110">W **właściwości** okna, kliknij przycisk wielokropka (**...** ) obok pozycji `ColumnDefinitions` właściwości, aby otworzyć **— Edytor kolekcji** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="127c9-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="127c9-111">W **— Edytor kolekcji** okno dialogowe, kliknij przycisk **Dodaj** przycisk trzy razy, aby wstawić trzy kolumny do układu.</span><span class="sxs-lookup"><span data-stu-id="127c9-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="127c9-112">Pierwsza kolumna będzie zawierać **przybornika**, druga kolumna będzie obsługiwać [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], a trzecia kolumna stosowanych w odniesieniu do Inspektora właściwości.</span><span class="sxs-lookup"><span data-stu-id="127c9-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>  
  
6.  <span data-ttu-id="127c9-113">Ustaw `Width` właściwość w środkowej kolumnie na wartość "4 \*".</span><span class="sxs-lookup"><span data-stu-id="127c9-113">Set the `Width` property of the middle column to the value "4\*".</span></span>  
  
7.  <span data-ttu-id="127c9-114">Kliknij przycisk **OK** , aby zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="127c9-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="127c9-115">Następujące XAML zostanie dodany do Twojego pliku MainWindow.xaml:</span><span class="sxs-lookup"><span data-stu-id="127c9-115">The following XAML is added to your MainWindow.xaml file:</span></span>  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  <span data-ttu-id="127c9-116">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy pliku MainWindow.xaml i wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="127c9-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="127c9-117">Należy zmodyfikować kod, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="127c9-117">Modify the code by following these steps:</span></span>  
  
    1.  <span data-ttu-id="127c9-118">Dodaj następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="127c9-118">Add the following namespaces:</span></span>  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  <span data-ttu-id="127c9-119">Aby zadeklarować pola prywatnego elementu członkowskiego, aby pomieścić wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, Dodaj następujący kod do `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="127c9-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>  
  
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
  
    3.  <span data-ttu-id="127c9-120">Dodaj następujący kod `AddDesigner` metody `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="127c9-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="127c9-121">Implementacja tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, dodaje <xref:System.Activities.Statements.Sequence> działania i umieszcza je w środkowej kolumnie grid1 **siatki**.</span><span class="sxs-lookup"><span data-stu-id="127c9-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>  
  
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
  
    4.  <span data-ttu-id="127c9-122">Zarejestruj metadane projektanta do projektanta obsługę wbudowanych działań.</span><span class="sxs-lookup"><span data-stu-id="127c9-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="127c9-123">Dzięki temu można upuszczać działania z przybornika do oryginalnego <xref:System.Activities.Statements.Sequence> działania w [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="127c9-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="127c9-124">Aby to zrobić, Dodaj `RegisterMetadata` metody `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="127c9-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         <span data-ttu-id="127c9-125">Aby uzyskać więcej informacji na temat rejestrowania Projektanci działań, zobacz [jak: Tworzenie niestandardowego projektanta działań](how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="127c9-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>  
  
    5.  <span data-ttu-id="127c9-126">W `MainWindow` konstruktora klasy, Dodaj wywołania metod uprzednio zadeklarowany, zarejestruj metadane projektanta pomocy technicznej i utworzyć <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="127c9-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>  
  
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
        >  <span data-ttu-id="127c9-127">`RegisterMetadata` Metoda rejestruje metadane projektanta działań wbudowanych, łącznie z <xref:System.Activities.Statements.Sequence> działania.</span><span class="sxs-lookup"><span data-stu-id="127c9-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="127c9-128">Ponieważ `AddDesigner` metoda używa <xref:System.Activities.Statements.Sequence> działania `RegisterMetadata` najpierw musi zostać wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="127c9-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>  
  
9. <span data-ttu-id="127c9-129">Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="127c9-129">Press F5 to build and run the solution.</span></span>  
  
10. <span data-ttu-id="127c9-130">Zobacz [zadanie 3: Tworzenie okienka PropertyGrid i przybornika](task-3-create-the-toolbox-and-propertygrid-panes.md) dowiesz się, jak dodać **przybornika** i **PropertyGrid** pomocy technicznej do Twojej rehostowanym projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="127c9-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127c9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="127c9-131">See also</span></span>
- [<span data-ttu-id="127c9-132">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="127c9-132">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="127c9-133">Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="127c9-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="127c9-134">Zadanie 3. Tworzenie okienka PropertyGrid i przybornika</span><span class="sxs-lookup"><span data-stu-id="127c9-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
