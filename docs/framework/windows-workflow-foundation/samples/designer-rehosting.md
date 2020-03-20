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
# <a name="designer-rehosting"></a><span data-ttu-id="d8a22-102">Rehostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="d8a22-102">Designer Rehosting</span></span>
<span data-ttu-id="d8a22-103">Ponowne hostowanie projektanta jest typowym scenariuszem, który odnosi się do hostowania kanwy projektu przepływu pracy wewnątrz aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="d8a22-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="d8a22-104">Aplikacja hostingowa, z której większość osób jest zaznajomiona z programem Visual Studio, jednak istnieje wiele scenariuszy, w których wyświetlanie projektanta przepływu pracy w aplikacji może być przydatne:</span><span class="sxs-lookup"><span data-stu-id="d8a22-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="d8a22-105">Monitorowanie aplikacji (umożliwiając użytkownikowi końcowemu wizualizowanie procesu, a także dane środowiska wykonawczego o procesie, takie jak aktualnie aktywny stan, zagregowane dane czasu wykonywania lub inne informacje o wystąpieniu przepływu pracy).</span><span class="sxs-lookup"><span data-stu-id="d8a22-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="d8a22-106">Aplikacje, które umożliwiają użytkownikowi dostosowanie procesu za pomocą ograniczonego zestawu działań.</span><span class="sxs-lookup"><span data-stu-id="d8a22-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="d8a22-107">Do obsługi tego typu aplikacji, projektant przepływu pracy jest dostarczany wewnątrz .NET Framework i może być obsługiwany wewnątrz aplikacji WPF lub w aplikacji WinForms z odpowiednim kodem hostingu WPF.</span><span class="sxs-lookup"><span data-stu-id="d8a22-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="d8a22-108">W tym przykładzie pokazano:</span><span class="sxs-lookup"><span data-stu-id="d8a22-108">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="d8a22-109">Ponowne hostowanie projektanta WF.</span><span class="sxs-lookup"><span data-stu-id="d8a22-109">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="d8a22-110">Za pomocą rehosted przybornik i siatki właściwości, jak również.</span><span class="sxs-lookup"><span data-stu-id="d8a22-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="d8a22-111">Ponowne hostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="d8a22-111">Rehosting the designer</span></span>  
 <span data-ttu-id="d8a22-112">W tym przykładzie pokazano, jak utworzyć układ WPF zawierają projektanta, widoczne w następującym układzie siatki (kod przybornika pominięte dla kwestii miejsca).</span><span class="sxs-lookup"><span data-stu-id="d8a22-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="d8a22-113">Zwróć uwagę na nazewnictwo obramowań, które zawierają siatkę projektanta i właściwości.</span><span class="sxs-lookup"><span data-stu-id="d8a22-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="d8a22-114">Następnie przykład tworzy projektanta i kojarzy jego podstawowy <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> z odpowiednim kontenerem w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d8a22-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="d8a22-115">Istnieje kilka dodatkowych wierszy kodu w poniższym przykładzie, które zasługują na pewne wyjaśnienie.</span><span class="sxs-lookup"><span data-stu-id="d8a22-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="d8a22-116">Wywołanie <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> jest wymagane do skojarzenia domyślnych projektantów działań dla działań dostarczanych z programem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8a22-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="d8a22-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>jest wywoływana do przekazania w elemencie WF do edycji.</span><span class="sxs-lookup"><span data-stu-id="d8a22-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="d8a22-118">Na koniec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (podstawowa kanwa) i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (siatka właściwości) są umieszczane na powierzchni interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d8a22-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="d8a22-119">Korzystanie z przybornika hostowanego ponownie</span><span class="sxs-lookup"><span data-stu-id="d8a22-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="d8a22-120">W tym przykładzie użyto kontroli zestawu narzędzi rehosted deklaratywnie w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="d8a22-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="d8a22-121">Należy zauważyć, że w kodzie <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> można przekazać typ do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d8a22-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="d8a22-122">Korzystanie z próbki</span><span class="sxs-lookup"><span data-stu-id="d8a22-122">Using the sample</span></span>  
  
1. <span data-ttu-id="d8a22-123">Otwórz rozwiązanie DesignerRehosting.sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="d8a22-123">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="d8a22-124">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="d8a22-124">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="d8a22-125">Aplikacja WPF rozpoczyna się od projektanta rehosted.</span><span class="sxs-lookup"><span data-stu-id="d8a22-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d8a22-126">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d8a22-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d8a22-127">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="d8a22-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d8a22-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d8a22-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d8a22-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d8a22-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
