---
title: Rekordy śledzenia
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: c9c0d7d8c29d89ab47957c271444740f5f2f9b7f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650942"
---
# <a name="tracking-records"></a>Rekordy śledzenia
Środowisko wykonawcze przepływów pracy został zinstrumentowany aby emitować rekordów śledzenia z wykonywania wystąpienia przepływu pracy.  
  
## <a name="tracking-records"></a>Rekordy śledzenia  
 W poniższej tabeli przedstawiono rekordów śledzenia emitowane przez środowisko wykonawcze przepływów pracy.  
  
|Rekord śledzenia|Opis|  
|---------------------|-----------------|  
|Rekordy cyklu życia przepływu pracy|Emitowane na różnych etapach cyklu życia wystąpienia przepływu pracy. Na przykład rekord jest emitowane, gdy przepływ pracy rozpoczyna się lub kończy.|  
|Rekordy cyklu życia aktywności|Szczegóły wykonania działania. Te rekordy wskazują stan działania przepływu pracy, takie jak harmonogramem działania, po ukończeniu działania lub w przypadku, gdy wystąpi błąd.|  
|Zakładki wznowienie rekordów|Emitowane przy każdym zakładki w ramach wystąpienie przepływu pracy zostanie wznowione.|  
|Niestandardowe rekordy śledzenia|Tworzenie przepływu pracy można utworzyć niestandardowe rekordy śledzenia i emitować je w ramach działań niestandardowych.|  
  
 Wszystkie rekordy dotyczące śledzenia emitowane przez środowisko uruchomieniowe programu WF pochodzi z klasy bazowej <xref:System.Activities.Tracking.TrackingRecord>, który zawiera wspólnego zestawu danych. Cykl życia prosty przepływ pracy umożliwia wyświetlenie rekordów śledzenia. Każdy rekord śledzenia zawiera szczegóły dotyczące zdarzenia śledzenia skojarzony, takie jak <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>, alertów oraz dodatkowe informacje specyficzne dla typu rekord śledzenia.  
  
 Następujące rodzaje <xref:System.Activities.Tracking.TrackingRecord> obiekty są emitowane przez środowisko wykonawcze przepływów pracy:  
  
- **WorkflowInstanceRecord** — to <xref:System.Activities.Tracking.TrackingRecord> opisuje cyklu życia wystąpienia przepływu pracy. Na przykład rekord jest emitowane przepływu pracy rozpoczyna się lub kończy, gdy zawiera stan wystąpienia przepływu pracy. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
- **WorkflowInstanceAbortedRecord** — to <xref:System.Activities.Tracking.TrackingRecord> są emitowane po przerywa wystąpienia przepływu pracy. Rekord zawiera powód wystąpienia przepływu pracy, Trwa przerywanie. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
- **WorkflowInstanceUnhandledExceptionRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowane, jeśli wyjątek występuje w wystąpieniu przepływu pracy i nie jest obsługiwany przez wszystkie działania. Rekord zawiera szczegóły wyjątku. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
- **WorkflowInstanceSuspendedRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowane zawsze wtedy, gdy wystąpienie przepływu pracy jest zawieszone. Rekord zawiera powód wystąpienia przepływu pracy jest zawieszone. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
- **WorkflowInstanceTerminatedRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowane zawsze wtedy, gdy wystąpienie przepływu pracy zostanie zakończony. Rekord zawiera powód wystąpienia przepływu pracy zostanie zakończone. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
- **ActivityStateRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowane, gdy wykonuje działania w przepływie pracy. Te informacje wskazują stan działania w ramach wystąpienie przepływu pracy. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
- **ActivityScheduledRecord** — to <xref:System.Activities.Tracking.TrackingRecord> są emitowane po działaniu planuje działanie podrzędne. Ten rekord zawiera szczegóły dotyczące działania nadrzędnego (Planowanie działań) i działania podrzędnego zaplanowane. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
- **FaultPropagationRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowane na każdy program obsługi, który patrzy na rekord, dopóki nie zostanie obsłużony. Służy do określenia ścieżki, którą awarii weszło w ramach wystąpienie przepływu pracy. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
- **CancelRequestedRecord** — to <xref:System.Activities.Tracking.TrackingRecord> jest emitowane zawsze wtedy, gdy próbuje anulować działanie podrzędne przez działanie. Ten rekord zawiera szczegóły dotyczące działania nadrzędnego i działania podrzędnego, który jest anulowane. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
- **BookmarkResumptionRecord** — to <xref:System.Activities.Tracking.TrackingRecord> śledzi wszystkie zakładki, która jest wznowione. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
- **CustomTrackingRecord** — to <xref:System.Activities.Tracking.TrackingRecord> zostanie utworzony i wyemitowane przez autora przepływu pracy, wewnątrz działania elementu pracy. Niestandardowe rekordy śledzenia można wypełnić przy użyciu danych maszynowych wraz z rekordów. Szczegóły dotyczące tego rekordu, można znaleźć w folderze <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Na przykład może być prosty <xref:System.Activities.Statements.Sequence> działania, który zawiera <xref:System.Activities.Statements.WriteLine> operacji śledzenia rekordów emitowane w następującej kolejności:  
  
1. <xref:System.Activities.Tracking.WorkflowInstanceRecord> Wskazuje, że przepływ pracy jest uruchamiany.  
  
2. <xref:System.Activities.Tracking.ActivityScheduledRecord> Wskazuje, czy działanie zostało zaplanowane. W tym przypadku jest <xref:System.Activities.Statements.Sequence> działania.  
  
3. <xref:System.Activities.Tracking.ActivityScheduledRecord> reprezentuje <xref:System.Activities.Statements.WriteLine> działania.  
  
4. Istnieją dwa <xref:System.Activities.Tracking.ActivityStateRecord> rekordy, które reprezentują dwa działania, kończenie pracy.  
  
5. <xref:System.Activities.Tracking.WorkflowInstanceRecord> Wskazuje, że przepływ pracy jest kończonych.  
  
## <a name="see-also"></a>Zobacz także

- [Windows Server AppFabric monitorowania](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=201275)
