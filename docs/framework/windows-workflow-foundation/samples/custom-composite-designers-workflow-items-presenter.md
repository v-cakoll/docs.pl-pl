---
title: Niestandardowi projektanci złożonych — Prezenter elementy przepływu pracy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 13d1a76779877bc2ab6d1cbd9c892bf14781e788
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705946"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="6f113-102">Niestandardowi projektanci złożonych — Prezenter elementy przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6f113-102">Custom Composite Designers - Workflow Items Presenter</span></span>
<span data-ttu-id="6f113-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> Typ klucza w WF projektanta model programowania, który umożliwia edytowanie kolekcję elementów zawartych.</span><span class="sxs-lookup"><span data-stu-id="6f113-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="6f113-104">Niniejszy przykład pokazuje sposób kompilowania, Projektant działań, która udostępnia można edytować kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6f113-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

 <span data-ttu-id="6f113-105">W tym przykładzie przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="6f113-105">This sample demonstrates:</span></span>

-   <span data-ttu-id="6f113-106">Tworzenie niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f113-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

-   <span data-ttu-id="6f113-107">Tworzenie projektanta działań przy użyciu widoku "zwiniętego" i "rozwiniętego".</span><span class="sxs-lookup"><span data-stu-id="6f113-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

-   <span data-ttu-id="6f113-108">Zastępowanie domyślnego projektanta w rehostowanym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f113-108">Overriding a default designer in a rehosted application.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6f113-109">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="6f113-109">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="6f113-110">Otwórz **UsingWorkflowItemsPresenter.sln** przykładowe rozwiązanie dla języka C# lub VB w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6f113-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in Visual Studio 2010.</span></span>

2.  <span data-ttu-id="6f113-111">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6f113-111">Build and run the solution.</span></span> <span data-ttu-id="6f113-112">Powinna zostać otwarta aplikacja projektanta rehostowanym przepływu pracy i działania można przeciągnąć na kanwę.</span><span class="sxs-lookup"><span data-stu-id="6f113-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="6f113-113">Najważniejsze funkcje próbki</span><span class="sxs-lookup"><span data-stu-id="6f113-113">Sample Highlights</span></span>
 <span data-ttu-id="6f113-114">Kod w tym przykładzie przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="6f113-114">The code for this sample shows the following:</span></span>

-   <span data-ttu-id="6f113-115">Działanie programu designer zaprojektowano pod kątem:  `Parallel`</span><span class="sxs-lookup"><span data-stu-id="6f113-115">The activity a designer is built for:  `Parallel`</span></span>

-   <span data-ttu-id="6f113-116">Tworzenie niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f113-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6f113-117">Kilka kwestii, które zwracają uwagę na:</span><span class="sxs-lookup"><span data-stu-id="6f113-117">A few things to point out:</span></span>

    -   <span data-ttu-id="6f113-118">Zwróć uwagę na użycie powiązanie danych WPF można powiązać `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="6f113-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="6f113-119">`ModelItem` jest to właściwość na `WorkflowElementDesigner` odwołujący się do obiektu źródłowego projektanta jest używany, w tym przypadku nasze `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="6f113-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

    -   <span data-ttu-id="6f113-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Można umieścić element wizualny, aby wyświetlić między poszczególne elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6f113-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

    -   <span data-ttu-id="6f113-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> jest szablon, który można przekazać do określania układu elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6f113-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="6f113-122">W tym przypadku jest używany panel stosu poziomej.</span><span class="sxs-lookup"><span data-stu-id="6f113-122">In this case, a horizontal stack panel is used.</span></span>

 <span data-ttu-id="6f113-123">Ten poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="6f113-123">This following example code shows this.</span></span>

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

-   <span data-ttu-id="6f113-124">Wykonaj stowarzyszenie `DesignerAttribute` do `Parallel` typu i następnie dane wyjściowe zgłaszane atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6f113-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

    -   <span data-ttu-id="6f113-125">Najpierw należy zarejestrować wszystkie domyślne projektantów.</span><span class="sxs-lookup"><span data-stu-id="6f113-125">First, register all of the default designers.</span></span>

 <span data-ttu-id="6f113-126">Poniżej przedstawiono przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="6f113-126">The following is the code example.</span></span>

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

    -   <span data-ttu-id="6f113-127">Następnie zastąp równoległego w `RegisterCustomMetadata` metody.</span><span class="sxs-lookup"><span data-stu-id="6f113-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

 <span data-ttu-id="6f113-128">Poniższy kod przedstawia to w języku C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6f113-128">The following code shows this in C# and Visual Basic.</span></span>

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

-   <span data-ttu-id="6f113-129">Na koniec Zwróć uwagę na użycie różnych szablonów danych i wyzwalaczy, aby wybrać odpowiedni szablon na podstawie `IsRootDesigner` właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f113-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

 <span data-ttu-id="6f113-130">Poniżej przedstawiono przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="6f113-130">The following is the code example.</span></span>

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
>  <span data-ttu-id="6f113-131">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="6f113-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6f113-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="6f113-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6f113-133">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="6f113-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6f113-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6f113-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="6f113-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f113-135">See also</span></span>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="6f113-136">Tworzenie aplikacji przy użyciu Projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6f113-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
