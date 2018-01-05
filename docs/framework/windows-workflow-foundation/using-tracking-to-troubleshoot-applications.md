---
title: "Do rozwiązywania problemów z aplikacjami za pomocą śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb8971c344ff24120b5f85dceb518b0944bd5feb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="6389d-102">Do rozwiązywania problemów z aplikacjami za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="6389d-102">Using Tracking to Troubleshoot Applications</span></span>
[!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="6389d-103">Umożliwia śledzenie informacji związanych z przepływu pracy, o podanie szczegółów do wykonywania [!INCLUDE[wf2](../../../includes/wf2-md.md)] aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="6389d-103"> enables you to track workflow-related information to give details into the execution of a [!INCLUDE[wf2](../../../includes/wf2-md.md)] application or service.</span></span> [!INCLUDE[wf2](../../../includes/wf2-md.md)]<span data-ttu-id="6389d-104">hosty mogą uzyskiwać do przechwytywania zdarzeń przepływu pracy podczas wykonywania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6389d-104"> hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="6389d-105">Jeśli przepływ pracy generuje błędów i wyjątków, możesz użyć [!INCLUDE[wf2](../../../includes/wf2-md.md)] Szczegóły śledzenia do rozwiązywania problemów z jego przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="6389d-105">If your workflow generates faults or exceptions, you can use the [!INCLUDE[wf2](../../../includes/wf2-md.md)] tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="6389d-106">Rozwiązywanie problemów z WF, używając WF śledzenia</span><span class="sxs-lookup"><span data-stu-id="6389d-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="6389d-107">Aby wykryć błędów w ramach przetwarzania [!INCLUDE[wf2](../../../includes/wf2-md.md)] działania, można włączyć śledzenie za pomocą profilu śledzenia, który odpytuje dla <xref:System.Activities.Tracking.ActivityStateRecord> o stanie Faulted.</span><span class="sxs-lookup"><span data-stu-id="6389d-107">To detect faults within the processing of a [!INCLUDE[wf2](../../../includes/wf2-md.md)] activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="6389d-108">Odpowiednie zapytanie jest określone w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6389d-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="6389d-109">Jeśli błąd jest propagowane i przetwarzanych w ramach obsługi błędów (takich jak <xref:System.Activities.Statements.TryCatch> działania) to mogą zostać wykryte przy użyciu <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="6389d-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="6389d-110"><xref:System.Activities.Tracking.FaultPropagationRecord> Wskazuje działania źródłowego usterki i nazwę programu obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="6389d-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="6389d-111"><xref:System.Activities.Tracking.FaultPropagationRecord> Zawiera szczegółowe informacje o błędzie w postaci stosu wyjątków dla błędu. Zapytanie, aby subskrybować <xref:System.Activities.Tracking.FaultPropagationRecord> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6389d-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="6389d-112">Jeśli błąd nie jest obsługiwana w ramach przepływu pracy, który powoduje nieobsługiwany wyjątek na wystąpienie przepływu pracy i wystąpienia przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="6389d-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="6389d-113">Aby poznać szczegóły nieobsługiwany wyjątek, profilu śledzenia należy zbadać rekord wystąpienia przepływu pracy z `state name="UnhandledException"` jak określono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6389d-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="6389d-114">W przypadku wystąpienia przepływu pracy napotkał nieobsługiwany wyjątek, <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> obiektu jest emitowany Jeśli [!INCLUDE[wf2](../../../includes/wf2-md.md)] włączył śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6389d-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if [!INCLUDE[wf2](../../../includes/wf2-md.md)] tracking has been enabled.</span></span>  
  
 <span data-ttu-id="6389d-115">Ten rekord śledzenia zawiera szczegółowe informacje o błędzie w formie stosu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6389d-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="6389d-116">Ma on szczegółowe informacje o źródle błędów (na przykład działanie), który wystąpił błąd i spowodowała nieobsługiwany wyjątek. Aby subskrybować zdarzenia błędów z [!INCLUDE[wf2](../../../includes/wf2-md.md)], Włącz śledzenie, dodając uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6389d-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a [!INCLUDE[wf2](../../../includes/wf2-md.md)], enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="6389d-117">Skonfiguruj tego profilu śledzenia, który odpytuje dla `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, i `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="6389d-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="6389d-118">Jeśli śledzenie jest włączone, za pomocą uczestnika śledzenia funkcji ETW, zdarzenia błędów są emitowane w sesji usługi ETW.</span><span class="sxs-lookup"><span data-stu-id="6389d-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="6389d-119">Zdarzenia można wyświetlić za pomocą Podglądu zdarzeń w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6389d-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="6389d-120">Znajdują się w węźle **aplikacji -> Podgląd zdarzeń i dzienników usług -> Microsoft -> Windows -> aplikacje serwera aplikacji** w kanale danych analitycznych.</span><span class="sxs-lookup"><span data-stu-id="6389d-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6389d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6389d-121">See Also</span></span>  
 [<span data-ttu-id="6389d-122">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="6389d-122">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="6389d-123">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="6389d-123">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
