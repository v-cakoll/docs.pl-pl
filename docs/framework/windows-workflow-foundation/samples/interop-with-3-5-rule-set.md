---
title: "Współdziałanie z zestawu reguł w wersji 3.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 854aeac936d3f911f2613c6e315ab81347f64a25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="interop-with-35-rule-set"></a><span data-ttu-id="cc9e9-102">Współdziałanie z zestawu reguł w wersji 3.5</span><span class="sxs-lookup"><span data-stu-id="cc9e9-102">Interop with 3.5 Rule Set</span></span>
<span data-ttu-id="cc9e9-103">W tym przykładzie przedstawiono użycie <xref:System.Activities.Statements.Interop> działania integracji z działań niestandardowych w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] przy użyciu <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` i zasady.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-103">This sample demonstrates the use of the <xref:System.Activities.Statements.Interop> activity to integrate with a custom activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] using <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` and rules.</span></span> <span data-ttu-id="cc9e9-104">Przekazuje dane do działania niestandardowego przez powiązanie [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] zmienne do właściwości zależności udostępnianych przez działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-104">It passes data to the custom activity by binding [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc9e9-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc9e9-105">Requirements</span></span>  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a><span data-ttu-id="cc9e9-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="cc9e9-106">Demonstrates</span></span>  
 <span data-ttu-id="cc9e9-107"><xref:System.Activities.Statements.Interop>działanie, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` działania w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] z właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="cc9e9-107"><xref:System.Activities.Statements.Interop> activity, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] with dependency properties</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="cc9e9-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cc9e9-108">Discussion</span></span>  
 <span data-ttu-id="cc9e9-109">W przykładzie pokazano jednego ze scenariuszy integracji dla integracji z [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] działania.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-109">The sample demonstrates one of the integration scenarios for integrating with a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] activity.</span></span> <span data-ttu-id="cc9e9-110">Ten przykład zawiera [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] działania niestandardowego, który wywołuje <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` działania.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-110">This sample includes a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] custom activity that invokes a <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity.</span></span>  
  
## <a name="travelrulelibrary"></a><span data-ttu-id="cc9e9-111">TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="cc9e9-111">TravelRuleLibrary</span></span>  
 <span data-ttu-id="cc9e9-112">Otwieranie TravelRuleSet.cs w Projektancie zawiera niestandardowe działanie sekwencyjne zawierający w następujący sposób działania zasad</span><span class="sxs-lookup"><span data-stu-id="cc9e9-112">Opening TravelRuleSet.cs in the designer shows a custom sequential activity that contains a Policy activity as follows</span></span>  
  
 <span data-ttu-id="cc9e9-113">![Działania Interop](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span><span class="sxs-lookup"><span data-stu-id="cc9e9-113">![Interop Activity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span></span>  
  
 <span data-ttu-id="cc9e9-114">Kliknij dwukrotnie **DiscountPolicy** działanie zasad do sprawdzenia zasad.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-114">Double-click the **DiscountPolicy** policy activity to examine the rules.</span></span> <span data-ttu-id="cc9e9-115">Aby wyświetlić zasady zostanie wyświetlony Edytor reguły.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-115">The Rules editor appears to show the rules.</span></span>  
  
 <span data-ttu-id="cc9e9-116">![Edytor zestawu reguł](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span><span class="sxs-lookup"><span data-stu-id="cc9e9-116">![Rule Set Editor](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span></span>  
  
 <span data-ttu-id="cc9e9-117">Kliknij prawym przyciskiem myszy **DiscountPolicy** działanie i wybierz **kod widoku** opcję do zbadania obok kodu C# kod, który łączy się z tego działania.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-117">Right-click the **DiscountPolicy** activity and select the **View Code** option to examine the code-beside C# code that goes with this activity.</span></span> <span data-ttu-id="cc9e9-118">Sprawdź ustawienie właściwości zależności `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-118">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="cc9e9-119">Jest to równoważne <xref:System.Activities.Argument> w [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc9e9-119">This is equivalent to an <xref:System.Activities.Argument> in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span>  
  
```  
public static DependencyProperty DiscountLevelProperty = DependencyProperty.Register("DiscountLevel", typeof(int), typeof(TravelRuleSet));  
  
[DescriptionAttribute("DiscountLevel")]  
[CategoryAttribute("DiscountLevel Category")]  
[BrowsableAttribute(true)]  
[DesignerSerializationVisibilityAttribute(DesignerSerializationVisibility.Visible)]  
public int DiscountLevel  
{  
   get  
   {  
return ((int)base.GetValue(TravelRuleSet.DiscountLevelProperty)));  
   }  
   set  
   {  
base.SetValue(TravelRuleSet.DiscountLevelProperty, value);  
   }  
}  
```  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="cc9e9-120">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="cc9e9-120">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="cc9e9-121">Jest to [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] projektu sekwencyjnego przepływu pracy, który używa <xref:System.Activities.Statements.Interop> działania integracji z zestawu utworzonego w projekcie TravelRuleLibrary reguł niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-121">This is a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom rule set created in the TravelRuleLibrary project.</span></span> <span data-ttu-id="cc9e9-122">Zmienne utworzone na najwyższym poziomie <xref:System.Activities.Statements.Sequence> w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-122">Variables are created on the top-level <xref:System.Activities.Statements.Sequence> as follows.</span></span>  
  
 <span data-ttu-id="cc9e9-123">![Zmienne](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span><span class="sxs-lookup"><span data-stu-id="cc9e9-123">![Variables](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span></span>  
  
 <span data-ttu-id="cc9e9-124">![Eksplorator rozwiązań](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span><span class="sxs-lookup"><span data-stu-id="cc9e9-124">![Solution Explorer](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span></span>  
  
 <span data-ttu-id="cc9e9-125">Ponadto <xref:System.Activities.Statements.Interop> to działanie służy do integracji z TravelRuleSet.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-125">Lastly, the <xref:System.Activities.Statements.Interop> activity is used to integrate with the TravelRuleSet.</span></span> <span data-ttu-id="cc9e9-126">Zmienne, które zostały zgłoszone wcześniej na <xref:System.Activities.Statements.Sequence> są używane w celu powiązania właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-126">The variables that were declared earlier on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
 <span data-ttu-id="cc9e9-127">![Typ działania](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span><span class="sxs-lookup"><span data-stu-id="cc9e9-127">![Activity Type](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span></span>  
  
 <span data-ttu-id="cc9e9-128">![Strzałka](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span><span class="sxs-lookup"><span data-stu-id="cc9e9-128">![Arrow](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span></span>  
  
 <span data-ttu-id="cc9e9-129">![Właściwości](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span><span class="sxs-lookup"><span data-stu-id="cc9e9-129">![Properties](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cc9e9-130">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cc9e9-131">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cc9e9-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cc9e9-132">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc9e9-133">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cc9e9-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
