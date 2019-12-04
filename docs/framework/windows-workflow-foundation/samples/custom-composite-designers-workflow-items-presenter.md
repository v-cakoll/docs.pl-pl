---
title: Projektanci niestandardowych elementów złożonych — prezenter elementu przepływu pracy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 542440d6bf9d6809abee1ec37c85c44ce72fd132
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715159"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="8f469-102">Projektanci niestandardowych elementów złożonych — prezenter elementu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8f469-102">Custom Composite Designers - Workflow Items Presenter</span></span>

<span data-ttu-id="8f469-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> jest typem klucza w modelu programowania projektanta WF, który umożliwia edytowanie kolekcji zawartych elementów.</span><span class="sxs-lookup"><span data-stu-id="8f469-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="8f469-104">Ten przykład pokazuje, jak utworzyć projektanta działań, który wyświetla tę kolekcję edytowalną.</span><span class="sxs-lookup"><span data-stu-id="8f469-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

<span data-ttu-id="8f469-105">Ten przykład ilustruje:</span><span class="sxs-lookup"><span data-stu-id="8f469-105">This sample demonstrates:</span></span>

- <span data-ttu-id="8f469-106">Tworzenie niestandardowego projektanta działań za pomocą <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f469-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="8f469-107">Tworzenie projektanta działań z widokiem "zwinięte" i "rozwinięte".</span><span class="sxs-lookup"><span data-stu-id="8f469-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

- <span data-ttu-id="8f469-108">Zastępowanie domyślnego projektanta w aplikacji przehostowanej.</span><span class="sxs-lookup"><span data-stu-id="8f469-108">Overriding a default designer in a rehosted application.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8f469-109">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="8f469-109">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8f469-110">Otwórz przykładowe rozwiązanie **UsingWorkflowItemsPresenter. sln** dla C# programu lub dla języka vb w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="8f469-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in Visual Studio 2010.</span></span>

2. <span data-ttu-id="8f469-111">Kompiluj i uruchamiaj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8f469-111">Build and run the solution.</span></span> <span data-ttu-id="8f469-112">Powinna zostać otwarta aplikacja projektanta przepływów pracy, na której można przeciągnąć działania na kanwę.</span><span class="sxs-lookup"><span data-stu-id="8f469-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="8f469-113">Przykładowe najważniejsze elementy</span><span class="sxs-lookup"><span data-stu-id="8f469-113">Sample Highlights</span></span>

<span data-ttu-id="8f469-114">Kod dla tego przykładu pokazuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="8f469-114">The code for this sample shows the following:</span></span>

- <span data-ttu-id="8f469-115">Działanie, dla którego utworzono projektanta: `Parallel`</span><span class="sxs-lookup"><span data-stu-id="8f469-115">The activity a designer is built for:  `Parallel`</span></span>

- <span data-ttu-id="8f469-116">Tworzenie niestandardowego projektanta działań za pomocą <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f469-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8f469-117">Kilka rzeczy, które należy wskazać:</span><span class="sxs-lookup"><span data-stu-id="8f469-117">A few things to point out:</span></span>

  - <span data-ttu-id="8f469-118">Zwróć uwagę na użycie powiązania danych WPF do powiązania z `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="8f469-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="8f469-119">`ModelItem` jest właściwością `WorkflowElementDesigner` odwołującą się do obiektu źródłowego, który jest używany przez projektanta, w tym przypadku naszych `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="8f469-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

  - <span data-ttu-id="8f469-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> może służyć do umieszczania wizualizacji między poszczególnymi elementami w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8f469-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

  - <span data-ttu-id="8f469-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> to szablon, który można podać w celu określenia układu elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8f469-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="8f469-122">W takim przypadku używany jest poziomy Panel stosu.</span><span class="sxs-lookup"><span data-stu-id="8f469-122">In this case, a horizontal stack panel is used.</span></span>

  <span data-ttu-id="8f469-123">Poniższy przykładowy kod przedstawia ten sposób.</span><span class="sxs-lookup"><span data-stu-id="8f469-123">This following example code shows this.</span></span>

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

- <span data-ttu-id="8f469-124">Wykonaj skojarzenie `DesignerAttribute` z typem `Parallel`, a następnie dane wyjściowe raportowanych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="8f469-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

  - <span data-ttu-id="8f469-125">Najpierw Zarejestruj wszystkie domyślne projektantów.</span><span class="sxs-lookup"><span data-stu-id="8f469-125">First, register all of the default designers.</span></span>

    <span data-ttu-id="8f469-126">Oto przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="8f469-126">The following is the code example.</span></span>

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

  - <span data-ttu-id="8f469-127">Następnie Zastąp metodę Parallel w `RegisterCustomMetadata`.</span><span class="sxs-lookup"><span data-stu-id="8f469-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

    <span data-ttu-id="8f469-128">Poniższy kod ilustruje to w C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8f469-128">The following code shows this in C# and Visual Basic.</span></span>

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

- <span data-ttu-id="8f469-129">Na koniec należy zwrócić uwagę na użycie różnych szablonów danych i wyzwalaczy, aby wybrać odpowiedni szablon na podstawie właściwości `IsRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="8f469-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

  <span data-ttu-id="8f469-130">Oto przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="8f469-130">The following is the code example.</span></span>

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
> <span data-ttu-id="8f469-131">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8f469-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8f469-132">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="8f469-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8f469-133">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f469-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8f469-134">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8f469-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a><span data-ttu-id="8f469-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f469-135">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="8f469-136">Tworzenie aplikacji przy użyciu Projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8f469-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
