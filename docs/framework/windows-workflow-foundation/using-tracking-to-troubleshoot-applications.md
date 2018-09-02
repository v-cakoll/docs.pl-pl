---
title: Używanie śledzenia do rozwiązywania problemów z aplikacjami
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: f991533b61705c8d0a1a8e71b632dd53f24dd979
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401280"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Używanie śledzenia do rozwiązywania problemów z aplikacjami
Windows Workflow Foundation (WF) umożliwia śledzenie informacji związanych z przepływu pracy, o podanie szczegółów do wykonywania aplikacji Windows Workflow Foundation lub usługi. Hosty programu Windows Workflow Foundation mają możliwość przechwytywania zdarzeń przepływu pracy podczas wykonywania wystąpienia przepływu pracy. Jeśli przepływ pracy generuje błędy lub wyjątki, można użyć programu Windows Workflow Foundation, Szczegóły śledzenia do rozwiązywania problemów z jego przetwarzania.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Rozwiązywanie problemów z WF przy użyciu programu WF śledzenia  
 Aby wykryć błędy w ramach przetwarzania działania programu Windows Workflow Foundation, można włączyć śledzenie za pomocą profilu śledzenia, który odpytuje dla <xref:System.Activities.Tracking.ActivityStateRecord> o stanie Faulted. Odnośnego zapytania jest określona w poniższym kodzie.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Jeśli błąd jest propagowana i przetwarzanych w ramach obsługi błędów (takie jak <xref:System.Activities.Statements.TryCatch> działania) to mogą zostać wykryte za pomocą <xref:System.Activities.Tracking.FaultPropagationRecord>. <xref:System.Activities.Tracking.FaultPropagationRecord> Wskazuje działanie źródła błędu i nazwę programu obsługi błędów. <xref:System.Activities.Tracking.FaultPropagationRecord> Zawiera szczegółowe informacje o błędzie w postaci stosu wyjątku błędu. Zapytanie, aby subskrybować <xref:System.Activities.Tracking.FaultPropagationRecord> przedstawiono w poniższym przykładzie.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Jeśli błąd nie jest obsługiwany w ramach przepływu pracy, który powoduje nieobsługiwany wyjątek w wystąpienie przepływu pracy i wystąpienia przepływu pracy zostało przerwane. Aby poznać szczegóły nieobsługiwany wyjątek, profilu śledzenia musi wykonać zapytanie rekord wystąpienia przepływu pracy przy użyciu `state name="UnhandledException"` określone w poniższym przykładzie.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Gdy wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> obiektu jest emitowane, jeśli włączono śledzenie Windows Workflow Foundation.  
  
 Ten rekord śledzenia zawiera szczegóły błędów w formie stosu wyjątków. Zawiera szczegółowe informacje o źródle błąd (na przykład działanie), który wystąpił błąd i spowodowała nieobsługiwany wyjątek. Subskrybowanie do zdarzeń błędów z Windows Workflow Foundation, należy włączyć śledzenie, dodając uczestnika śledzenia. Konfigurowanie tej uczestnik przy użyciu profilu śledzenia, który odpytuje dla `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, i `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Jeśli śledzenie jest włączone, za pomocą funkcji ETW śledzenia uczestnika, zdarzenia błędów są emitowane sesji funkcji ETW. Zdarzenia można przeglądać za pomocą Podglądu zdarzeń w Podglądzie zdarzeń. Ten znajduje się w węźle **Podgląd zdarzeń -> aplikacji i usług -> Microsoft -> Windows -> aplikacje serwera aplikacji** w kanału danych analitycznych.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Server AppFabric monitorowania](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=201275)
