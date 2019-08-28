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
# <a name="designer-rehosting"></a><span data-ttu-id="035b1-102">Rehostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="035b1-102">Designer Rehosting</span></span>
<span data-ttu-id="035b1-103">Rehostowanie projektanta jest typowym scenariuszem, który odnosi się do hostingu kanwy projektowania przepływu pracy w aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="035b1-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="035b1-104">Aplikacja hostingu większość osób zna program Visual Studio, jednak istnieje kilka scenariuszy, w których wyświetlanie projektanta przepływu pracy w aplikacji może być przydatne:</span><span class="sxs-lookup"><span data-stu-id="035b1-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="035b1-105">Monitorowanie aplikacji (umożliwienie użytkownikowi końcowemu wizualizacji procesu, a także danych środowiska uruchomieniowego dotyczących procesu, takich jak aktualnie aktywny stan, zagregowane dane czasu wykonywania lub inne informacje o wystąpieniu przepływu pracy).</span><span class="sxs-lookup"><span data-stu-id="035b1-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="035b1-106">Aplikacje, które umożliwiają użytkownikowi dostosowanie procesu przy użyciu ograniczonego zestawu działań.</span><span class="sxs-lookup"><span data-stu-id="035b1-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="035b1-107">Aby zapewnić obsługę tych typów aplikacji, Projektant przepływów pracy jest dostarczany wewnątrz .NET Framework i może być hostowany w aplikacji WPF lub w aplikacji WinForms z odpowiednim kodem hostingu WPF.</span><span class="sxs-lookup"><span data-stu-id="035b1-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="035b1-108">Ten przykład ilustruje:</span><span class="sxs-lookup"><span data-stu-id="035b1-108">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="035b1-109">Rehostowanie projektanta WF.</span><span class="sxs-lookup"><span data-stu-id="035b1-109">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="035b1-110">Również przy użyciu narzędzia Hostowanie i siatki właściwości.</span><span class="sxs-lookup"><span data-stu-id="035b1-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="035b1-111">Hostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="035b1-111">Rehosting the designer</span></span>  
 <span data-ttu-id="035b1-112">Ten przykład pokazuje, jak utworzyć układ WPF, aby zawierał projektanta, widoczny w poniższym układzie siatki (kod przybornika został pominięty w przypadku problemów z miejscem).</span><span class="sxs-lookup"><span data-stu-id="035b1-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="035b1-113">Zwróć uwagę na nazwy obramowań zawierające projektanta i siatkę właściwości.</span><span class="sxs-lookup"><span data-stu-id="035b1-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="035b1-114">Następnie przykład tworzy projektanta i kojarzy jego podstawową <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> z odpowiednim kontenerem w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="035b1-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="035b1-115">W poniższym przykładzie znajduje się kilka dodatkowych wierszy kodu, które stanowią objaśnienie niektórych wyjaśnień.</span><span class="sxs-lookup"><span data-stu-id="035b1-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="035b1-116"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Wywołanie jest wymagane do skojarzenia domyślnego projektanta działań dla działań dostarczonych z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="035b1-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="035b1-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>jest wywoływana, aby przekazać element WF do edycji.</span><span class="sxs-lookup"><span data-stu-id="035b1-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="035b1-118">Na koniec <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (główna Kanwa) i (siatka właściwości) są umieszczane na powierzchni interfejsu użytkownika. <xref:System.Activities.Presentation.WorkflowDesigner.View%2A></span><span class="sxs-lookup"><span data-stu-id="035b1-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="035b1-119">Korzystanie z przybornika przehostowanego</span><span class="sxs-lookup"><span data-stu-id="035b1-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="035b1-120">Ten przykład używa wbudowanej kontrolki przybornika w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="035b1-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="035b1-121">Należy zauważyć, że w kodzie, jeden może przekazać typ do <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="035b1-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="035b1-122">Korzystanie z przykładu</span><span class="sxs-lookup"><span data-stu-id="035b1-122">Using the sample</span></span>  
  
1. <span data-ttu-id="035b1-123">Otwórz rozwiązanie DesignerRehosting. sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="035b1-123">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="035b1-124">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="035b1-124">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="035b1-125">Aplikacja WPF zaczyna się od zahostowanego projektanta.</span><span class="sxs-lookup"><span data-stu-id="035b1-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="035b1-126">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="035b1-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="035b1-127">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="035b1-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="035b1-128">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="035b1-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="035b1-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="035b1-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
