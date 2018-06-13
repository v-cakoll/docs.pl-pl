---
title: Do rozwiązywania problemów z aplikacjami za pomocą śledzenia
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: ee9aaaae80f213f026a222ac1754ae8b4fdf2d37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517046"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="b6177-102">Do rozwiązywania problemów z aplikacjami za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="b6177-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="b6177-103">Windows Workflow Foundation (WF) umożliwia śledzenie informacji związanych z przepływu pracy, aby podać szczegóły do wykonywania programu Windows Workflow Foundation aplikacji lub usługi.</span><span class="sxs-lookup"><span data-stu-id="b6177-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="b6177-104">Do przechwytywania zdarzeń przepływu pracy podczas wykonywania wystąpienia przepływu pracy mogą hostów Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="b6177-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="b6177-105">Jeśli przepływ pracy generuje błędów i wyjątków, można użyć programu Windows Workflow Foundation Szczegóły śledzenia do rozwiązywania problemów z jego przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="b6177-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="b6177-106">Rozwiązywanie problemów z WF, używając WF śledzenia</span><span class="sxs-lookup"><span data-stu-id="b6177-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="b6177-107">Aby wykrywać błędy w ramach przetwarzania działania Windows Workflow Foundation, można włączyć śledzenie za pomocą profilu śledzenia, który odpytuje dla <xref:System.Activities.Tracking.ActivityStateRecord> o stanie Faulted.</span><span class="sxs-lookup"><span data-stu-id="b6177-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="b6177-108">Odpowiednie zapytanie jest określone w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b6177-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="b6177-109">Jeśli błąd jest propagowane i przetwarzanych w ramach obsługi błędów (takich jak <xref:System.Activities.Statements.TryCatch> działania) to mogą zostać wykryte przy użyciu <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="b6177-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="b6177-110"><xref:System.Activities.Tracking.FaultPropagationRecord> Wskazuje działania źródłowego usterki i nazwę programu obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="b6177-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="b6177-111"><xref:System.Activities.Tracking.FaultPropagationRecord> Zawiera szczegółowe informacje o błędzie w postaci stosu wyjątków dla błędu. Zapytanie, aby subskrybować <xref:System.Activities.Tracking.FaultPropagationRecord> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b6177-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="b6177-112">Jeśli błąd nie jest obsługiwana w ramach przepływu pracy, który powoduje nieobsługiwany wyjątek na wystąpienie przepływu pracy i wystąpienia przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="b6177-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="b6177-113">Aby poznać szczegóły nieobsługiwany wyjątek, profilu śledzenia należy zbadać rekord wystąpienia przepływu pracy z `state name="UnhandledException"` jak określono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b6177-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="b6177-114">W przypadku wystąpienia przepływu pracy napotkał nieobsługiwany wyjątek, <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> obiektu jest emitowany, jeśli włączono śledzenie Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="b6177-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="b6177-115">Ten rekord śledzenia zawiera szczegółowe informacje o błędzie w formie stosu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b6177-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="b6177-116">Ma on szczegółowe informacje o źródle błędów (na przykład działanie), który wystąpił błąd i spowodowała nieobsługiwany wyjątek. Aby subskrybować zdarzenia błędów z programu Windows Workflow Foundation, należy włączyć śledzenie, dodając uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b6177-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="b6177-117">Skonfiguruj tego profilu śledzenia, który odpytuje dla `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, i `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="b6177-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="b6177-118">Jeśli śledzenie jest włączone, za pomocą uczestnika śledzenia funkcji ETW, zdarzenia błędów są emitowane w sesji usługi ETW.</span><span class="sxs-lookup"><span data-stu-id="b6177-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="b6177-119">Zdarzenia można wyświetlić za pomocą Podglądu zdarzeń w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b6177-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="b6177-120">Znajdują się w węźle **aplikacji -> Podgląd zdarzeń i dzienników usług -> Microsoft -> Windows -> aplikacje serwera aplikacji** w kanale danych analitycznych.</span><span class="sxs-lookup"><span data-stu-id="b6177-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6177-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6177-121">See Also</span></span>  
 [<span data-ttu-id="b6177-122">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="b6177-122">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="b6177-123">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="b6177-123">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
