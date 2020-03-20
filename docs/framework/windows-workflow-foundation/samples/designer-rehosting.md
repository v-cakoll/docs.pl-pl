---
title: Rehostowanie projektanta
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: b72e3450799db40988c8b99e4db3707de330d8ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182823"
---
# <a name="designer-rehosting"></a>Rehostowanie projektanta
Ponowne hostowanie projektanta jest typowym scenariuszem, który odnosi się do hostowania kanwy projektu przepływu pracy wewnątrz aplikacji niestandardowej. Aplikacja hostingowa, z której większość osób jest zaznajomiona z programem Visual Studio, jednak istnieje wiele scenariuszy, w których wyświetlanie projektanta przepływu pracy w aplikacji może być przydatne:  
  
- Monitorowanie aplikacji (umożliwiając użytkownikowi końcowemu wizualizowanie procesu, a także dane środowiska wykonawczego o procesie, takie jak aktualnie aktywny stan, zagregowane dane czasu wykonywania lub inne informacje o wystąpieniu przepływu pracy).  
  
- Aplikacje, które umożliwiają użytkownikowi dostosowanie procesu za pomocą ograniczonego zestawu działań.  
  
 Do obsługi tego typu aplikacji, projektant przepływu pracy jest dostarczany wewnątrz .NET Framework i może być obsługiwany wewnątrz aplikacji WPF lub w aplikacji WinForms z odpowiednim kodem hostingu WPF. W tym przykładzie pokazano:  
  
- Ponowne hostowanie projektanta WF.  
  
- Za pomocą rehosted przybornik i siatki właściwości, jak również.  
  
## <a name="rehosting-the-designer"></a>Ponowne hostowanie projektanta  
 W tym przykładzie pokazano, jak utworzyć układ WPF zawierają projektanta, widoczne w następującym układzie siatki (kod przybornika pominięte dla kwestii miejsca). Zwróć uwagę na nazewnictwo obramowań, które zawierają siatkę projektanta i właściwości.  
  
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
  
 Następnie przykład tworzy projektanta i kojarzy jego podstawowy <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> z odpowiednim kontenerem w interfejsie użytkownika. Istnieje kilka dodatkowych wierszy kodu w poniższym przykładzie, które zasługują na pewne wyjaśnienie. Wywołanie <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> jest wymagane do skojarzenia domyślnych projektantów działań dla działań dostarczanych z programem .NET Framework. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>jest wywoływana do przekazania w elemencie WF do edycji. Na koniec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (podstawowa kanwa) i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (siatka właściwości) są umieszczane na powierzchni interfejsu użytkownika.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Korzystanie z przybornika hostowanego ponownie  
 W tym przykładzie użyto kontroli zestawu narzędzi rehosted deklaratywnie w języku XAML. Należy zauważyć, że w kodzie <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> można przekazać typ do konstruktora.  
  
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
  
#### <a name="using-the-sample"></a>Korzystanie z próbki  
  
1. Otwórz rozwiązanie DesignerRehosting.sln w programie Visual Studio 2010.  
  
2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
3. Aplikacja WPF rozpoczyna się od projektanta rehosted.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
