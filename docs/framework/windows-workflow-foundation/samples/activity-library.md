---
title: Biblioteka działań
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142904"
---
# <a name="activity-library"></a><span data-ttu-id="00b51-102">Biblioteka działań</span><span class="sxs-lookup"><span data-stu-id="00b51-102">Activity Library</span></span>
<span data-ttu-id="00b51-103">Ta sekcja zawiera przykłady, które pokazują zaawansowane działania niestandardowe w programie Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="00b51-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00b51-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="00b51-104">In This Section</span></span>

 [<span data-ttu-id="00b51-105">Niestandardowe działanie SendMail</span><span class="sxs-lookup"><span data-stu-id="00b51-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="00b51-106">Pokazuje, jak utworzyć działanie niestandardowe, <xref:System.Activities.AsyncCodeActivity> które pochodzi z wysyłania poczty przy użyciu protokołu SMTP do użycia w aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="00b51-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="00b51-107">Działanie ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="00b51-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="00b51-108">Pokazuje, jak `ThrottleParallelForEach` działanie jest <xref:System.Activities.Statements.ParallelForEach%601> podobne do działania z jednym wyjątkiem, który umożliwia ustawienie współczynnik współbieżności, aby ograniczyć liczbę równoczesnych gałęzi do wykonania.</span><span class="sxs-lookup"><span data-stu-id="00b51-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="00b51-109">Działania dostępu do bazy danych</span><span class="sxs-lookup"><span data-stu-id="00b51-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="00b51-110">Pokazuje, jak tworzyć działania, które umożliwiają dostęp do baz danych do pobierania lub modyfikowania informacji i używać [ADO.NET](../../data/adonet/index.md) dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="00b51-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="00b51-111">Działanie zasad zewnętrznych w programie .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="00b51-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="00b51-112">Pokazuje, jak działanie ExternalizedPolicy4 umożliwia wykonywanie istniejących fundacji przepływu pracy systemu Windows w obiektach .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> w programie Windows Workflow Foundation w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] programie (WF 4.5) bezpośrednio przy użyciu aparatu reguł dostarczanych w 3.5 WF.</span><span class="sxs-lookup"><span data-stu-id="00b51-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="00b51-113">Nieogólne działanie ForEach</span><span class="sxs-lookup"><span data-stu-id="00b51-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="00b51-114">Pokazuje, jak utworzyć nierodową wersję <xref:System.Activities.Statements.ForEach%601> działania.</span><span class="sxs-lookup"><span data-stu-id="00b51-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="00b51-115">Nieogólne działanie ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="00b51-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="00b51-116">Pokazuje, jak utworzyć nierodową wersję <xref:System.Activities.Statements.ParallelForEach%601> działania.</span><span class="sxs-lookup"><span data-stu-id="00b51-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="00b51-117">Działanie GetWorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="00b51-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="00b51-118">Pokazuje, jak używać działania `GetWorkflowInstanceId`niestandardowego, aby zwrócić identyfikator wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="00b51-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
