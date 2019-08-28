---
title: Rehostowanie projektanta
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: ecbea5822825cca5f3f5cf40e20d5d249b17b07c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038194"
---
# <a name="designer-rehosting"></a>Rehostowanie projektanta
Rehostowanie projektanta jest typowym scenariuszem, który odnosi się do hostingu kanwy projektowania przepływu pracy w aplikacji niestandardowej. Aplikacja hostingu większość osób zna program Visual Studio, jednak istnieje kilka scenariuszy, w których wyświetlanie projektanta przepływu pracy w aplikacji może być przydatne:  
  
- Monitorowanie aplikacji (umożliwienie użytkownikowi końcowemu wizualizacji procesu, a także danych środowiska uruchomieniowego dotyczących procesu, takich jak aktualnie aktywny stan, zagregowane dane czasu wykonywania lub inne informacje o wystąpieniu przepływu pracy).  
  
- Aplikacje, które umożliwiają użytkownikowi dostosowanie procesu przy użyciu ograniczonego zestawu działań.  
  
 Aby zapewnić obsługę tych typów aplikacji, Projektant przepływów pracy jest dostarczany wewnątrz .NET Framework i może być hostowany w aplikacji WPF lub w aplikacji WinForms z odpowiednim kodem hostingu WPF. Ten przykład ilustruje:  
  
- Rehostowanie projektanta WF.  
  
- Również przy użyciu narzędzia Hostowanie i siatki właściwości.  
  
## <a name="rehosting-the-designer"></a>Hostowanie projektanta  
 Ten przykład pokazuje, jak utworzyć układ WPF, aby zawierał projektanta, widoczny w poniższym układzie siatki (kod przybornika został pominięty w przypadku problemów z miejscem). Zwróć uwagę na nazwy obramowań zawierające projektanta i siatkę właściwości.  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 Następnie przykład tworzy projektanta i kojarzy jego podstawową <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> z odpowiednim kontenerem w interfejsie użytkownika. W poniższym przykładzie znajduje się kilka dodatkowych wierszy kodu, które stanowią objaśnienie niektórych wyjaśnień. <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Wywołanie jest wymagane do skojarzenia domyślnego projektanta działań dla działań dostarczonych z .NET Framework. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>jest wywoływana, aby przekazać element WF do edycji. Na koniec <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (główna Kanwa) i (siatka właściwości) są umieszczane na powierzchni interfejsu użytkownika. <xref:System.Activities.Presentation.WorkflowDesigner.View%2A>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a>Korzystanie z przybornika przehostowanego  
 Ten przykład używa wbudowanej kontrolki przybornika w języku XAML. Należy zauważyć, że w kodzie, jeden może przekazać typ do <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktora.  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a>Korzystanie z przykładu  
  
1. Otwórz rozwiązanie DesignerRehosting. sln w programie Visual Studio 2010.  
  
2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
3. Aplikacja WPF zaczyna się od zahostowanego projektanta.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
