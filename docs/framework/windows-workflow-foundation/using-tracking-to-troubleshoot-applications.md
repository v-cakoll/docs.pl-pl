---
title: Używanie śledzenia do rozwiązywania problemów z aplikacjami
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: 1ed95a26f682fcdb609b410251fdb3f8b647016a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734425"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="14264-102">Używanie śledzenia do rozwiązywania problemów z aplikacjami</span><span class="sxs-lookup"><span data-stu-id="14264-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="14264-103">Windows Workflow Foundation (WF) umożliwia śledzenie informacji związanych z przepływu pracy, o podanie szczegółów do wykonywania aplikacji Windows Workflow Foundation lub usługi.</span><span class="sxs-lookup"><span data-stu-id="14264-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="14264-104">Hosty programu Windows Workflow Foundation mają możliwość przechwytywania zdarzeń przepływu pracy podczas wykonywania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14264-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="14264-105">Jeśli przepływ pracy generuje błędy lub wyjątki, można użyć programu Windows Workflow Foundation, Szczegóły śledzenia do rozwiązywania problemów z jego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="14264-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="14264-106">Rozwiązywanie problemów z WF przy użyciu programu WF śledzenia</span><span class="sxs-lookup"><span data-stu-id="14264-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="14264-107">Aby wykryć błędy w ramach przetwarzania działania programu Windows Workflow Foundation, można włączyć śledzenie za pomocą profilu śledzenia, który odpytuje dla <xref:System.Activities.Tracking.ActivityStateRecord> o stanie Faulted.</span><span class="sxs-lookup"><span data-stu-id="14264-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="14264-108">Odnośnego zapytania jest określona w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="14264-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="14264-109">Jeśli błąd jest propagowana i przetwarzanych w ramach obsługi błędów (takie jak <xref:System.Activities.Statements.TryCatch> działania) to mogą zostać wykryte za pomocą <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="14264-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="14264-110"><xref:System.Activities.Tracking.FaultPropagationRecord> Wskazuje działanie źródła błędu i nazwę programu obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="14264-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="14264-111"><xref:System.Activities.Tracking.FaultPropagationRecord> Zawiera szczegółowe informacje o błędzie w postaci stosu wyjątku błędu. Zapytanie, aby subskrybować <xref:System.Activities.Tracking.FaultPropagationRecord> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="14264-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="14264-112">Jeśli błąd nie jest obsługiwany w ramach przepływu pracy, który powoduje nieobsługiwany wyjątek w wystąpienie przepływu pracy i wystąpienia przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="14264-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="14264-113">Aby poznać szczegóły nieobsługiwany wyjątek, profilu śledzenia musi wykonać zapytanie rekord wystąpienia przepływu pracy przy użyciu `state name="UnhandledException"` określone w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="14264-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="14264-114">Gdy wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> obiektu jest emitowane, jeśli włączono śledzenie Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="14264-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="14264-115">Ten rekord śledzenia zawiera szczegóły błędów w formie stosu wyjątków.</span><span class="sxs-lookup"><span data-stu-id="14264-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="14264-116">Zawiera szczegółowe informacje o źródle błąd (na przykład działanie), który wystąpił błąd i spowodowała nieobsługiwany wyjątek. Subskrybowanie do zdarzeń błędów z Windows Workflow Foundation, należy włączyć śledzenie, dodając uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="14264-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="14264-117">Konfigurowanie tej uczestnik przy użyciu profilu śledzenia, który odpytuje dla `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, i `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="14264-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="14264-118">Jeśli śledzenie jest włączone, za pomocą funkcji ETW śledzenia uczestnika, zdarzenia błędów są emitowane sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="14264-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="14264-119">Zdarzenia można przeglądać za pomocą Podglądu zdarzeń w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="14264-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="14264-120">Ten znajduje się w węźle **Podgląd zdarzeń -> aplikacji i usług -> Microsoft -> Windows -> aplikacje serwera aplikacji** w kanału danych analitycznych.</span><span class="sxs-lookup"><span data-stu-id="14264-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14264-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14264-121">See also</span></span>
- [<span data-ttu-id="14264-122">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="14264-122">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="14264-123">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="14264-123">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
