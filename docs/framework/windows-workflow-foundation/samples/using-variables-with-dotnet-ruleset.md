---
title: Używanie zmiennych z reguł składników .NET Framework 3.5
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 64d47564076e19e152e30b6ab0cb3900ce53cfa1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512857"
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a><span data-ttu-id="2ce36-102">Używanie zmiennych z reguł składników .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="2ce36-102">Using Variables with a .NET Framework 3.5 Ruleset</span></span>
<span data-ttu-id="2ce36-103">Ten przykład przedstawia sposób tworzenia przepływu pracy, który używa <xref:System.Activities.Statements.Interop> działanie, aby zintegrować działanie niestandardowe napisane w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] używającej zasadach i regułach.</span><span class="sxs-lookup"><span data-stu-id="2ce36-103">This sample demonstrates how to create a workflow that uses the <xref:System.Activities.Statements.Interop> activity to integrate a custom activity written in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] that uses policy and rules.</span></span> <span data-ttu-id="2ce36-104">Przepływ pracy przekazuje dane do działania niestandardowego przez powiązanie zmienne udostępnianych przez działanie niestandardowe właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="2ce36-104">The workflow passes data to the custom activity by binding variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="sample-walkthrough"></a><span data-ttu-id="2ce36-105">Przewodnik po przykładzie</span><span class="sxs-lookup"><span data-stu-id="2ce36-105">Sample walkthrough</span></span>  
  
#### <a name="to-examine-travelrulelibrary"></a><span data-ttu-id="2ce36-106">Aby zbadać TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="2ce36-106">To examine TravelRuleLibrary</span></span>  
  
1.  <span data-ttu-id="2ce36-107">W programie Visual Studio Otwórz plik rozwiązania InteropWith35RuleSet.sln.</span><span class="sxs-lookup"><span data-stu-id="2ce36-107">Using Visual Studio, open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2ce36-108">Otwórz TravelRuleSet.cs w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2ce36-108">Open the TravelRuleSet.cs in the workflow designer.</span></span>  
  
     <span data-ttu-id="2ce36-109">Niestandardowe działania sekwencyjnego, który zawiera <xref:System.Workflow.Activities.PolicyActivity> jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="2ce36-109">A custom sequential activity that contains a <xref:System.Workflow.Activities.PolicyActivity> is displayed.</span></span>  
  
3.  <span data-ttu-id="2ce36-110">Kliknij dwukrotnie działanie zasad DiscountPolicy, aby sprawdzić zasady.</span><span class="sxs-lookup"><span data-stu-id="2ce36-110">Double-click the DiscountPolicy policy activity to examine the rules.</span></span>  
  
     <span data-ttu-id="2ce36-111">Edytor reguł pojawia się, aby wyświetlić zasady.</span><span class="sxs-lookup"><span data-stu-id="2ce36-111">The Rules editor pops up to show the rules.</span></span>  
  
4.  <span data-ttu-id="2ce36-112">Kliknij prawym przyciskiem myszy `DiscountPolicy` i wybierz **Wyświetl kod** opcję, aby sprawdzić kod obok kodu C# dla działania.</span><span class="sxs-lookup"><span data-stu-id="2ce36-112">Right click the `DiscountPolicy` and select the **View Code** option to examine the code beside C# code for the activity.</span></span>  
  
     <span data-ttu-id="2ce36-113">Sprawdź ustawienie właściwości zależności `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="2ce36-113">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="2ce36-114">Jest to równoważne argumentów [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2ce36-114">This is equivalent to arguments in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="2ce36-115">Aby uzyskać więcej informacji na temat argumentów, zobacz [zmienne i argumenty](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="2ce36-115">For more information about arguments, see [Variables and Arguments](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span></span>  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="2ce36-116">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="2ce36-116">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="2ce36-117">Jest to projekt sekwencyjnego przepływu pracy, który używa <xref:System.Activities.Statements.Interop> działania integracji z niestandardowego zestawu reguł utworzonych w `TravelRuleLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="2ce36-117">This is a sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom Rule set created in the `TravelRuleLibrary` project.</span></span> <span data-ttu-id="2ce36-118">Zmienne są tworzone na najwyższym poziomie <xref:System.Activities.Statements.Sequence> działania.</span><span class="sxs-lookup"><span data-stu-id="2ce36-118">Variables are created on the top level <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="2ce36-119"><xref:System.Activities.Statements.Interop> To działanie służy do integrowania z `TravelRuleSet` działania.</span><span class="sxs-lookup"><span data-stu-id="2ce36-119">The <xref:System.Activities.Statements.Interop> activity is used to integrate with the `TravelRuleSet` activity.</span></span> <span data-ttu-id="2ce36-120">Zmienne, które są zadeklarowane na <xref:System.Activities.Statements.Sequence> są używane do powiązania właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="2ce36-120">The variables that are declared on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="2ce36-121">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="2ce36-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="2ce36-122">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InteropWith35RuleSet.sln.</span><span class="sxs-lookup"><span data-stu-id="2ce36-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2ce36-123">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="2ce36-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2ce36-124">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="2ce36-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2ce36-125">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2ce36-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2ce36-126">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2ce36-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2ce36-127">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2ce36-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2ce36-128">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2ce36-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`