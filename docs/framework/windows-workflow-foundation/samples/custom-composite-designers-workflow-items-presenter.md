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
# <a name="custom-composite-designers---workflow-items-presenter"></a>Niestandardowi projektanci złożonych — Prezenter elementy przepływu pracy
<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> Typ klucza w WF projektanta model programowania, który umożliwia edytowanie kolekcję elementów zawartych. Niniejszy przykład pokazuje sposób kompilowania, Projektant działań, która udostępnia można edytować kolekcji.

 W tym przykładzie przedstawiono:

-   Tworzenie niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.

-   Tworzenie projektanta działań przy użyciu widoku "zwiniętego" i "rozwiniętego".

-   Zastępowanie domyślnego projektanta w rehostowanym aplikacji.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1.  Otwórz **UsingWorkflowItemsPresenter.sln** przykładowe rozwiązanie dla języka C# lub VB w programie Visual Studio 2010.

2.  Skompiluj i uruchom rozwiązanie. Powinna zostać otwarta aplikacja projektanta rehostowanym przepływu pracy i działania można przeciągnąć na kanwę.

## <a name="sample-highlights"></a>Najważniejsze funkcje próbki
 Kod w tym przykładzie przedstawiono poniżej:

-   Działanie programu designer zaprojektowano pod kątem:  `Parallel`

-   Tworzenie niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>. Kilka kwestii, które zwracają uwagę na:

    -   Zwróć uwagę na użycie powiązanie danych WPF można powiązać `ModelItem.Branches`. `ModelItem` jest to właściwość na `WorkflowElementDesigner` odwołujący się do obiektu źródłowego projektanta jest używany, w tym przypadku nasze `Parallel`.

    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Można umieścić element wizualny, aby wyświetlić między poszczególne elementy w kolekcji.

    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> jest szablon, który można przekazać do określania układu elementów w kolekcji. W tym przypadku jest używany panel stosu poziomej.

 Ten poniższy przykład kodu pokazuje to.

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

-   Wykonaj stowarzyszenie `DesignerAttribute` do `Parallel` typu i następnie dane wyjściowe zgłaszane atrybutów.

    -   Najpierw należy zarejestrować wszystkie domyślne projektantów.

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

    -   Następnie zastąp równoległego w `RegisterCustomMetadata` metody.

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

-   Na koniec Zwróć uwagę na użycie różnych szablonów danych i wyzwalaczy, aby wybrać odpowiedni szablon na podstawie `IsRootDesigner` właściwości.

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
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [Tworzenie aplikacji przy użyciu Projektanta przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
