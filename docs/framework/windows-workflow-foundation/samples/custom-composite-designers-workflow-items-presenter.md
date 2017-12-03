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
# <a name="custom-composite-designers---workflow-items-presenter"></a>Niestandardowe projektantów złożonego - Prezenterze elementy przepływu pracy
<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> Jest typem klucza w WF projektanta modelu programowania umożliwiający edytowanie kolekcję elementów zawartych w niej. W tym przykładzie pokazano, jak zbudować Projektant działań, która udostępnia można edytować kolekcji.  
  
 W tym przykładzie przedstawiono:  
  
-   Tworzenie Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.  
  
-   Tworzenie Projektant działań z widokiem "zwiniętego" i "rozwiniętego".  
  
-   Zastępowanie domyślnego projektanta w rehosted aplikacji.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz **UsingWorkflowItemsPresenter.sln** przykładowe rozwiązanie dla C# lub VB. w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Tworzenie i uruchamianie rozwiązania. Powinno spowodować otwarcie aplikacji projektanta rehosted przepływu pracy i działania można przeciągnąć na kanwę.  
  
## <a name="sample-highlights"></a>Najważniejsze funkcje próbki  
 Kod w tym przykładzie przedstawiono poniżej:  
  
-   Działanie projektanta jest przeznaczony dla:`Parallel`  
  
-   Tworzenie Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>. Kilka rzeczy, aby wskazać:  
  
    -   Zwróć uwagę na użycie powiązanie danych WPF powiązać `ModelItem.Branches`. `ModelItem`jest właściwością na `WorkflowElementDesigner` odwołujący się do obiektu źródłowego projektanta jest używany, w tym przypadku naszego `Parallel`.  
  
    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Można umieścić element wizualny, aby wyświetlić między poszczególne elementy w kolekcji.  
  
    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType>to szablon, który może zostać dostarczona do określania układu elementów w kolekcji. W takim przypadku służy panel stosu poziomej.  
  
 To poniższy przykład kodu pokazuje to.  
  
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
  
-   Wykonaj skojarzeniem `DesignerAttribute` do `Parallel` typu i następnie dane wyjściowe zgłosił atrybutów.  
  
    -   Najpierw zarejestrować wszystkie domyślne projektantów.  
  
 Poniżej przedstawiono przykładowy kod.  
  
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
  
    -   Następnie zastąp równoległe w `RegisterCustomMetadata` metody.  
  
 Poniższy kod przedstawia to w języku C# i Visual Basic.  
 
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
  
-   Na koniec, zwróć uwagę na użycie różnych szablonów danych i wyzwalaczy, aby wybrać odpowiedni szablon na podstawie `IsRootDesigner` właściwości.  
  
 Poniżej przedstawiono przykładowy kod.  
  
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
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 [Tworzenie aplikacji przy użyciu Projektanta przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
