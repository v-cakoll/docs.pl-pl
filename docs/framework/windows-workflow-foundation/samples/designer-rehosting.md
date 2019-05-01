---
title: Rehostowanie projektanta
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: b2a51014e34bf27d6f016db71d2c2eaabb906c6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005236"
---
# <a name="designer-rehosting"></a>Rehostowanie projektanta
Rehostowanie projektanta jest to typowy scenariusz, która odwołuje się do hostowania kanwę projektu przepływu pracy w aplikacji niestandardowej. Aplikacji macierzystej, których większość osób, którzy znają to program Visual Studio, jednak istnieje kilka scenariuszy, których wyświetlanie w Projektancie przepływu pracy w aplikacji mogą być przydatne:  
  
- Monitorowanie aplikacji (umożliwiając użytkownikowi końcowemu wizualizować proces, a także dane czasu wykonywania o procesie, takie jak aktualnie aktywnego stanu, łączny czas wykonywania danych lub inne informacje dotyczące wystąpienia przepływu pracy).  
  
- Aplikacje, które umożliwiają użytkownikowi dostosowywanie procesu z ograniczonym zestawem działań.  
  
 Aby zapewnić obsługę tych typów aplikacji, projektanta przepływu pracy jest dostarczany w .NET Framework i mogą być hostowane w aplikacji WPF lub w aplikacji formularzy WinForms przy użyciu odpowiedniej platformy WPF kod hostingu. W tym przykładzie przedstawiono:  
  
- Rehostowanie projektanta programu WF.  
  
- Przy użyciu rehostowanym przybornika i właściwości siatki także.  
  
## <a name="rehosting-the-designer"></a>Rehostowanie projektanta  
 W tym przykładzie pokazano, jak utworzyć układ platformy WPF, projektanta, zawierać widoczne w następujących Układ tabelaryczny (kod przybornika pominięcia dotyczy miejsca). Należy pamiętać nazw obramowania, zawierające siatki projektanta i właściwości.  
  
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
  
 Następnie przykład tworzy projektanta i kojarzy podstawowym <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> przy użyciu odpowiedniego kontenera w interfejsie użytkownika. Istnieje kilka dodatkowych wierszy kodu w poniższym przykładzie że opiszemy je w niektórych wyjaśnienie. <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Wywołanie jest wymagane do skojarzenia Projektanci działań domyślny dla działania są dostarczane z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> jest wywoływana, aby przekazać przedmiotu WF do edycji. Na koniec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (podstawowy Kanwa) i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (siatki właściwości) są umieszczane na powierzchnię interfejsu użytkownika.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Korzystanie z przybornika rehostowanym  
 Ta próbka używa kontrolki przybornika rehostowanym deklaratywnie w XAML. Należy pamiętać, że w kodzie, jeden można przekazać typ, który ma <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktora.  
  
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
  
#### <a name="using-the-sample"></a>Przy użyciu przykładu  
  
1. Otwórz rozwiązanie DesignerRehosting.sln w programie Visual Studio 2010.  
  
2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
3. Aplikacja WPF rozpoczyna się od rehostowanym projektancie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`