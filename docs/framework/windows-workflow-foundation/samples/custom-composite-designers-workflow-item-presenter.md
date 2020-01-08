---
title: Projektanci niestandardowych elementów złożonych — prezenter elementu przepływu pracy
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: d1047b8be35545e83eaa8788b53751b6b0056984
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338044"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="e4e90-102">Projektanci niestandardowych elementów złożonych — prezenter elementu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e4e90-102">Custom Composite Designers - Workflow Item Presenter</span></span>

<span data-ttu-id="e4e90-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> jest typem klucza w modelu programowania programu WF Designer, który umożliwia tworzenie "upuszczania strefy", gdzie można umieścić dowolne działanie.</span><span class="sxs-lookup"><span data-stu-id="e4e90-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="e4e90-104">Ten przykład pokazuje, jak utworzyć projektanta działań, który ma takie same "strefy upuszczania".</span><span class="sxs-lookup"><span data-stu-id="e4e90-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

<span data-ttu-id="e4e90-105">Ten przykład ilustruje:</span><span class="sxs-lookup"><span data-stu-id="e4e90-105">This sample demonstrates:</span></span>

- <span data-ttu-id="e4e90-106">Tworzenie niestandardowego projektanta działań za pomocą <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="e4e90-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="e4e90-107">Rejestrowanie niestandardowego projektanta przy użyciu magazynu metadanych.</span><span class="sxs-lookup"><span data-stu-id="e4e90-107">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="e4e90-108">Programowanie przehostowanego paska narzędzi w sposób deklaratywny i niezbędny.</span><span class="sxs-lookup"><span data-stu-id="e4e90-108">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="e4e90-109">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="e4e90-109">Sample Details</span></span>

<span data-ttu-id="e4e90-110">Kod dla tego przykładu pokazuje:</span><span class="sxs-lookup"><span data-stu-id="e4e90-110">The code for this sample shows:</span></span>

- <span data-ttu-id="e4e90-111">Projektant działań niestandardowych został skompilowany dla klasy `SimpleNativeActivity`.</span><span class="sxs-lookup"><span data-stu-id="e4e90-111">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="e4e90-112">Tworzenie niestandardowego projektanta działań za pomocą <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="e4e90-112">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

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

 <span data-ttu-id="e4e90-113">Zwróć uwagę na użycie powiązania danych WPF do powiązania z `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="e4e90-113">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="e4e90-114">`ModelItem` jest właściwością <xref:System.Activities.Presentation.ActivityDesigner> odwołującą się do obiektu źródłowego, który jest używany przez projektanta, w tym przypadku **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="e4e90-114">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="e4e90-115">Konfigurowanie, kompilowanie i uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="e4e90-115">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="e4e90-116">Otwórz rozwiązanie w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4e90-116">Open the solution in Visual Studio.</span></span>

2. <span data-ttu-id="e4e90-117">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="e4e90-117">Press **F5** to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4e90-118">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e4e90-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e4e90-119">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="e4e90-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e4e90-120">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4e90-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4e90-121">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e4e90-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`

## <a name="see-also"></a><span data-ttu-id="e4e90-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4e90-122">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="e4e90-123">Tworzenie aplikacji przy użyciu Projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e4e90-123">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
