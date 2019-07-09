---
title: Projektanci niestandardowych elementów złożonych — prezenter elementu przepływu pracy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: b28981196490e249d053ecd1704f6ba978585520
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662866"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="87915-102">Projektanci niestandardowych elementów złożonych — prezenter elementu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="87915-102">Custom Composite Designers - Workflow Items Presenter</span></span>

<span data-ttu-id="87915-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> Typ klucza w WF projektanta model programowania, który umożliwia edytowanie kolekcję elementów zawartych.</span><span class="sxs-lookup"><span data-stu-id="87915-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="87915-104">Niniejszy przykład pokazuje sposób kompilowania, Projektant działań, która udostępnia można edytować kolekcji.</span><span class="sxs-lookup"><span data-stu-id="87915-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

<span data-ttu-id="87915-105">W tym przykładzie przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="87915-105">This sample demonstrates:</span></span>

- <span data-ttu-id="87915-106">Tworzenie niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87915-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="87915-107">Tworzenie projektanta działań przy użyciu widoku "zwiniętego" i "rozwiniętego".</span><span class="sxs-lookup"><span data-stu-id="87915-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

- <span data-ttu-id="87915-108">Zastępowanie domyślnego projektanta w rehostowanym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87915-108">Overriding a default designer in a rehosted application.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="87915-109">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="87915-109">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="87915-110">Otwórz **UsingWorkflowItemsPresenter.sln** przykładowe rozwiązanie dla języka C# lub VB w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="87915-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in Visual Studio 2010.</span></span>

2. <span data-ttu-id="87915-111">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="87915-111">Build and run the solution.</span></span> <span data-ttu-id="87915-112">Powinna zostać otwarta aplikacja projektanta rehostowanym przepływu pracy i działania można przeciągnąć na kanwę.</span><span class="sxs-lookup"><span data-stu-id="87915-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="87915-113">Najważniejsze funkcje próbki</span><span class="sxs-lookup"><span data-stu-id="87915-113">Sample Highlights</span></span>

<span data-ttu-id="87915-114">Kod w tym przykładzie przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="87915-114">The code for this sample shows the following:</span></span>

- <span data-ttu-id="87915-115">Działanie programu designer zaprojektowano pod kątem:  `Parallel`</span><span class="sxs-lookup"><span data-stu-id="87915-115">The activity a designer is built for:  `Parallel`</span></span>

- <span data-ttu-id="87915-116">Tworzenie niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87915-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87915-117">Kilka kwestii, które zwracają uwagę na:</span><span class="sxs-lookup"><span data-stu-id="87915-117">A few things to point out:</span></span>

  - <span data-ttu-id="87915-118">Zwróć uwagę na użycie powiązanie danych WPF można powiązać `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="87915-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="87915-119">`ModelItem` jest to właściwość na `WorkflowElementDesigner` odwołujący się do obiektu źródłowego projektanta jest używany, w tym przypadku nasze `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="87915-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

  - <span data-ttu-id="87915-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Można umieścić element wizualny, aby wyświetlić między poszczególne elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="87915-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

  - <span data-ttu-id="87915-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> jest szablon, który można przekazać do określania układu elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="87915-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="87915-122">W tym przypadku jest używany panel stosu poziomej.</span><span class="sxs-lookup"><span data-stu-id="87915-122">In this case, a horizontal stack panel is used.</span></span>

  <span data-ttu-id="87915-123">Ten poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="87915-123">This following example code shows this.</span></span>

  ```xaml
  <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                Items="{Binding Path=ModelItem.Branches}">
      <sad:WorkflowItemsPresenter.SpacerTemplate>
        <DataTemplate>
          <Ellipse Width="10" Height="10" Fill="Black"/>
        </DataTemplate>
      </sad:WorkflowItemsPresenter.SpacerTemplate>
      <sad:WorkflowItemsPresenter.ItemsPanel>
        <ItemsPanelTemplate>
          <StackPanel Orientation="Horizontal"/>
        </ItemsPanelTemplate>
      </sad:WorkflowItemsPresenter.ItemsPanel>
    </sad:WorkflowItemsPresenter>
  ```

- <span data-ttu-id="87915-124">Wykonaj stowarzyszenie `DesignerAttribute` do `Parallel` typu i następnie dane wyjściowe zgłaszane atrybutów.</span><span class="sxs-lookup"><span data-stu-id="87915-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

  - <span data-ttu-id="87915-125">Najpierw należy zarejestrować wszystkie domyślne projektantów.</span><span class="sxs-lookup"><span data-stu-id="87915-125">First, register all of the default designers.</span></span>

    <span data-ttu-id="87915-126">Poniżej przedstawiono przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="87915-126">The following is the code example.</span></span>

    ```csharp
    // register metadata
    (new DesignerMetadata()).Register();
    RegisterCustomMetadata();
    ```

    ```vb
    ' register metadata
    Dim metadata = New DesignerMetadata()
    metadata.Register()
    ' register custom metadata
    RegisterCustomMetadata()
    ```

  - <span data-ttu-id="87915-127">Następnie zastąp równoległego w `RegisterCustomMetadata` metody.</span><span class="sxs-lookup"><span data-stu-id="87915-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

    <span data-ttu-id="87915-128">Poniższy kod przedstawia to w języku C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="87915-128">The following code shows this in C# and Visual Basic.</span></span>

    ```csharp
    void RegisterCustomMetadata()
    {
          AttributeTableBuilder builder = new AttributeTableBuilder();
          builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
          MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

    ```vb
    Sub RegisterCustomMetadata()
       Dim builder As New AttributeTableBuilder()
       builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))
       MetadataStore.AddAttributeTable(builder.CreateTable())
    End Sub
    ```

- <span data-ttu-id="87915-129">Na koniec Zwróć uwagę na użycie różnych szablonów danych i wyzwalaczy, aby wybrać odpowiedni szablon na podstawie `IsRootDesigner` właściwości.</span><span class="sxs-lookup"><span data-stu-id="87915-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

  <span data-ttu-id="87915-130">Poniżej przedstawiono przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="87915-130">The following is the code example.</span></span>

  ```xaml
  <sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"
      xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">
    <sad:ActivityDesigner.Resources>
      <DataTemplate x:Key="Expanded">
        <StackPanel>
          <TextBlock>This is the Expanded View</TextBlock>
          <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                      Items="{Binding Path=ModelItem.Branches}">
            <sad:WorkflowItemsPresenter.SpacerTemplate>
              <DataTemplate>
                <Ellipse Width="10" Height="10" Fill="Black"/>
              </DataTemplate>
            </sad:WorkflowItemsPresenter.SpacerTemplate>
            <sad:WorkflowItemsPresenter.ItemsPanel>
              <ItemsPanelTemplate>
                <StackPanel Orientation="Horizontal"/>
              </ItemsPanelTemplate>
            </sad:WorkflowItemsPresenter.ItemsPanel>
          </sad:WorkflowItemsPresenter>
        </StackPanel>
      </DataTemplate>
      <DataTemplate x:Key="Collapsed">
        <TextBlock>This is the Collapsed View</TextBlock>
      </DataTemplate>
      <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
        <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
        <Style.Triggers>
          <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">
            <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
          </DataTrigger>
        </Style.Triggers>
      </Style>
    </sad: ActivityDesigner.Resources>
    <Grid>
      <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
    </Grid>
  </sad: ActivityDesigner>
  ```

> [!IMPORTANT]
> <span data-ttu-id="87915-131">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="87915-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="87915-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="87915-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="87915-133">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="87915-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87915-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="87915-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a><span data-ttu-id="87915-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87915-135">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="87915-136">Tworzenie aplikacji przy użyciu Projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="87915-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
