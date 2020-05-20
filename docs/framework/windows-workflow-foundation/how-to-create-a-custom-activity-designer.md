---
title: 'Instrukcje: Tworzenie niestandardowego projektanta działań'
description: W tym artykule opisano sposób tworzenia niestandardowego projektanta działań programu Workflow Foundation, który ma strefę upuszczania, w której można umieścić dowolne działanie.
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 015efd1e482e2b531d28b9caec411c76116c9653
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419788"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="35fda-103">Instrukcje: Tworzenie niestandardowego projektanta działań</span><span class="sxs-lookup"><span data-stu-id="35fda-103">How to: Create a Custom Activity Designer</span></span>

<span data-ttu-id="35fda-104">Projektanci działań niestandardowych są zwykle implementowane, dzięki czemu ich skojarzone działania są przeznaczone do tworzenia z innymi działaniami, których projektanci mogą zostać porzucone do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="35fda-104">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="35fda-105">Ta funkcja wymaga, aby niestandardowy Projektant działań zapewniał "upuszczania strefy", w której można umieścić dowolne działanie, a także środki do zarządzania wynikiem zebrania elementów na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="35fda-105">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="35fda-106">W tym temacie opisano sposób tworzenia niestandardowego projektanta działań zawierającego taką strefę upuszczania oraz sposób tworzenia niestandardowego projektanta działań, który zapewnia, że funkcje edytowania potrzebne do zarządzania kolekcją elementów projektanta.</span><span class="sxs-lookup"><span data-stu-id="35fda-106">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>

<span data-ttu-id="35fda-107">Projektanci działań niestandardowych zwykle dziedziczą z <xref:System.Activities.Presentation.ActivityDesigner> , który jest domyślnym typem projektanta działań podstawowych dla wszystkich działań bez określonego projektanta.</span><span class="sxs-lookup"><span data-stu-id="35fda-107">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="35fda-108">Ten typ zapewnia środowisko czasu projektowania do współpracy z siatką właściwości i konfigurowania podstawowych aspektów, takich jak zarządzanie kolorami i ikonami.</span><span class="sxs-lookup"><span data-stu-id="35fda-108">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>

<span data-ttu-id="35fda-109"><xref:System.Activities.Presentation.ActivityDesigner>używa dwóch kontrolek pomocnika <xref:System.Activities.Presentation.WorkflowItemPresenter> i ułatwia <xref:System.Activities.Presentation.WorkflowItemsPresenter> Opracowywanie niestandardowych projektantów działań.</span><span class="sxs-lookup"><span data-stu-id="35fda-109"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="35fda-110">Obsługują one typowe funkcje, takie jak przeciąganie i upuszczanie elementów podrzędnych, usuwanie, wybieranie i Dodawanie tych elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="35fda-110">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="35fda-111"><xref:System.Activities.Presentation.WorkflowItemPresenter>Zezwala na pojedynczy podrzędny element interfejsu użytkownika wewnątrz, co zapewnia "strefę upuszczania", podczas gdy <xref:System.Activities.Presentation.WorkflowItemsPresenter> może zapewnić obsługę wielu elementów interfejsu użytkownika, w tym dodatkowych funkcji, takich jak porządkowanie, przesuwanie, usuwanie i Dodawanie elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="35fda-111">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>

<span data-ttu-id="35fda-112">Druga część tego wątku, która wymaga wyróżnienia w implementacji niestandardowego projektanta działań, ma wpływ na sposób, w jaki zmiany wizualne są powiązane przy użyciu powiązania danych WPF z wystąpieniem przechowywanym w pamięci w projektancie.</span><span class="sxs-lookup"><span data-stu-id="35fda-112">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using WPF data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="35fda-113">Jest to realizowane przez drzewo elementów modelu, które jest również odpowiedzialne za Włączanie powiadomień o zmianach i śledzenie zdarzeń, takich jak zmiany w Stanach.</span><span class="sxs-lookup"><span data-stu-id="35fda-113">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>

<span data-ttu-id="35fda-114">W tym temacie przedstawiono dwie procedury.</span><span class="sxs-lookup"><span data-stu-id="35fda-114">This topic outlines two procedures.</span></span>

1. <span data-ttu-id="35fda-115">W pierwszej procedurze opisano sposób tworzenia niestandardowego projektanta działań z programem <xref:System.Activities.Presentation.WorkflowItemPresenter> , który zapewnia strefę upuszczania, która odbiera inne działania.</span><span class="sxs-lookup"><span data-stu-id="35fda-115">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="35fda-116">Ta procedura jest oparta na [niestandardowym projektantom złożonym — przykładowi prezentera elementu przepływu pracy](./samples/custom-composite-designers-workflow-item-presenter.md) .</span><span class="sxs-lookup"><span data-stu-id="35fda-116">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](./samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>

2. <span data-ttu-id="35fda-117">Druga procedura zawiera opis sposobu tworzenia niestandardowego projektanta działań z programem <xref:System.Activities.Presentation.WorkflowItemsPresenter> , który zapewnia funkcje konieczne do edytowania kolekcji zawartych elementów.</span><span class="sxs-lookup"><span data-stu-id="35fda-117">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="35fda-118">Ta procedura jest oparta na [niestandardowym projektantom złożonym — przykładowi dla prezenterów elementów przepływu pracy](./samples/custom-composite-designers-workflow-items-presenter.md) .</span><span class="sxs-lookup"><span data-stu-id="35fda-118">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](./samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="35fda-119">Aby utworzyć niestandardowy Projektant działań ze strefą upuszczania przy użyciu WorkflowItemPresenter</span><span class="sxs-lookup"><span data-stu-id="35fda-119">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>

1. <span data-ttu-id="35fda-120">Uruchom program Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="35fda-120">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="35fda-121">W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt...**.</span><span class="sxs-lookup"><span data-stu-id="35fda-121">On the **File** menu, point to **New**, and then select **Project…**.</span></span>

     <span data-ttu-id="35fda-122">Zostanie otwarte okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="35fda-122">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="35fda-123">W okienku **zainstalowane szablony** wybierz pozycję **Windows** z preferowanej kategorii języka.</span><span class="sxs-lookup"><span data-stu-id="35fda-123">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>

4. <span data-ttu-id="35fda-124">W okienku **Szablony** wybierz pozycję **Aplikacja WPF**.</span><span class="sxs-lookup"><span data-stu-id="35fda-124">In the **Templates** pane, select **WPF Application**.</span></span>

5. <span data-ttu-id="35fda-125">W polu **Nazwa** wprowadź wartość `UsingWorkflowItemPresenter` .</span><span class="sxs-lookup"><span data-stu-id="35fda-125">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>

6. <span data-ttu-id="35fda-126">W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.</span><span class="sxs-lookup"><span data-stu-id="35fda-126">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>

7. <span data-ttu-id="35fda-127">W polu **rozwiązanie** Zaakceptuj wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="35fda-127">In the **Solution** box, accept the default value.</span></span>

8. <span data-ttu-id="35fda-128">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="35fda-128">Click **OK**.</span></span>

9. <span data-ttu-id="35fda-129">Kliknij prawym przyciskiem myszy plik *MainWindows. XAML* w **Eksplorator rozwiązań**, wybierz pozycję **Usuń** i Potwierdź **OK** w oknie dialogowym **Microsoft Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="35fda-129">Right-click the *MainWindows.xaml* file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialog box.</span></span>

10. <span data-ttu-id="35fda-130">Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksplorator rozwiązań**, wybierz pozycję **Dodaj**, a następnie pozycję **nowy element...**</span><span class="sxs-lookup"><span data-stu-id="35fda-130">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="35fda-131">Aby wyświetlić okno dialogowe **Dodaj nowy element** i wybrać kategorię **WPF** z sekcji **zainstalowane szablony** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="35fda-131">to bring up the **Add New Item** dialog and select the **WPF** category from the **Installed Templates** section on the left.</span></span>

11. <span data-ttu-id="35fda-132">Wybierz szablon **okna (WPF)** , nadaj mu nazwę `RehostingWFDesigner` , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="35fda-132">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>

12. <span data-ttu-id="35fda-133">Otwórz plik *RehostingWFDesigner. XAML* i wklej do niego następujący kod, aby zdefiniować interfejs użytkownika dla aplikacji:</span><span class="sxs-lookup"><span data-stu-id="35fda-133">Open the *RehostingWFDesigner.xaml* file and paste the following code into it to define the UI for the application:</span></span>

    ```xaml
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"
            xmlns:sys="clr-namespace:System;assembly=mscorlib"
            Title="Window1" Height="600" Width="900">
        <Window.Resources>
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>
        </Window.Resources>
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="2*"/>
                <ColumnDefinition Width="7*"/>
                <ColumnDefinition Width="3*"/>
            </Grid.ColumnDefinitions>
            <Border Grid.Column="0">
                <sapt:ToolboxControl Name="Toolbox">
                    <sapt:ToolboxCategory CategoryName="Basic">
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.Sequence
                            </sapt:ToolboxItemWrapper.ToolName>
                           </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.WriteLine
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.If
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.While
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                    </sapt:ToolboxCategory>
                </sapt:ToolboxControl>
            </Border>
            <Border Grid.Column="1" Name="DesignerBorder"/>
            <Border Grid.Column="2" Name="PropertyBorder"/>
        </Grid>
    </Window>
    ```

13. <span data-ttu-id="35fda-134">Aby skojarzyć projektanta działań z typem działania, należy zarejestrować ten Projektant działań w magazynie metadanych.</span><span class="sxs-lookup"><span data-stu-id="35fda-134">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="35fda-135">Aby to zrobić, Dodaj `RegisterMetadata` metodę do `RehostingWFDesigner` klasy.</span><span class="sxs-lookup"><span data-stu-id="35fda-135">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="35fda-136">W zakresie `RegisterMetadata` metody Utwórz <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> obiekt i Wywołaj <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metodę, aby dodać do niej atrybuty.</span><span class="sxs-lookup"><span data-stu-id="35fda-136">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="35fda-137">Wywołaj <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> metodę, aby dodać <xref:System.Activities.Presentation.Metadata.AttributeTable> do magazynu metadanych.</span><span class="sxs-lookup"><span data-stu-id="35fda-137">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="35fda-138">Poniższy kod zawiera logikę rehostowania dla projektanta.</span><span class="sxs-lookup"><span data-stu-id="35fda-138">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="35fda-139">Rejestruje metadane, umieszcza je `SimpleNativeActivity` w przyborniku i tworzy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="35fda-139">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="35fda-140">Umieść ten kod w pliku *RehostingWFDesigner.XAML.cs* .</span><span class="sxs-lookup"><span data-stu-id="35fda-140">Put this code into the *RehostingWFDesigner.xaml.cs* file.</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Presentation.Toolbox;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespace UsingWorkflowItemPresenter
    {
        // Interaction logic for RehostingWFDesigner.xaml
        public partial class RehostingWFDesigner
        {
            public RehostingWFDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. <span data-ttu-id="35fda-141">Kliknij prawym przyciskiem myszy katalog odwołania w Eksplorator rozwiązań i wybierz polecenie **Dodaj odwołanie...**</span><span class="sxs-lookup"><span data-stu-id="35fda-141">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="35fda-142">Aby wyświetlić okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="35fda-142">to bring up the **Add Reference** dialog.</span></span>

15. <span data-ttu-id="35fda-143">Kliknij kartę **.NET** , odszukaj zestaw o nazwie **System. Activities. Core. Presentation**, zaznacz go i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="35fda-143">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>

16. <span data-ttu-id="35fda-144">Korzystając z tej samej procedury, Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="35fda-144">Using the same procedure, add references to the following assemblies:</span></span>

    1. <span data-ttu-id="35fda-145">System. Data. DataSetExtensions. dll</span><span class="sxs-lookup"><span data-stu-id="35fda-145">System.Data.DataSetExtensions.dll</span></span>

    2. <span data-ttu-id="35fda-146">System. Activities. Presentation. dll</span><span class="sxs-lookup"><span data-stu-id="35fda-146">System.Activities.Presentation.dll</span></span>

    3. <span data-ttu-id="35fda-147">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="35fda-147">System.ServiceModel.Activities.dll</span></span>

17. <span data-ttu-id="35fda-148">Otwórz plik *App. XAML* i zmień wartość StartUpUri na "RehostingWFDesigner. XAML".</span><span class="sxs-lookup"><span data-stu-id="35fda-148">Open the *App.xaml* file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>

18. <span data-ttu-id="35fda-149">Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksplorator rozwiązań**, wybierz pozycję **Dodaj**, a następnie pozycję **nowy element...**</span><span class="sxs-lookup"><span data-stu-id="35fda-149">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="35fda-150">Aby wyświetlić okno dialogowe **Dodaj nowy element** , a następnie wybierz kategorię **przepływ pracy** formularz w sekcji **zainstalowane szablony** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="35fda-150">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

19. <span data-ttu-id="35fda-151">Wybierz szablon **projektanta działań** , nadaj mu nazwę `SimpleNativeDesigner` , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="35fda-151">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>

20. <span data-ttu-id="35fda-152">Otwórz plik *SimpleNativeDesigner. XAML* i wklej do niego następujący kod.</span><span class="sxs-lookup"><span data-stu-id="35fda-152">Open the *SimpleNativeDesigner.xaml* file and paste the following code into it.</span></span> <span data-ttu-id="35fda-153">Zwróć uwagę, że ten kod używa <xref:System.Activities.Presentation.ActivityDesigner> jako elementu głównego i pokazuje, jak powiązanie jest używane do integrowania z <xref:System.Activities.Presentation.WorkflowItemPresenter> projektantem, dzięki czemu typ podrzędny może być wyświetlany w projektancie działań złożonych.</span><span class="sxs-lookup"><span data-stu-id="35fda-153">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="35fda-154">Schemat dla programu <xref:System.Activities.Presentation.ActivityDesigner> umożliwia dodanie tylko jednego elementu podrzędnego do definicji projektanta działań niestandardowych, jednak ten element może być `StackPanel` , `Grid` lub innego złożonego elementu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="35fda-154">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <StackPanel>
                    <TextBlock>This is the collapsed view</TextBlock>
                </StackPanel>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock>Custom Text</TextBlock>
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                            HintText="Please drop an activity here" />
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
        </Grid>
    </sap:ActivityDesigner>
    ```

21. <span data-ttu-id="35fda-155">Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksplorator rozwiązań**, wybierz pozycję **Dodaj**, a następnie pozycję **nowy element...**</span><span class="sxs-lookup"><span data-stu-id="35fda-155">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="35fda-156">Aby wyświetlić okno dialogowe **Dodaj nowy element** , a następnie wybierz kategorię **przepływ pracy** formularz w sekcji **zainstalowane szablony** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="35fda-156">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

22. <span data-ttu-id="35fda-157">Wybierz szablon **działania kod** , nadaj mu nazwę `SimpleNativeActivity` , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="35fda-157">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>

23. <span data-ttu-id="35fda-158">Zaimplementuj `SimpleNativeActivity` klasę, wprowadzając następujący kod do pliku *SimpleNativeActivity.cs* :</span><span class="sxs-lookup"><span data-stu-id="35fda-158">Implement the `SimpleNativeActivity` class by entering the following code into the *SimpleNativeActivity.cs* file:</span></span>

    ```csharp
    using System.Activities;

    namespace UsingWorkflowItemPresenter
    {
        public sealed class SimpleNativeActivity : NativeActivity
        {
            // this property contains an activity that will be scheduled in the execute method
            // the WorkflowItemPresenter in the designer is bound to this to enable editing
            // of the value
            public Activity Body { get; set; }

            protected override void CacheMetadata(NativeActivityMetadata metadata)
            {
               metadata.AddChild(Body);
               base.CacheMetadata(metadata);

            }

            protected override void Execute(NativeActivityContext context)
            {
                context.ScheduleActivity(Body);
            }
        }
    }
    ```

24. <span data-ttu-id="35fda-159">Wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="35fda-159">Select **Build Solution** from the **Build** menu.</span></span>

25. <span data-ttu-id="35fda-160">Wybierz pozycję **Uruchom bez debugowania** z menu **Debuguj** , aby otworzyć okno zaprojektowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="35fda-160">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="35fda-161">Tworzenie niestandardowego projektanta działań za pomocą WorkflowItemsPresenter</span><span class="sxs-lookup"><span data-stu-id="35fda-161">To create a custom activity designer using WorkflowItemsPresenter</span></span>

1. <span data-ttu-id="35fda-162">Procedura drugiego niestandardowego projektanta działań jest równoległa do pierwszego z kilku modyfikacji, a pierwszy to nazwa drugiej aplikacji `UsingWorkflowItemsPresenter` .</span><span class="sxs-lookup"><span data-stu-id="35fda-162">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="35fda-163">Ponadto ta aplikacja nie definiuje nowego działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="35fda-163">Also this application does not define a new custom activity.</span></span>

2. <span data-ttu-id="35fda-164">Kluczowe różnice są zawarte w plikach *CustomParallelDesigner. XAML* i *RehostingWFDesigner.XAML.cs* .</span><span class="sxs-lookup"><span data-stu-id="35fda-164">Key differences are contained in the *CustomParallelDesigner.xaml* and *RehostingWFDesigner.xaml.cs* files.</span></span> <span data-ttu-id="35fda-165">Oto kod z pliku *CustomParallelDesigner. XAML* , który definiuje interfejs użytkownika:</span><span class="sxs-lookup"><span data-stu-id="35fda-165">Here is the code from the *CustomParallelDesigner.xaml* file that defines the UI:</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <TextBlock>This is the Collapsed View</TextBlock>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"
                                        Items="{Binding Path=ModelItem.Branches}">
                        <sap:WorkflowItemsPresenter.SpacerTemplate>
                            <DataTemplate>
                                <Ellipse Width="10" Height="10" Fill="Black"/>
                            </DataTemplate>
                        </sap:WorkflowItemsPresenter.SpacerTemplate>
                        <sap:WorkflowItemsPresenter.ItemsPanel>
                            <ItemsPanelTemplate>
                                <StackPanel Orientation="Horizontal"/>
                            </ItemsPanelTemplate>
                        </sap:WorkflowItemsPresenter.ItemsPanel>
                    </sap:WorkflowItemsPresenter>
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
        </Grid>
    </sap:ActivityDesigner>
    ```

3. <span data-ttu-id="35fda-166">Oto kod z pliku *RehostingWFDesigner.XAML.cs* , który udostępnia logikę rehostowania:</span><span class="sxs-lookup"><span data-stu-id="35fda-166">Here is the code from the *RehostingWFDesigner.xaml.cs* file that provides the rehosting logic:</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespaceUsingWorkflowItemsPresenter
    {
        public partial class RehostingWfDesigner : Window
        {
            public RehostingWfDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="35fda-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35fda-167">See also</span></span>

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [<span data-ttu-id="35fda-168">Dostosowywanie środowiska projektowania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="35fda-168">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
