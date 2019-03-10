---
title: Biblioteka działań
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: b701d382c25644181b23f3c0f0cd8e019b8d37d1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709847"
---
# <a name="activity-library"></a><span data-ttu-id="a36f0-102">Biblioteka działań</span><span class="sxs-lookup"><span data-stu-id="a36f0-102">Activity Library</span></span>
<span data-ttu-id="a36f0-103">Ta sekcja zawiera przykłady pokazujące, zaawansowanych niestandardowych działań w Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="a36f0-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a36f0-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a36f0-104">In This Section</span></span>

 [<span data-ttu-id="a36f0-105">Niestandardowe działanie SendMail</span><span class="sxs-lookup"><span data-stu-id="a36f0-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="a36f0-106">Pokazuje, jak utworzyć niestandardowe działanie, która pochodzi od klasy <xref:System.Activities.AsyncCodeActivity> do wysyłania wiadomości e-mail przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a36f0-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="a36f0-107">Działanie ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="a36f0-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="a36f0-108">Pokazuje, jak `ThrottleParallelForEach` działanie jest podobne do <xref:System.Activities.Statements.ParallelForEach%601> działania z jednym wyjątkiem że umożliwia ustawienie współczynnika współbieżności Aby ograniczyć liczbę jednoczesnych gałęzi do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a36f0-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="a36f0-109">Działania dostępu do bazy danych</span><span class="sxs-lookup"><span data-stu-id="a36f0-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="a36f0-110">Pokazuje, jak utworzyć działania, które umożliwiają uzyskiwanie dostępu do bazy danych do pobierania lub modyfikowanie informacji i użycia [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) dostęp do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a36f0-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
 [<span data-ttu-id="a36f0-111">Działanie zasad zewnętrznych w programie .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="a36f0-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="a36f0-112">Pokazuje, jak działanie ExternalizedPolicy4 zezwala na wykonywanie istniejącej Windows Workflow Foundation w [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> obiektów w programie Windows Workflow Foundation w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) bezpośrednio za pomocą aparatu reguł to znaczy wydane w wersji 3.5 WF.</span><span class="sxs-lookup"><span data-stu-id="a36f0-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span> 
  
 [<span data-ttu-id="a36f0-113">Nieogólne działanie ForEach</span><span class="sxs-lookup"><span data-stu-id="a36f0-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="a36f0-114">Pokazuje, jak utworzyć wersję inną niż ogólna <xref:System.Activities.Statements.ForEach%601> działania.</span><span class="sxs-lookup"><span data-stu-id="a36f0-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="a36f0-115">Nieogólne działanie ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="a36f0-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="a36f0-116">Pokazuje, jak utworzyć wersję inną niż ogólna <xref:System.Activities.Statements.ParallelForEach%601> działania.</span><span class="sxs-lookup"><span data-stu-id="a36f0-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="a36f0-117">Działanie GetWorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="a36f0-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="a36f0-118">Pokazuje, jak użyć niestandardowego działania, `GetWorkflowInstanceId`, aby zwrócić identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a36f0-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
