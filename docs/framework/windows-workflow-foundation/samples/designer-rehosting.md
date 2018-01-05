---
title: Projektant ReHosting
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44577450bb81e255caf22f306dcd0276821d262c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="designer-rehosting"></a>Projektant ReHosting
Rehosting projektanta jest typowym scenariuszem odnoszący się do hostingu obszaru projektu przepływu pracy wewnątrz aplikacji niestandardowej. Hostingu aplikacji, którą osoby większość zapoznali się z jest Visual Studio, jednak istnieje wiele scenariuszy, w którym przedstawiający projektanta przepływów pracy w aplikacji może być przydatna:  
  
-   Monitorowanie aplikacji (co pozwala użytkownikowi końcowemu zwizualizować proces, a także dane środowiska uruchomieniowego o procesie, takie jak stan aktywny, łączny czas wykonywania danych lub inne informacje dotyczące wystąpienia przepływu pracy).  
  
-   Aplikacje, które umożliwiają użytkownikom dostosowanie procesu z ograniczonym zestawem działań.  
  
 Do obsługi tych typów aplikacji, projektanta przepływów pracy jest dostarczany w programie .NET Framework i może być obsługiwany w aplikacji WPF lub w aplikacji WinForms z użyciem WPF odpowiedni kod hostowania. W tym przykładzie przedstawiono:  
  
-   Rehosting projektanta WF.  
  
-   Przy użyciu rehosted przybornika i właściwości siatki również.  
  
## <a name="rehosting-the-designer"></a>Rehosting projektanta  
 W tym przykładzie przedstawiono sposób tworzenia układu WPF zawiera projektanta, w następujących układ siatki (kod przybornika pominięcia dotyczy miejsca). Należy pamiętać, nazewnictwa obramowań, zawierające siatki projektanta i właściwości.  
  
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
  
 Następnie tworzy projektanta próbki i kojarzy jego podstawowym <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> z odpowiedniego kontenera w interfejsie użytkownika. Istnieje kilka dodatkowych wierszy kodu w poniższym przykładzie, które wymagają wyjaśnień. <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Wywołanie jest wymagane do skojarzenia z projektantami działań domyślny dla działania dostarczone z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. <xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>nazywa się do przekazania w elemencie WF do edycji. Na koniec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (podstawowy kanwy) i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (siatki właściwości) są umieszczane na powierzchnię interfejsu użytkownika.  
  
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
  
## <a name="using-the-rehosted-toolbox"></a>Korzystanie z przybornika rehosted  
 W przykładzie użyto kontroli przybornika rehosted deklaratywnie w języku XAML. Należy pamiętać, że w kodzie, co może przekazać typ do <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktora.  
  
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
  
#### <a name="using-the-sample"></a>Przy użyciu próbki  
  
1.  Otwórz rozwiązanie DesignerRehosting.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
3.  Aplikacja WPF rozpoczyna się od rehosted projektanta.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`