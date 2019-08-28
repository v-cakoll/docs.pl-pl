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
# <a name="custom-composite-designers---workflow-item-presenter"></a>Projektanci niestandardowych elementów złożonych — prezenter elementu przepływu pracy
<xref:System.Activities.Presentation.WorkflowItemPresenter> Jest to typ klucza w modelu programowania projektanta WF, który umożliwia tworzenie "upuszczania strefy", gdzie można umieścić dowolne działanie. Ten przykład pokazuje, jak utworzyć projektanta działań, który ma takie same "strefy upuszczania".

 Ten przykład ilustruje:

## <a name="demonstrates"></a>Demonstracje

- Tworzenie niestandardowego projektanta działań za pomocą <xref:System.Activities.Presentation.WorkflowItemPresenter>.

- Rejestrowanie niestandardowego projektanta przy użyciu magazynu metadanych.

- Programowanie przehostowanego paska narzędzi w sposób deklaratywny i niezbędny.

## <a name="sample-details"></a>Przykładowe szczegóły
 Kod dla tego przykładu pokazuje:

- Projektant działań niestandardowych został skompilowany dla `SimpleNativeActivity` klasy.

- Tworzenie niestandardowego projektanta działań za pomocą <xref:System.Activities.Presentation.WorkflowItemPresenter>.

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

 Zwróć uwagę na użycie powiązania danych WPF do powiązania `ModelItem.Body`. `ModelItem`jest właściwością <xref:System.Activities.Presentation.ActivityDesigner> , która odwołuje się do obiektu bazowego, który jest używany przez projektanta, w tym przypadku **SimpleNativeActivity**.

#### <a name="to-setup-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Otwórz rozwiązanie w programie Visual Studio 2010.

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [Tworzenie aplikacji przy użyciu Projektanta przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
