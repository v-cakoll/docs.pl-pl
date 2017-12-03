---
title: "Śledzenie rekordów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 764253f24f75b4311f181671c7dc85677df701ff
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="tracking-records"></a>Śledzenie rekordów
Środowiska uruchomieniowego przepływu pracy jest instrumentowany na emitowanie rekordów śledzenia wykonać wykonywania wystąpienia przepływu pracy.  
  
## <a name="tracking-records"></a>Śledzenie rekordów  
 W poniższej tabeli przedstawiono rekordy śledzenia emitowane środowiska uruchomieniowego przepływu pracy.  
  
|Rekord śledzenia|Opis|  
|---------------------|-----------------|  
|Rejestruje cyklu przepływu pracy|Emitowane różnych etapach cyklu życia wystąpienia przepływu pracy. Na przykład rekord jest emitowany podczas uruchamiania przepływu pracy, lub zakończeniu.|  
|Rekordy cykl życia|Szczegóły wykonywania działania. Te rekordy wskazują stan działania przepływu pracy, takie jak w przypadku zaplanowanego działania, po ukończeniu działania lub gdy wystąpi błąd.|  
|Rejestruje wznowienie zakładki|Emitowane zawsze, gdy zostanie wznowione zakładki w ramach wystąpienia przepływu pracy.|  
|Śledzenie niestandardowych rekordów|Autor przepływu pracy można utworzyć rekordy śledzenia niestandardowych i wysyłać je w ramach działania niestandardowego.|  
  
 Wszystkie rekordy dotyczące śledzenia emitowanych przez środowisko uruchomieniowe WF pochodzi od klasy podstawowej <xref:System.Activities.Tracking.TrackingRecord>, który zawiera wspólny zbiór danych. Cykl życia proste przepływu pracy bazie danych śledzenia. Każdy rekord śledzenia zawiera szczegóły dotyczące zdarzenia śledzenia skojarzony, takie jak <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>oraz dodatkowe informacje specyficzne dla typu rekordu śledzenia.  
  
 Następujące typy <xref:System.Activities.Tracking.TrackingRecord> obiekty są emitowane przez środowisko wykonawcze przepływu pracy:  
  
-   **WorkflowInstanceRecord** — to <xref:System.Activities.Tracking.TrackingRecord> opisuje cyklu życia wystąpienia przepływu pracy. Na przykład rekord jest emitowany, kiedy przepływ pracy rozpoczyna się lub kończy pracę i zawiera stan wystąpienia przepływu pracy. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
-   **WorkflowInstanceAbortedRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowany, jeśli przerwanie wystąpienia przepływu pracy. Rekord zawiera Przyczyna przerwanie wystąpienia przepływu pracy. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
-   **WorkflowInstanceUnhandledExceptionRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowany, jeśli wyjątek występuje w wystąpieniu przepływu pracy i nie jest obsługiwane przez wszystkie działania. Rekord zawiera szczegóły wyjątku. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
-   **WorkflowInstanceSuspendedRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowany zawsze, gdy wystąpienie przepływu pracy jest wstrzymana. Rekord zawiera przyczynę wystąpienia przepływu pracy wstrzymywane. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
-   **WorkflowInstanceTerminatedRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowany zawsze, gdy wystąpienie przepływu pracy zostało zakończone. Rekord zawiera przyczynę wystąpienia przepływu pracy przerywane. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
-   **ActivityStateRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowany podczas działania w przepływie pracy. Te rekordy wskazują stan działania w ramach wystąpienia przepływu pracy. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
-   **ActivityScheduledRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowany podczas działania planuje działania podrzędnego. Ten rekord zawiera szczegóły dla działania nadrzędnego (Planowanie działania) i działania podrzędnego zaplanowane. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
-   **FaultPropagationRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowany dla każdego obsługi, która analizuje rekordu, dopóki nie jest obsługiwane. Służy do oznaczania ścieżkę, którą błąd trwało w wystąpieniu przepływu pracy. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
-   **CancelRequestedRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowany zawsze, gdy próbuje anulować działanie podrzędne działania. Ten rekord zawiera szczegóły dla działania nadrzędnego i działanie podrzędne, która została anulowana. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
-   **BookmarkResumptionRecord** — to <xref:System.Activities.Tracking.TrackingRecord> śledzi wszystkie zakładki, która zostanie wznowione pomyślnie. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
-   **CustomTrackingRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest tworzony i emitowane przez autora przepływu pracy w ramach działania niestandardowego przepływu pracy. Śledzenie rekordów niestandardowe można wypełniać za pomocą danych, aby emitować wraz z rekordów. Szczegóły tego rekordu można znaleźć w folderze <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Na przykład może być prosty <xref:System.Activities.Statements.Sequence> działania, który zawiera <xref:System.Activities.Statements.WriteLine> operacji ze śledzeniem rekordów emitowanych w następującej kolejności:  
  
1.  <xref:System.Activities.Tracking.WorkflowInstanceRecord>Wskazuje, że trwa uruchamianie przepływu pracy.  
  
2.  <xref:System.Activities.Tracking.ActivityScheduledRecord>Wskazuje, czy działanie zostało zaplanowane. W tym przypadku jest <xref:System.Activities.Statements.Sequence> działania.  
  
3.  <xref:System.Activities.Tracking.ActivityScheduledRecord>reprezentuje <xref:System.Activities.Statements.WriteLine> działania.  
  
4.  Istnieją dwa <xref:System.Activities.Tracking.ActivityStateRecord> rekordów, które reprezentują dwa działania, kończenie.  
  
5.  <xref:System.Activities.Tracking.WorkflowInstanceRecord>Wskazuje, że przepływ pracy jest kończonych.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
