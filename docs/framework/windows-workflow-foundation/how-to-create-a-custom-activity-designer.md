---
title: "Porady: tworzenie Projektant działań niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0b1f27af6b4ec372b9dbd63e4bc89a5c435efe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="2bf22-102">Porady: tworzenie Projektant działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="2bf22-102">How to: Create a Custom Activity Designer</span></span>
<span data-ttu-id="2bf22-103">Projektantów działań niestandardowych są zwykle implementowany ich działania skojarzone są zezwala na składanie z innymi działaniami projektantów, których można było porzucić na powierzchnię projektu z nimi.</span><span class="sxs-lookup"><span data-stu-id="2bf22-103">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="2bf22-104">Ta funkcja wymaga, Projektant działań niestandardowych podania "strefy docelowej" rozmieszczenia dowolne działanie, a także sposób zarządzania wynikowy zbiór elementów na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="2bf22-104">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="2bf22-105">W tym temacie opisano, jak utworzyć projektanta działań niestandardowych, który zawiera strefy docelowej i jak utworzyć designer działania niestandardowego, który zapewnia, że funkcji edytowania potrzebne do zarządzania kolekcję elementów projektanta.</span><span class="sxs-lookup"><span data-stu-id="2bf22-105">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>  
  
 <span data-ttu-id="2bf22-106">Zwykle dziedziczyć projektantów działań niestandardowych <xref:System.Activities.Presentation.ActivityDesigner> czyli domyślny typ projektanta działanie podstawowe dla dowolnego działania bez określonego projektanta.</span><span class="sxs-lookup"><span data-stu-id="2bf22-106">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="2bf22-107">Ten typ zapewnia środowisko czasu projektowania interakcji z siatką właściwości i konfigurowania podstawowych aspektów, takie jak zarządzanie, kolory i ikon.</span><span class="sxs-lookup"><span data-stu-id="2bf22-107">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>  
  
 <span data-ttu-id="2bf22-108"><xref:System.Activities.Presentation.ActivityDesigner>używa dwóch formantów pomocnika, <xref:System.Activities.Presentation.WorkflowItemPresenter> i <xref:System.Activities.Presentation.WorkflowItemsPresenter> ułatwiające opracowanie projektantów działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2bf22-108"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="2bf22-109">Obsługują typowych funkcji, takich jak przeciąganie i upuszczanie elementów podrzędnych, usuwanie, wybór i dodanie tych elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2bf22-109">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="2bf22-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> Umożliwia pojedynczy element potomny elementu interfejsu użytkownika wewnątrz "strefy docelowej", podając go podczas <xref:System.Activities.Presentation.WorkflowItemsPresenter> zapewniają obsługuje wiele elementów interfejsu użytkownika, takie jak dodatkowe funkcje, takie jak kolejność, przenoszenie i dodawanie elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2bf22-110">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>  
  
 <span data-ttu-id="2bf22-111">Inne część klucza artykuł, który wymaga wyróżnianie w implementacji Projektant działań niestandardowych dotyczy sposób, w którym zmiany wizualne są powiązane za pomocą [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] wiązanie danych do wystąpienia przechowywane w pamięci, co możemy edycji w projektancie.</span><span class="sxs-lookup"><span data-stu-id="2bf22-111">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="2bf22-112">Jest to osiągane przez drzewo element modelu, w którym jest również odpowiada za włączanie powiadomienia o zmianie i śledzenia zdarzeń, takich jak zmiany stanów.</span><span class="sxs-lookup"><span data-stu-id="2bf22-112">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>  
  
 <span data-ttu-id="2bf22-113">W tym temacie przedstawiono dwie procedury.</span><span class="sxs-lookup"><span data-stu-id="2bf22-113">This topic outlines two procedures.</span></span>  
  
1.  <span data-ttu-id="2bf22-114">Pierwsza procedura opisuje sposób tworzenia Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemPresenter> zapewnia strefy docelowej odbierająca innych działań.</span><span class="sxs-lookup"><span data-stu-id="2bf22-114">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="2bf22-115">Ta procedura jest oparta na [niestandardowe projektantów złożonego - Prezenterze element przepływu pracy](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="2bf22-115">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>  
  
2.  <span data-ttu-id="2bf22-116">W drugiej procedurze opisano sposób tworzenia Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemsPresenter> zapewnia funkcje potrzebne do edycji z kolekcją elementów zawartych w niej.</span><span class="sxs-lookup"><span data-stu-id="2bf22-116">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="2bf22-117">Ta procedura jest oparta na [niestandardowe projektantów złożonego - Prezenterze elementy przepływu pracy](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="2bf22-117">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>  
  
### <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="2bf22-118">Aby utworzyć designer działań niestandardowych z strefy docelowej przy użyciu WorkflowItemPresenter</span><span class="sxs-lookup"><span data-stu-id="2bf22-118">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>  
  
1.  <span data-ttu-id="2bf22-119">Uruchom [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2bf22-119">Start [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="2bf22-120">Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu...** .</span><span class="sxs-lookup"><span data-stu-id="2bf22-120">On the **File** menu, point to **New**, and then select **Project…**.</span></span>  
  
     <span data-ttu-id="2bf22-121">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2bf22-121">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="2bf22-122">W **zainstalowane szablony** okienku wybierz **Windows** z kategorii preferowany język.</span><span class="sxs-lookup"><span data-stu-id="2bf22-122">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>  
  
4.  <span data-ttu-id="2bf22-123">W **szablony** okienku wybierz **aplikacji WPF**.</span><span class="sxs-lookup"><span data-stu-id="2bf22-123">In the **Templates** pane, select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="2bf22-124">W **nazwa** wprowadź `UsingWorkflowItemPresenter`.</span><span class="sxs-lookup"><span data-stu-id="2bf22-124">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>  
  
6.  <span data-ttu-id="2bf22-125">W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.</span><span class="sxs-lookup"><span data-stu-id="2bf22-125">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>  
  
7.  <span data-ttu-id="2bf22-126">W **rozwiązania** pozycję Zaakceptuj wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="2bf22-126">In the **Solution** box, accept the default value.</span></span>  
  
8.  <span data-ttu-id="2bf22-127">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2bf22-127">Click **OK**.</span></span>  
  
9. <span data-ttu-id="2bf22-128">Kliknij prawym przyciskiem myszy plik MainWindows.xaml **Eksploratora rozwiązań**, wybierz pozycję **usunąć** i Potwierdź **OK** w **programu Microsoft Visual Studio**okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2bf22-128">Right-click the MainWindows.xaml file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialogue box.</span></span>  
  
10. <span data-ttu-id="2bf22-129">Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksploratora rozwiązań**, wybierz pozycję **Dodaj**, następnie **nowy element...**</span><span class="sxs-lookup"><span data-stu-id="2bf22-129">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="2bf22-130">Aby wyświetlić **Dodaj nowy element** dialog i wybierz **WPF** kategorii z **zainstalowane szablony** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="2bf22-130">to bring up the **Add New Item** dialogue and select the **WPF** category from the **Installed Templates** section on the left.</span></span>  
  
11. <span data-ttu-id="2bf22-131">Wybierz **okna (WPF)** szablonu, nadaj jej nazwę `RehostingWFDesigner`i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="2bf22-131">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>  
  
12. <span data-ttu-id="2bf22-132">Otwórz plik RehostingWFDesigner.xaml i wklej następujący kod do niego, aby zdefiniować interfejsu użytkownika dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2bf22-132">Open the RehostingWFDesigner.xaml file and paste the following code into it to define the UI for the application.</span></span>  
  
    ```xml  
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
  
13. <span data-ttu-id="2bf22-133">Aby skojarzyć Projektant działań z typem działania, że Projektant działań należy zarejestrować się w magazynie metadanych.</span><span class="sxs-lookup"><span data-stu-id="2bf22-133">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="2bf22-134">Aby to zrobić, należy dodać `RegisterMetadata` metody `RehostingWFDesigner` klasy.</span><span class="sxs-lookup"><span data-stu-id="2bf22-134">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="2bf22-135">W zakresie `RegisterMetadata` metody, Utwórz <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> obiekt i wywołanie <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metodę, aby dodać atrybuty do niego.</span><span class="sxs-lookup"><span data-stu-id="2bf22-135">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="2bf22-136">Wywołanie <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> metody w celu dodania <xref:System.Activities.Presentation.Metadata.AttributeTable> w magazynie metadanych.</span><span class="sxs-lookup"><span data-stu-id="2bf22-136">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="2bf22-137">Poniższy kod zawiera logikę rehosting projektanta.</span><span class="sxs-lookup"><span data-stu-id="2bf22-137">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="2bf22-138">Rejestruje metadanych, umieszcza `SimpleNativeActivity` do przybornika i tworzy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="2bf22-138">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="2bf22-139">Umieść ten kod do pliku RehostingWFDesigner.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="2bf22-139">Put this code into the RehostingWFDesigner.xaml.cs file.</span></span>  
  
    ```  
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
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
                // add custom activity to toolbox  
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));  
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
14. <span data-ttu-id="2bf22-140">Kliknij prawym przyciskiem myszy katalogu odwołania w Eksploratorze rozwiązań i wybierz **Dodawanie odwołania...**</span><span class="sxs-lookup"><span data-stu-id="2bf22-140">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="2bf22-141">Aby wyświetlić **Dodaj odwołanie** dialogu.</span><span class="sxs-lookup"><span data-stu-id="2bf22-141">to bring up the **Add Reference** dialogue.</span></span>  
  
15. <span data-ttu-id="2bf22-142">Kliknij przycisk **.NET** zlokalizuj zestawu o nazwie **System.Activities.Core.Presentation**, zaznacz go i kliknij **OK**.</span><span class="sxs-lookup"><span data-stu-id="2bf22-142">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>  
  
16. <span data-ttu-id="2bf22-143">Przy użyciu tej samej procedury, dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="2bf22-143">Using the same procedure, add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="2bf22-144">System.Data.DataSetExtensions.dll</span><span class="sxs-lookup"><span data-stu-id="2bf22-144">System.Data.DataSetExtensions.dll</span></span>  
  
    2.  <span data-ttu-id="2bf22-145">System.Activities.Presentation.dll</span><span class="sxs-lookup"><span data-stu-id="2bf22-145">System.Activities.Presentation.dll</span></span>  
  
    3.  <span data-ttu-id="2bf22-146">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="2bf22-146">System.ServiceModel.Activities.dll</span></span>  
  
17. <span data-ttu-id="2bf22-147">Otwórz plik App.xaml i zmień wartość StartUpUri "RehostingWFDesigner.xaml".</span><span class="sxs-lookup"><span data-stu-id="2bf22-147">Open the App.xaml file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>  
  
18. <span data-ttu-id="2bf22-148">Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksploratora rozwiązań**, wybierz pozycję **Dodaj**, następnie **nowy element...**</span><span class="sxs-lookup"><span data-stu-id="2bf22-148">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="2bf22-149">Aby wyświetlić **Dodaj nowy element** dialog i wybierz **przepływu pracy** formularz kategorii **zainstalowane szablony** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="2bf22-149">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>  
  
19. <span data-ttu-id="2bf22-150">Wybierz **Projektant działań** szablonu, nadaj jej nazwę `SimpleNativeDesigner`i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="2bf22-150">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>  
  
20. <span data-ttu-id="2bf22-151">Otwórz plik SimpleNativeDesigner.xaml i wklej następujący kod do niego.</span><span class="sxs-lookup"><span data-stu-id="2bf22-151">Open the SimpleNativeDesigner.xaml file and paste the following code into it.</span></span> <span data-ttu-id="2bf22-152">Należy pamiętać, ten kod zawiera <xref:System.Activities.Presentation.ActivityDesigner> jako element główny i pokazuje sposób powiązania jest używany do integrowania <xref:System.Activities.Presentation.WorkflowItemPresenter> w z projektantem, więc typ podrzędny mogą być wyświetlane w Projektancie Twoje działania złożonego.</span><span class="sxs-lookup"><span data-stu-id="2bf22-152">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2bf22-153">Schemat dla <xref:System.Activities.Presentation.ActivityDesigner> umożliwia dodanie tylko jeden element podrzędny elementu do definicji projektanta działań niestandardowych; jednak ten element może być `StackPanel`, `Grid`, lub niektóre inne złożonego elementu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2bf22-153">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>  
  
    ```xml  
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
  
21. <span data-ttu-id="2bf22-154">Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksploratora rozwiązań**, wybierz pozycję **Dodaj**, następnie **nowy element...**</span><span class="sxs-lookup"><span data-stu-id="2bf22-154">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="2bf22-155">Aby wyświetlić **Dodaj nowy element** dialog i wybierz **przepływu pracy** formularz kategorii **zainstalowane szablony** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="2bf22-155">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>  
  
22. <span data-ttu-id="2bf22-156">Wybierz **działania związane z kodem** szablonu, nadaj jej nazwę `SimpleNativeActivity`i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="2bf22-156">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>  
  
23. <span data-ttu-id="2bf22-157">Implementowanie `SimpleNativeActivity` klasy wprowadzając następujący kod do pliku SimpleNativeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="2bf22-157">Implement the `SimpleNativeActivity` class by entering the following code into the SimpleNativeActivity.cs file.</span></span>  
  
    ```  
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
  
24. <span data-ttu-id="2bf22-158">Wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="2bf22-158">Select **Build Solution** from the **Build** menu.</span></span>  
  
25. <span data-ttu-id="2bf22-159">Wybierz **uruchomić bez debugowania** z **debugowania** menu, aby otworzyć okno rehosted projektowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2bf22-159">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>  
  
### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="2bf22-160">Aby utworzyć designer działań niestandardowych, za pomocą WorkflowItemsPresenter</span><span class="sxs-lookup"><span data-stu-id="2bf22-160">To create a custom activity designer using WorkflowItemsPresenter</span></span>  
  
1.  <span data-ttu-id="2bf22-161">Procedura drugi Projektant działań niestandardowych jest równoleżników pierwsza z kilka zmian, z których pierwszy polega na nazwę drugiego aplikacji `UsingWorkflowItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="2bf22-161">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="2bf22-162">Ta aplikacja nie definiuje również nowe niestandardowe działanie.</span><span class="sxs-lookup"><span data-stu-id="2bf22-162">Also this application does not define a new custom activity.</span></span>  
  
2.  <span data-ttu-id="2bf22-163">Podstawowe różnice są zawarte w plikach CustomParallelDesigner.xaml i RehostingWFDesigner.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="2bf22-163">Key differences are contained in the CustomParallelDesigner.xaml and RehostingWFDesigner.xaml.cs files.</span></span> <span data-ttu-id="2bf22-164">Oto kod z pliku CustomParallelDesigne.xaml, który definiuje interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2bf22-164">Here is the code from the CustomParallelDesigne.xaml file that defines the UI.</span></span>  
  
    ```xml  
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
  
3.  <span data-ttu-id="2bf22-165">Oto kod z pliku RehostingWFDesigner.xaml.cs, który zapewnia rehosting logiki.</span><span class="sxs-lookup"><span data-stu-id="2bf22-165">Here is the code from the RehostingWFDesigner.xaml.cs file that provides the rehosting logic.</span></span>  
  
    ```  
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
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2bf22-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bf22-166">See Also</span></span>  
 <xref:System.Activities.Presentation.ActivityDesigner>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 <xref:System.Activities.Presentation.WorkflowViewElement>  
 <xref:System.Activities.Presentation.Model.ModelItem>  
 [<span data-ttu-id="2bf22-167">Dostosowywanie projektu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2bf22-167">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
