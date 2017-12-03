---
title: "Niestandardowe projektantów złożonego - Prezenterze element przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bba89e9da78fd96d0cd7d61e825e4792729bae5b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="6356f-102">Niestandardowe projektantów złożonego - Prezenterze element przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6356f-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="6356f-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> Jest typem klucza w WF projektanta programowania modelu, który umożliwia tworzenie "strefy docelowej" rozmieszczenia dowolnego działania.</span><span class="sxs-lookup"><span data-stu-id="6356f-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="6356f-104">W tym przykładzie przedstawiono sposób tworzenia Projektant działań tego powierzchni takiej "upuszczania strefy."</span><span class="sxs-lookup"><span data-stu-id="6356f-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>  
  
 <span data-ttu-id="6356f-105">W tym przykładzie przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="6356f-105">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6356f-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="6356f-106">Demonstrates</span></span>  
  
-   <span data-ttu-id="6356f-107">Tworzenie Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="6356f-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
-   <span data-ttu-id="6356f-108">Rejestrowanie niestandardowe projektanta przy użyciu magazynu metadanych.</span><span class="sxs-lookup"><span data-stu-id="6356f-108">Registering the custom designer using the metadata store.</span></span>  
  
-   <span data-ttu-id="6356f-109">Programowanie przybornika rehosted deklaratywnie i imperatively.</span><span class="sxs-lookup"><span data-stu-id="6356f-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="6356f-110">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="6356f-110">Sample Details</span></span>  
 <span data-ttu-id="6356f-111">Dla tego przykładu kod:</span><span class="sxs-lookup"><span data-stu-id="6356f-111">The code for this sample shows:</span></span>  
  
-   <span data-ttu-id="6356f-112">Projektant działań niestandardowych zaprojektowano pod kątem `SimpleNativeActivity` klasy.</span><span class="sxs-lookup"><span data-stu-id="6356f-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>  
  
-   <span data-ttu-id="6356f-113">Tworzenie Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="6356f-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
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
  
 <span data-ttu-id="6356f-114">Zwróć uwagę na użycie powiązanie danych WPF powiązać `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="6356f-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="6356f-115">`ModelItem`jest właściwością na <xref:System.Activities.Presentation.ActivityDesigner> odwołujący się do obiektu źródłowego projektanta jest używany, w tym przypadku **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="6356f-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>  
  
#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="6356f-116">Aby skonfigurować, skompilować i uruchomić próbki</span><span class="sxs-lookup"><span data-stu-id="6356f-116">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6356f-117">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6356f-117">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6356f-118">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="6356f-118">Press F5 to compile and run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6356f-119">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="6356f-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6356f-120">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="6356f-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6356f-121">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="6356f-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6356f-122">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6356f-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="6356f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6356f-123">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [<span data-ttu-id="6356f-124">Tworzenie aplikacji przy użyciu Projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6356f-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
