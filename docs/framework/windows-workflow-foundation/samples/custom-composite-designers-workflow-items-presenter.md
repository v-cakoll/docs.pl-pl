---
title: "Niestandardowe projektantów złożonego - Prezenterze elementy przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b708d39ba6e5f53579f575d5e228de43db3d90a9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="c97cc-102">Niestandardowe projektantów złożonego - Prezenterze elementy przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c97cc-102">Custom Composite Designers - Workflow Items Presenter</span></span>
<span data-ttu-id="c97cc-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> Jest typem klucza w WF projektanta modelu programowania umożliwiający edytowanie kolekcję elementów zawartych w niej.</span><span class="sxs-lookup"><span data-stu-id="c97cc-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="c97cc-104">W tym przykładzie pokazano, jak zbudować Projektant działań, która udostępnia można edytować kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c97cc-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>  
  
 <span data-ttu-id="c97cc-105">W tym przykładzie przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="c97cc-105">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="c97cc-106">Tworzenie Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c97cc-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="c97cc-107">Tworzenie Projektant działań z widokiem "zwiniętego" i "rozwiniętego".</span><span class="sxs-lookup"><span data-stu-id="c97cc-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>  
  
-   <span data-ttu-id="c97cc-108">Zastępowanie domyślnego projektanta w rehosted aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c97cc-108">Overriding a default designer in a rehosted application.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c97cc-109">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="c97cc-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c97cc-110">Otwórz **UsingWorkflowItemsPresenter.sln** przykładowe rozwiązanie dla C# lub VB. w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c97cc-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c97cc-111">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c97cc-111">Build and run the solution.</span></span> <span data-ttu-id="c97cc-112">Powinno spowodować otwarcie aplikacji projektanta rehosted przepływu pracy i działania można przeciągnąć na kanwę.</span><span class="sxs-lookup"><span data-stu-id="c97cc-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>  
  
## <a name="sample-highlights"></a><span data-ttu-id="c97cc-113">Najważniejsze funkcje próbki</span><span class="sxs-lookup"><span data-stu-id="c97cc-113">Sample Highlights</span></span>  
 <span data-ttu-id="c97cc-114">Kod w tym przykładzie przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="c97cc-114">The code for this sample shows the following:</span></span>  
  
-   <span data-ttu-id="c97cc-115">Działanie projektanta jest przeznaczony dla:`Parallel`</span><span class="sxs-lookup"><span data-stu-id="c97cc-115">The activity a designer is built for:  `Parallel`</span></span>  
  
-   <span data-ttu-id="c97cc-116">Tworzenie Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c97cc-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c97cc-117">Kilka rzeczy, aby wskazać:</span><span class="sxs-lookup"><span data-stu-id="c97cc-117">A few things to point out:</span></span>  
  
    -   <span data-ttu-id="c97cc-118">Zwróć uwagę na użycie powiązanie danych WPF powiązać `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="c97cc-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="c97cc-119">`ModelItem`jest właściwością na `WorkflowElementDesigner` odwołujący się do obiektu źródłowego projektanta jest używany, w tym przypadku naszego `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="c97cc-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>  
  
    -   <span data-ttu-id="c97cc-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Można umieścić element wizualny, aby wyświetlić między poszczególne elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c97cc-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>  
  
    -   <span data-ttu-id="c97cc-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType>to szablon, który może zostać dostarczona do określania układu elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c97cc-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="c97cc-122">W takim przypadku służy panel stosu poziomej.</span><span class="sxs-lookup"><span data-stu-id="c97cc-122">In this case, a horizontal stack panel is used.</span></span>  
  
 <span data-ttu-id="c97cc-123">To poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="c97cc-123">This following example code shows this.</span></span>  
  
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
  
-   <span data-ttu-id="c97cc-124">Wykonaj skojarzeniem `DesignerAttribute` do `Parallel` typu i następnie dane wyjściowe zgłosił atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c97cc-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>  
  
    -   <span data-ttu-id="c97cc-125">Najpierw zarejestrować wszystkie domyślne projektantów.</span><span class="sxs-lookup"><span data-stu-id="c97cc-125">First, register all of the default designers.</span></span>  
  
 <span data-ttu-id="c97cc-126">Poniżej przedstawiono przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="c97cc-126">The following is the code example.</span></span>  
  
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
  
    -   <span data-ttu-id="c97cc-127">Następnie zastąp równoległe w `RegisterCustomMetadata` metody.</span><span class="sxs-lookup"><span data-stu-id="c97cc-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>  
  
 <span data-ttu-id="c97cc-128">Poniższy kod przedstawia to w języku C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c97cc-128">The following code shows this in C# and Visual Basic.</span></span>  
 
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
  
-   <span data-ttu-id="c97cc-129">Na koniec, zwróć uwagę na użycie różnych szablonów danych i wyzwalaczy, aby wybrać odpowiedni szablon na podstawie `IsRootDesigner` właściwości.</span><span class="sxs-lookup"><span data-stu-id="c97cc-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>  
  
 <span data-ttu-id="c97cc-130">Poniżej przedstawiono przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="c97cc-130">The following is the code example.</span></span>  
  
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
>  <span data-ttu-id="c97cc-131">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c97cc-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c97cc-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c97cc-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c97cc-133">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="c97cc-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c97cc-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c97cc-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="c97cc-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c97cc-135">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 [<span data-ttu-id="c97cc-136">Tworzenie aplikacji przy użyciu Projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c97cc-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
