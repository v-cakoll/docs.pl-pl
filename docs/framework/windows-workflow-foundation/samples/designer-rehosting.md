---
title: Rehostowanie projektanta
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 26878be2aec03f83c5ec0d65e415f75691601d0a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588668"
---
# <a name="designer-rehosting"></a><span data-ttu-id="85c54-102">Rehostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="85c54-102">Designer Rehosting</span></span>
<span data-ttu-id="85c54-103">Rehostowanie projektanta jest to typowy scenariusz, która odwołuje się do hostowania kanwę projektu przepływu pracy w aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="85c54-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="85c54-104">Aplikacji macierzystej, których większość osób, którzy znają to program Visual Studio, jednak istnieje kilka scenariuszy, których wyświetlanie w Projektancie przepływu pracy w aplikacji mogą być przydatne:</span><span class="sxs-lookup"><span data-stu-id="85c54-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="85c54-105">Monitorowanie aplikacji (umożliwiając użytkownikowi końcowemu wizualizować proces, a także dane czasu wykonywania o procesie, takie jak aktualnie aktywnego stanu, łączny czas wykonywania danych lub inne informacje dotyczące wystąpienia przepływu pracy).</span><span class="sxs-lookup"><span data-stu-id="85c54-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="85c54-106">Aplikacje, które umożliwiają użytkownikowi dostosowywanie procesu z ograniczonym zestawem działań.</span><span class="sxs-lookup"><span data-stu-id="85c54-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="85c54-107">Aby zapewnić obsługę tych typów aplikacji, projektanta przepływu pracy jest dostarczany w .NET Framework i mogą być hostowane w aplikacji WPF lub w aplikacji formularzy WinForms przy użyciu odpowiedniej platformy WPF kod hostingu.</span><span class="sxs-lookup"><span data-stu-id="85c54-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="85c54-108">W tym przykładzie przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="85c54-108">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="85c54-109">Rehostowanie projektanta programu WF.</span><span class="sxs-lookup"><span data-stu-id="85c54-109">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="85c54-110">Przy użyciu rehostowanym przybornika i właściwości siatki także.</span><span class="sxs-lookup"><span data-stu-id="85c54-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="85c54-111">Rehostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="85c54-111">Rehosting the designer</span></span>  
 <span data-ttu-id="85c54-112">W tym przykładzie pokazano, jak utworzyć układ platformy WPF, projektanta, zawierać widoczne w następujących Układ tabelaryczny (kod przybornika pominięcia dotyczy miejsca).</span><span class="sxs-lookup"><span data-stu-id="85c54-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="85c54-113">Należy pamiętać nazw obramowania, zawierające siatki projektanta i właściwości.</span><span class="sxs-lookup"><span data-stu-id="85c54-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="85c54-114">Następnie przykład tworzy projektanta i kojarzy podstawowym <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> przy użyciu odpowiedniego kontenera w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="85c54-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="85c54-115">Istnieje kilka dodatkowych wierszy kodu w poniższym przykładzie że opiszemy je w niektórych wyjaśnienie.</span><span class="sxs-lookup"><span data-stu-id="85c54-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="85c54-116"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Wywołanie jest wymagane do skojarzenia Projektanci działań domyślne działań dostarczane z programem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85c54-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="85c54-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> jest wywoływana, aby przekazać przedmiotu WF do edycji.</span><span class="sxs-lookup"><span data-stu-id="85c54-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="85c54-118">Na koniec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (podstawowy Kanwa) i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (siatki właściwości) są umieszczane na powierzchnię interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="85c54-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="85c54-119">Korzystanie z przybornika rehostowanym</span><span class="sxs-lookup"><span data-stu-id="85c54-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="85c54-120">Ta próbka używa kontrolki przybornika rehostowanym deklaratywnie w XAML.</span><span class="sxs-lookup"><span data-stu-id="85c54-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="85c54-121">Należy pamiętać, że w kodzie, jeden można przekazać typ, który ma <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="85c54-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="85c54-122">Przy użyciu przykładu</span><span class="sxs-lookup"><span data-stu-id="85c54-122">Using the sample</span></span>  
  
1. <span data-ttu-id="85c54-123">Otwórz rozwiązanie DesignerRehosting.sln w programie Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="85c54-123">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="85c54-124">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="85c54-124">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="85c54-125">Aplikacja WPF rozpoczyna się od rehostowanym projektancie.</span><span class="sxs-lookup"><span data-stu-id="85c54-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85c54-126">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="85c54-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="85c54-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="85c54-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="85c54-128">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="85c54-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="85c54-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="85c54-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
