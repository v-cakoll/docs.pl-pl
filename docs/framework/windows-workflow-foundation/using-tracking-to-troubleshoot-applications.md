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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02c6d346c6ebea27148c11f5f033f74dfb556e44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Do rozwiązywania problemów z aplikacjami za pomocą śledzenia
[!INCLUDE[wf](../../../includes/wf-md.md)]Umożliwia śledzenie informacji związanych z przepływu pracy, o podanie szczegółów do wykonywania [!INCLUDE[wf2](../../../includes/wf2-md.md)] aplikacji lub usługi. [!INCLUDE[wf2](../../../includes/wf2-md.md)]hosty mogą uzyskiwać do przechwytywania zdarzeń przepływu pracy podczas wykonywania wystąpienia przepływu pracy. Jeśli przepływ pracy generuje błędów i wyjątków, możesz użyć [!INCLUDE[wf2](../../../includes/wf2-md.md)] Szczegóły śledzenia do rozwiązywania problemów z jego przetwarzanie.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Rozwiązywanie problemów z WF, używając WF śledzenia  
 Aby wykryć błędów w ramach przetwarzania [!INCLUDE[wf2](../../../includes/wf2-md.md)] działania, można włączyć śledzenie za pomocą profilu śledzenia, który odpytuje dla <xref:System.Activities.Tracking.ActivityStateRecord> o stanie Faulted. Odpowiednie zapytanie jest określone w poniższym kodzie.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Jeśli błąd jest propagowane i przetwarzanych w ramach obsługi błędów (takich jak <xref:System.Activities.Statements.TryCatch> działania) to mogą zostać wykryte przy użyciu <xref:System.Activities.Tracking.FaultPropagationRecord>. <xref:System.Activities.Tracking.FaultPropagationRecord> Wskazuje działania źródłowego usterki i nazwę programu obsługi błędów. <xref:System.Activities.Tracking.FaultPropagationRecord> Zawiera szczegółowe informacje o błędzie w postaci stosu wyjątków dla błędu. Zapytanie, aby subskrybować <xref:System.Activities.Tracking.FaultPropagationRecord> przedstawiono w poniższym przykładzie.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Jeśli błąd nie jest obsługiwana w ramach przepływu pracy, który powoduje nieobsługiwany wyjątek na wystąpienie przepływu pracy i wystąpienia przepływu pracy zostało przerwane. Aby poznać szczegóły nieobsługiwany wyjątek, profilu śledzenia należy zbadać rekord wystąpienia przepływu pracy z `state name="UnhandledException"` jak określono w poniższym przykładzie.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 W przypadku wystąpienia przepływu pracy napotkał nieobsługiwany wyjątek, <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> obiektu jest emitowany Jeśli [!INCLUDE[wf2](../../../includes/wf2-md.md)] włączył śledzenia.  
  
 Ten rekord śledzenia zawiera szczegółowe informacje o błędzie w formie stosu wyjątku. Ma on szczegółowe informacje o źródle błędów (na przykład działanie), który wystąpił błąd i spowodowała nieobsługiwany wyjątek. Aby subskrybować zdarzenia błędów z [!INCLUDE[wf2](../../../includes/wf2-md.md)], Włącz śledzenie, dodając uczestnika śledzenia. Skonfiguruj tego profilu śledzenia, który odpytuje dla `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, i `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Jeśli śledzenie jest włączone, za pomocą uczestnika śledzenia funkcji ETW, zdarzenia błędów są emitowane w sesji usługi ETW. Zdarzenia można wyświetlić za pomocą Podglądu zdarzeń w Podglądzie zdarzeń. Znajdują się w węźle **aplikacji -> Podgląd zdarzeń i dzienników usług -> Microsoft -> Windows -> aplikacje serwera aplikacji** w kanale danych analitycznych.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
