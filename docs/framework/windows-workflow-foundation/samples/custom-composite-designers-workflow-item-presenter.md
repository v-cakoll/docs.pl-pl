---
title: Projektanci niestandardowych elementów złożonych — prezenter elementu przepływu pracy
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 239f7ccd81d5bb60eed32298220df215b09e3e47
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038372"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="98541-102">Projektanci niestandardowych elementów złożonych — prezenter elementu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="98541-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="98541-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> Jest to typ klucza w modelu programowania projektanta WF, który umożliwia tworzenie "upuszczania strefy", gdzie można umieścić dowolne działanie.</span><span class="sxs-lookup"><span data-stu-id="98541-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="98541-104">Ten przykład pokazuje, jak utworzyć projektanta działań, który ma takie same "strefy upuszczania".</span><span class="sxs-lookup"><span data-stu-id="98541-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

 <span data-ttu-id="98541-105">Ten przykład ilustruje:</span><span class="sxs-lookup"><span data-stu-id="98541-105">This sample demonstrates:</span></span>

## <a name="demonstrates"></a><span data-ttu-id="98541-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="98541-106">Demonstrates</span></span>

- <span data-ttu-id="98541-107">Tworzenie niestandardowego projektanta działań za pomocą <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="98541-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="98541-108">Rejestrowanie niestandardowego projektanta przy użyciu magazynu metadanych.</span><span class="sxs-lookup"><span data-stu-id="98541-108">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="98541-109">Programowanie przehostowanego paska narzędzi w sposób deklaratywny i niezbędny.</span><span class="sxs-lookup"><span data-stu-id="98541-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="98541-110">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="98541-110">Sample Details</span></span>
 <span data-ttu-id="98541-111">Kod dla tego przykładu pokazuje:</span><span class="sxs-lookup"><span data-stu-id="98541-111">The code for this sample shows:</span></span>

- <span data-ttu-id="98541-112">Projektant działań niestandardowych został skompilowany dla `SimpleNativeActivity` klasy.</span><span class="sxs-lookup"><span data-stu-id="98541-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="98541-113">Tworzenie niestandardowego projektanta działań za pomocą <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="98541-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
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

 <span data-ttu-id="98541-114">Zwróć uwagę na użycie powiązania danych WPF do powiązania `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="98541-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="98541-115">`ModelItem`jest właściwością <xref:System.Activities.Presentation.ActivityDesigner> , która odwołuje się do obiektu bazowego, który jest używany przez projektanta, w tym przypadku **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="98541-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="98541-116">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="98541-116">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="98541-117">Otwórz rozwiązanie w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="98541-117">Open the solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="98541-118">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="98541-118">Press F5 to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98541-119">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="98541-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98541-120">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="98541-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="98541-121">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="98541-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98541-122">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="98541-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="98541-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98541-123">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="98541-124">Tworzenie aplikacji przy użyciu Projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="98541-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
