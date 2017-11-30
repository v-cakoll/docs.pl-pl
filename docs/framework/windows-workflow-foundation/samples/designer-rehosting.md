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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 005d6f98a7341954801c9b98e9eefdb1f0391d6c
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="designer-rehosting"></a><span data-ttu-id="f1dfd-102">Projektant ReHosting</span><span class="sxs-lookup"><span data-stu-id="f1dfd-102">Designer ReHosting</span></span>
<span data-ttu-id="f1dfd-103">Rehosting projektanta jest typowym scenariuszem odnoszący się do hostingu obszaru projektu przepływu pracy wewnątrz aplikacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="f1dfd-104">Hostingu aplikacji, którą osoby większość zapoznali się z jest Visual Studio, jednak istnieje wiele scenariuszy, w którym przedstawiający projektanta przepływów pracy w aplikacji może być przydatna:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
-   <span data-ttu-id="f1dfd-105">Monitorowanie aplikacji (co pozwala użytkownikowi końcowemu zwizualizować proces, a także dane środowiska uruchomieniowego o procesie, takie jak stan aktywny, łączny czas wykonywania danych lub inne informacje dotyczące wystąpienia przepływu pracy).</span><span class="sxs-lookup"><span data-stu-id="f1dfd-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
-   <span data-ttu-id="f1dfd-106">Aplikacje, które umożliwiają użytkownikom dostosowanie procesu z ograniczonym zestawem działań.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="f1dfd-107">Do obsługi tych typów aplikacji, projektanta przepływów pracy jest dostarczany w programie .NET Framework i może być obsługiwany w aplikacji WPF lub w aplikacji WinForms z użyciem WPF odpowiedni kod hostowania.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="f1dfd-108">W tym przykładzie przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-108">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="f1dfd-109">Rehosting projektanta WF.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-109">Rehosting the WF designer.</span></span>  
  
-   <span data-ttu-id="f1dfd-110">Przy użyciu rehosted przybornika i właściwości siatki również.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="f1dfd-111">Rehosting projektanta</span><span class="sxs-lookup"><span data-stu-id="f1dfd-111">Rehosting the designer</span></span>  
 <span data-ttu-id="f1dfd-112">W tym przykładzie przedstawiono sposób tworzenia układu WPF zawiera projektanta, w następujących układ siatki (kod przybornika pominięcia dotyczy miejsca).</span><span class="sxs-lookup"><span data-stu-id="f1dfd-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="f1dfd-113">Należy pamiętać, nazewnictwa obramowań, zawierające siatki projektanta i właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
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
  
 <span data-ttu-id="f1dfd-114">Następnie tworzy projektanta próbki i kojarzy jego podstawowym <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> z odpowiedniego kontenera w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="f1dfd-115">Istnieje kilka dodatkowych wierszy kodu w poniższym przykładzie, które wymagają wyjaśnień.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="f1dfd-116"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> Wywołanie jest wymagane do skojarzenia z projektantami działań domyślny dla działania dostarczone z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1dfd-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="f1dfd-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>nazywa się do przekazania w elemencie WF do edycji.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="f1dfd-118">Na koniec <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (podstawowy kanwy) i <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (siatki właściwości) są umieszczane na powierzchnię interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
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
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="f1dfd-119">Korzystanie z przybornika rehosted</span><span class="sxs-lookup"><span data-stu-id="f1dfd-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="f1dfd-120">W przykładzie użyto kontroli przybornika rehosted deklaratywnie w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="f1dfd-121">Należy pamiętać, że w kodzie, co może przekazać typ do <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
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
  
#### <a name="using-the-sample"></a><span data-ttu-id="f1dfd-122">Przy użyciu próbki</span><span class="sxs-lookup"><span data-stu-id="f1dfd-122">Using the sample</span></span>  
  
1.  <span data-ttu-id="f1dfd-123">Otwórz rozwiązanie DesignerRehosting.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1dfd-123">Open the DesignerRehosting.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f1dfd-124">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-124">Press F5 to compile and run the application.</span></span>  
  
3.  <span data-ttu-id="f1dfd-125">Aplikacja WPF rozpoczyna się od rehosted projektanta.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1dfd-126">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1dfd-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f1dfd-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f1dfd-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1dfd-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`