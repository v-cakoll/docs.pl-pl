---
title: Niestandardowi projektanci złożonych — Prezenter elementu przepływu pracy
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 7519ea560bab1e0c6651ad0b37c8477297b0d64d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526833"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>Niestandardowi projektanci złożonych — Prezenter elementu przepływu pracy
<xref:System.Activities.Presentation.WorkflowItemPresenter> Typ klucza w WF projektanta modelu programowania umożliwiający tworzenie "strefy listy" gdzie można umieścić dowolne działanie. W tym przykładzie przedstawiono sposób tworzenia projektanta działań, który uwypukli najistotniejsze takiej "listy strefy."  
  
 W tym przykładzie przedstawiono:  
  
## <a name="demonstrates"></a>Demonstracje  
  
-   Tworzenie niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemPresenter>.  
  
-   Rejestrowanie niestandardowego projektanta, przy użyciu magazynu metadanych.  
  
-   Programowania rehostowanym przybornika w sposób deklaratywny i obowiązkowo.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W tym przykładzie kod:  
  
-   Niestandardowego projektanta działań zaprojektowano pod kątem `SimpleNativeActivity` klasy.  
  
-   Tworzenie niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemPresenter>.  
  
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
  
 Zwróć uwagę na użycie powiązanie danych WPF można powiązać `ModelItem.Body`. `ModelItem` jest to właściwość na <xref:System.Activities.Presentation.ActivityDesigner> odwołujący się do obiektu źródłowego projektanta jest używany, w tym przypadku **SimpleNativeActivity**.  
  
#### <a name="to-setup-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [Tworzenie aplikacji przy użyciu Projektanta przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
