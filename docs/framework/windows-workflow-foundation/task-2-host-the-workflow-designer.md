---
title: Zadanie 2. Hostowanie projektanta przepływu pracy
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 92c5fa347cc7a2c0088ab8f4fbdfddf25ffb83c1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037869"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="c67ec-102">Zadanie 2. Hostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c67ec-102">Task 2: Host the Workflow Designer</span></span>

<span data-ttu-id="c67ec-103">[!INCLUDE[wfd1](../../../includes/wfd1-md.md)] W tym temacie opisano procedurę hostingu wystąpienia programu w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="c67ec-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="c67ec-104">Procedura konfiguruje kontrolkę **siatki** , która zawiera projektanta, programowo tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner> , które zawiera domyślne <xref:System.Activities.Statements.Sequence> działanie, rejestruje metadane projektanta, aby zapewnić obsługę projektanta dla wszystkich wbudowane działania i hosty [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="c67ec-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the WPF application.</span></span>

### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="c67ec-105">Aby hostować projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c67ec-105">To host the workflow designer</span></span>

1. <span data-ttu-id="c67ec-106">Otwórz projekt HostingApplication utworzony w [zadaniu 1: Utwórz nową aplikację](task-1-create-a-new-wpf-app.md)Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="c67ec-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>

2. <span data-ttu-id="c67ec-107">Dostosuj rozmiar okna, aby ułatwić korzystanie z programu [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c67ec-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="c67ec-108">Aby to zrobić, wybierz pozycję **MainWindow** w projektancie, naciśnij klawisz F4, aby wyświetlić okno **Właściwości** , a następnie w sekcji **układ** Ustaw **Szerokość** na wartość 600 i **wysokość** na wartość 350.</span><span class="sxs-lookup"><span data-stu-id="c67ec-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>

3. <span data-ttu-id="c67ec-109">Ustaw nazwę siatki, wybierając panel **siatki** w projektancie (kliknij pole wewnątrz **MainWindow**) i ustaw właściwość **Nazwa** w górnej części okna **Właściwości** na "grid1".</span><span class="sxs-lookup"><span data-stu-id="c67ec-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>

4. <span data-ttu-id="c67ec-110">W oknie **Właściwości** kliknij przycisk wielokropka ( **...** ) `ColumnDefinitions` obok właściwości, aby otworzyć okno dialogowe **Edytor kolekcji** .</span><span class="sxs-lookup"><span data-stu-id="c67ec-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>

5. <span data-ttu-id="c67ec-111">W oknie dialogowym **Edytor kolekcji** kliknij przycisk **Dodaj** trzy razy, aby wstawić trzy kolumny do układu.</span><span class="sxs-lookup"><span data-stu-id="c67ec-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="c67ec-112">Pierwsza kolumna będzie zawierać **Przybornik**, druga kolumna będzie hostować [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], a trzecia kolumna zostanie użyta dla Inspektora właściwości.</span><span class="sxs-lookup"><span data-stu-id="c67ec-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>

6. <span data-ttu-id="c67ec-113">`Width` Ustaw właściwość środkowej kolumny na wartość "4 \*".</span><span class="sxs-lookup"><span data-stu-id="c67ec-113">Set the `Width` property of the middle column to the value "4\*".</span></span>

7. <span data-ttu-id="c67ec-114">Kliknij przycisk **OK** , aby zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="c67ec-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="c67ec-115">Następujący kod XAML zostanie dodany do pliku MainWindow. XAML:</span><span class="sxs-lookup"><span data-stu-id="c67ec-115">The following XAML is added to your MainWindow.xaml file:</span></span>

    ```xml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. <span data-ttu-id="c67ec-116">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję MainWindow. XAML i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="c67ec-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="c67ec-117">Zmodyfikuj kod, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c67ec-117">Modify the code by following these steps:</span></span>

    1. <span data-ttu-id="c67ec-118">Dodaj następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="c67ec-118">Add the following namespaces:</span></span>

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. <span data-ttu-id="c67ec-119">Aby zadeklarować prywatne pole elementu członkowskiego do przechowywania wystąpienia <xref:System.Activities.Presentation.WorkflowDesigner>obiektu, Dodaj następujący kod `MainWindow` do klasy.</span><span class="sxs-lookup"><span data-stu-id="c67ec-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>

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

    3. <span data-ttu-id="c67ec-120">Dodaj następującą `AddDesigner` metodę `MainWindow` do klasy.</span><span class="sxs-lookup"><span data-stu-id="c67ec-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="c67ec-121">Implementacja tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, <xref:System.Activities.Statements.Sequence> dodaje do niego działanie i umieszcza je w środkowej kolumnie **siatki**grid1.</span><span class="sxs-lookup"><span data-stu-id="c67ec-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>

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

    4. <span data-ttu-id="c67ec-122">Zarejestruj metadane projektanta, aby dodać obsługę projektanta dla wszystkich wbudowanych działań.</span><span class="sxs-lookup"><span data-stu-id="c67ec-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="c67ec-123">Dzięki temu można porzucić działania z przybornika na pierwotne <xref:System.Activities.Statements.Sequence> działanie [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]w.</span><span class="sxs-lookup"><span data-stu-id="c67ec-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="c67ec-124">Aby to zrobić, Dodaj `RegisterMetadata` metodę `MainWindow` do klasy.</span><span class="sxs-lookup"><span data-stu-id="c67ec-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>

        ```csharp
        private void RegisterMetadata()
        {
            DesignerMetadata dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        <span data-ttu-id="c67ec-125">Aby uzyskać więcej informacji na temat rejestrowania projektantów działań [, zobacz How to: Tworzenie niestandardowego projektanta](how-to-create-a-custom-activity-designer.md)działań.</span><span class="sxs-lookup"><span data-stu-id="c67ec-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>

    5. <span data-ttu-id="c67ec-126">W konstruktorze <xref:System.Activities.Presentation.WorkflowDesigner>klasyDodajwywołania do metod zadeklarowanych wcześniej, aby zarejestrować metadane dla wsparcia projektanta i utworzyć. `MainWindow`</span><span class="sxs-lookup"><span data-stu-id="c67ec-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>

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
        > <span data-ttu-id="c67ec-127">Metoda rejestruje metadane projektanta działań wbudowanych, w <xref:System.Activities.Statements.Sequence> tym działanie. `RegisterMetadata`</span><span class="sxs-lookup"><span data-stu-id="c67ec-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="c67ec-128">Ponieważ metoda używa działania, `RegisterMetadata` Metoda musi być wywoływana jako pierwsza. <xref:System.Activities.Statements.Sequence> `AddDesigner`</span><span class="sxs-lookup"><span data-stu-id="c67ec-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>

9. <span data-ttu-id="c67ec-129">Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="c67ec-129">Press F5 to build and run the solution.</span></span>

10. <span data-ttu-id="c67ec-130">Zobacz [zadanie 3: Utwórz okienka](task-3-create-the-toolbox-and-propertygrid-panes.md) Przybornik i PropertyGrid, aby dowiedzieć się, jak dodać **Przybornik** i obsługę elementu **PropertyGrid** do zahostowanego projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c67ec-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="c67ec-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c67ec-131">See also</span></span>

- [<span data-ttu-id="c67ec-132">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c67ec-132">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="c67ec-133">Zadanie 1: Utwórz nową aplikację Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="c67ec-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="c67ec-134">Zadanie 3: Tworzenie okienek Przybornik i PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="c67ec-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
