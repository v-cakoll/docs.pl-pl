---
title: Dokumentacja zdarzeń śledzenia
ms.date: 03/30/2017
ms.assetid: c1c1ee87-f80a-449b-acd0-50d81eef116e
ms.openlocfilehash: 5b3bba83b3c6c7ab27c9470213b7675f7e107c7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699880"
---
# <a name="tracking-events-reference"></a>Dokumentacja zdarzeń śledzenia
Podczas wykonywania przepływu pracy w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] wywołuje zdarzenia śledzenia, kiedy przesuwa się on za pośrednictwem różnych etapów w okresie swojego istnienia. Host może subskrybować te zdarzenia i aktualizować stan postęp przepływu pracy jego okres istnienia. Zdarzenia śledzenia, zgłaszane są omówione w tej sekcji.  
  
## <a name="event-reference"></a>Odwołanie do zdarzenia  
  
|Identyfikator zdarzenia|Poziom zdarzenia|Komunikat zdarzenia|słowa kluczowe|  
|--------------|-----------------|-------------------|--------------|  
|[100 — WorkflowInstanceRecord](100-workflowinstancerecord.md)|Informacje|TrackRecord = WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, stan = %5, adnotacje = %6, ProfileName = %7|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[101 — WorkflowInstanceUnhandledExceptionRecord](101-workflowinstanceunhandledexceptionrecord.md)|Błąd|TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, identyfikator = %6, SourceInstanceId = %7, SourceTypeName = %8, wyjątek = %9, adnotacje = % 10, ProfileName = % 11|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[102 — WorkflowInstanceAbortedRecord](102-workflowinstanceabortedrecord.md)|Ostrzeżenie|TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[103 — ActivityStateRecord](103-activitystaterecord.md)|Informacje|TrackRecord = ActivityStateRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, stan = %4, Nazwa = %5, identyfikator działania = %6, ActivityInstanceId = %7, ActivityTypeName = %8, argumenty = %9, zmienne = % 10, adnotacje = % 11, ProfileName = % 12|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[104 — ActivityScheduledRecord](104-activityscheduledrecord.md)|Informacje|TrackRecord = ActivityScheduledRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, identyfikator działania = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10 ChildActivityTypeName = % 11, adnotacje = ProfileName 12, % = % 13|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[105 — FaultPropagationRecord](105-faultpropagationrecord.md)|Ostrzeżenie|TrackRecord = FaultPropagationRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName = %7, FaultHandlerActivityName = %8, FaultHandlerActivityId = %9, FaultHandlerActivityInstanceId = % 10, FaultHandlerActivityTypeName = % 11, błąd = 12, IsFaultSource % = % 13, adnotacje = % 14, ProfileName = % 15|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[106 — CancelRequestRecord](106-cancelrequestrecord.md)|Informacje|TrackRecord = CancelRequestedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, identyfikator działania = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10 ChildActivityTypeName = % 11, adnotacje = ProfileName 12, % = % 13|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[107 — BookmarkResumptionRecord](107-bookmarkresumptionrecord.md)|Informacje|TrackRecord = BookmarkResumptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, SubInstanceID = %5, OwnerActivityName = %6, OwnerActivityId = %7, OwnerActivityInstanceId = %8, OwnerActivityTypeName = %9, adnotacje = % 10, ProfileName = % 11|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[108 — CustomTrackingRecordInfo](108-customtrackingrecordinfo.md)|Informacje|TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, ActivityName = %5, identyfikator działania = %6, ActivityInstanceId = %7, ActivityTypeName = %8, dane = %9, adnotacje = % 10, ProfileName = % 11|UserEvents EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[110 — CustomTrackingRecordWarning](110-customtrackingrecordwarning.md)|Ostrzeżenie|TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, ActivityName = %5, identyfikator działania = %6, ActivityInstanceId = %7, ActivityTypeName = %8, dane = %9, adnotacje = % 10, ProfileName = % 11|UserEvents EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[111 — CustomTrackingRecordError](111-customtrackingrecorderror.md)|Błąd|TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, ActivityName = %5, identyfikator działania = %6, ActivityInstanceId = %7, ActivityTypeName = %8, dane = %9, adnotacje = % 10, ProfileName = % 11|UserEvents EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[112 — WorkflowInstanceSuspendedRecord](112-workflowinstancesuspendedrecord.md)|Informacje|TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[113 — WorkflowInstanceTerminatedRecord](113-workflowinstanceterminatedrecord.md)|Błąd|TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|[114 — WorkflowInstanceRecordWithId](114-workflowinstancerecordwithid.md)|Informacje|TrackRecord = WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, stan = %5, adnotacje = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[115 — WorkflowInstanceAbortedRecordWithId](115-workflowinstanceabortedrecordwithid.md)|Ostrzeżenie|TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, przyczyna = %5, adnotacje = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[116 — WorkflowInstanceSuspendedRecordWithId](116-workflowinstancesuspendedrecordwithid.md)|Informacje|TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, przyczyna = %5, adnotacje = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[117 — WorkflowInstanceTerminatedRecordWithId](117-workflowinstanceterminatedrecordwithid.md)|Błąd|TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, przyczyna = %5, adnotacje = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[118 — WorkflowInstanceUnhandledExceptionRecordWithId](118-workflowinstanceunhandledexceptionrecordwithid.md)|Błąd|TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, identyfikator = %6, SourceInstanceId = %7, SourceTypeName = %8, wyjątek = %9, adnotacje = % 10, ProfileName = % 11, WorkflowDefinitionIdentity = % 12|WFTracking HealthMonitoring, WFTrackingHealthMonitoring,|  
|[119 — WorkflowInstanceUpdatedRecord](119-workflowinstanceupdatedrecord.md)|Informacje|TrackRecord = WorkflowInstanceUpdatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, stan = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, adnotacje = %8, ProfileName = %9|HealthMonitoring, WFTracking|  
|[225 — TraceCorrelationKeys](225-tracecorrelationkeys.md)|Informacje|Obliczona klucz korelacji "%1" przy użyciu wartości "%2" w zakresie nadrzędnym "%3".|Rozwiązywanie problemów z WFServices|  
|[440 — StartSignpostEvent1](440-startsignpostevent.md)|Informacje|Hranice aktivity|Rozwiązywanie problemów z WFServices|  
|[441 — StopSignpostEvent1](441-stopsignpostevent.md)|Informacje|Hranice aktivity|Rozwiązywanie problemów z WFServices|  
|[1001 — WorkflowApplicationCompleted](1001-workflowapplicationcompleted.md)|Informacje|WorkflowInstance Id: "%1" została zakończona w stanie zamkniętym.|WFRuntime|  
|[1002 — WorkflowApplicationTerminated](1002-workflowapplicationterminated.md)|Informacje|Identyfikator WorkflowApplication: "%1" została zakończona. Ukończono się w stanie Faulted z powodu wyjątku.|WFRuntime|  
|[1003 — WorkflowInstanceCanceled](1003-workflowinstancecanceled.md)|Informacje|WorkflowInstance Id: "%1" została ukończona w stanu Canceled.|WFRuntime|  
|[1004 — WorkflowInstanceAborted](1004-workflowinstanceaborted.md)|Informacje|WorkflowInstance Id: "%1" została przerwana z powodu wyjątku.|WFRuntime|  
|[1005 — WorkflowApplicationIdled](1005-workflowapplicationidled.md)|Informacje|Identyfikator WorkflowApplication: "%1" Wystąpił bezczynności.|WFRuntime|  
|[1006 — WorkflowApplicationUnhandledException](1006-workflowapplicationunhandledexception.md)|Błąd|WorkflowInstance Id: "%1" napotkał nieobsługiwany wyjątek.  Wyjątek pochodzi z działania "%2", DisplayName: "%3".  Zostaną podjęte następujące działania: %4.|WFRuntime|  
|[1007 — WorkflowApplicationPersisted](1007-workflowapplicationpersisted.md)|Informacje|Identyfikator WorkflowApplication: "%1" został zachowany.|WFRuntime|  
|[1008 — WorkflowApplicationUnloaded](1008-workflowapplicationunloaded.md)|Informacje|WorkflowInstance Id: "%1" został Unloaded.|WFRuntime|  
|[1009 — ActivityScheduled](1009-activityscheduled.md)|Informacje|Nadrzędne działanie "%1", DisplayName: "%2", InstanceId: "%3" podrzędnych zaplanowanego działania "%4" DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1010 — ActivityCompleted](1010-activitycompleted.md)|Informacje|Nadrzędne działanie "%1", DisplayName: "%2", InstanceId: "%3" podrzędnych zaplanowanego działania "%4" DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1011 — ScheduleExecuteActivityWorkItem](1011-scheduleexecuteactivityworkitem.md)|Pełny|ExecuteActivityWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1012 — StartExecuteActivityWorkItem](1012-startexecuteactivityworkitem.md)|Pełny|Rozpoczynanie wykonywania ExecuteActivityWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1013 — CompleteExecuteActivityWorkItem](1013-completeexecuteactivityworkitem.md)|Pełny|ExecuteActivityWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1014 — ScheduleCompletionWorkItem](1014-schedulecompletionworkitem.md)|Pełny|CompletionWorkItem zaplanowano nadrzędnego działania "%1", DisplayName: "%2", InstanceId: "%3".  Ukończono %4, DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1015 — StartCompletionWorkItem](1015-startcompletionworkitem.md)|Pełny|Rozpoczynanie wykonywania CompletionWorkItem dla nadrzędnego działania "%1", DisplayName: "%2", InstanceId: "%3". Ukończono %4, DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1016 — CompleteCompletionWorkItem](1016-completecompletionworkitem.md)|Pełny|CompletionWorkItem zostało ukończone dla nadrzędnej działania "%1", DisplayName: "%2", InstanceId: "%3". Ukończono %4, DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1017 — ScheduleCancelActivityWorkItem](1017-schedulecancelactivityworkitem.md)|Pełny|CancelActivityWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1018 — StartCancelActivityWorkItem](1018-startcancelactivityworkitem.md)|Pełny|Rozpoczynanie wykonywania CancelActivityWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1019 — CompleteCancelActivityWorkItem](1019-completecancelactivityworkitem.md)|Pełny|CancelActivityWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1020 — CreateBookmark](1020-createbookmark.md)|Pełny|Zakładka została utworzona dla działania "%1", DisplayName: "%2", InstanceId: "%3".  Nazwa_zakładki: %4, BookmarkScope: %5.|WFRuntime|  
|[1021 — ScheduleBookmarkWorkItem](1021-schedulebookmarkworkitem.md)|Pełny|BookmarkWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".  Nazwa_zakładki: %4, BookmarkScope: %5.|WFRuntime|  
|[1022 — StartBookmarkWorkItem](1022-startbookmarkworkitem.md)|Pełny|Rozpoczynanie wykonywania BookmarkWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".  Nazwa_zakładki: %4, BookmarkScope: %5.|WFRuntime|  
|[1023 — CompleteBookmarkWorkItem](1023-completebookmarkworkitem.md)|Pełny|BookmarkWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3". Nazwa_zakładki: %4, BookmarkScope: %5.|WFRuntime|  
|[1024 — CreateBookmarkScope](1024-createbookmarkscope.md)|Pełny|Utworzono BookmarkScope: %1.|WFRuntime|  
|[1025 — BookmarkScopeInitialized](1025-bookmarkscopeinitialized.md)|Pełny|BookmarkScope, który miał TemporaryId: "%1" została zainicjowana o identyfikatorze: "%2".|WFRuntime|  
|[1026 — ScheduleTransactionContextWorkItem](1026-scheduletransactioncontextworkitem.md)|Pełny|TransactionContextWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1027 — StartTransactionContextWorkItem](1027-starttransactioncontextworkitem.md)|Pełny|Rozpoczynanie wykonywania TransactionContextWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1028 — CompleteTransactionContextWorkItem](1028-completetransactioncontextworkitem.md)|Pełny|TransactionContextWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1029 — ScheduleFaultWorkItem](1029-schedulefaultworkitem.md)|Pełny|FaultWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".  Wyjątek został rozpropagowany działania "%4", DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1030 — StartFaultWorkItem](1030-startfaultworkitem.md)|Pełny|Rozpoczynanie wykonywania FaultWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".  Wyjątek został rozpropagowany działania "%4", DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1031 — CompleteFaultWorkItem](1031-completefaultworkitem.md)|Pełny|FaultWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3". Wyjątek został rozpropagowany działania "%4", DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1032 — ScheduleRuntimeWorkItem](1032-scheduleruntimeworkitem.md)|Pełny|Element roboczy środowiska uruchomieniowego została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1033 — StartRuntimeWorkItem](1033-startruntimeworkitem.md)|Pełny|Rozpoczynanie wykonywania elementu roboczego środowiska uruchomieniowego dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1034 — CompleteRuntimeWorkItem](1034-completeruntimeworkitem.md)|Pełny|Element roboczy środowisko uruchomieniowe zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3".|WFRuntime|  
|[1035 — RuntimeTransactionSet](1035-runtimetransactionset.md)|Pełny|Transakcja środowiska uruchomieniowego została ustawiona przez działanie "%1", DisplayName: "%2", InstanceId: "%3".  Wykonanie wyizolowane do działania "%4", DisplayName: '%5', InstanceId: '%6'.|WFRuntime|  
|[1036 — RuntimeTransactionCompletionRequested](1036-runtimetransactioncompletionrequested.md)|Pełny|Działanie "%1", DisplayName: "%2", InstanceId: "%3" zaplanowano ukończenia transakcji środowiska uruchomieniowego.|WFRuntime|  
|[1037 — RuntimeTransactionComplete](1037-runtimetransactioncomplete.md)|Pełny|Transakcja środowiska uruchomieniowego została ukończona ze stanem "%1".|WFRuntime|  
|[1038 — EnterNoPersistBlock](1038-enternopersistblock.md)|Pełny|Wprowadzenie bez blokady utrwalanie.|WFRuntime|  
|[1039 — ExitNoPersistBlock](1039-exitnopersistblock.md)|Pełny|Kończenie bez blokady utrwalanie.|WFRuntime|  
|[1040 — InArgumentBound](1040-inargumentbound.md)|Pełny|Argument "%1" w działaniu "%2", DisplayName: "%3", InstanceId: "%4" została powiązana z wartością: %5.|WFActivities|  
|[1041 — WorkflowApplicationPersistableIdle](1041-workflowapplicationpersistableidle.md)|Informacje|Identyfikator WorkflowApplication: "%1" jest bezczynny i stałe.  Zostaną podjęte następujące działania: %2.|WFRuntime|  
|[1101 — WorkflowActivityStart](1101-workflowactivitystart.md)|Informacje|WorkflowInstance Id: Aktivita E2E "%1"|WFRuntime|  
|[1102 — WorkflowActivityStop](1102-workflowactivitystop.md)|Informacje|WorkflowInstance Id: Aktivita E2E "%1"|WFRuntime|  
|[1103 — WorkflowActivitySuspend](1103-workflowactivitysuspend.md)|Informacje|WorkflowInstance Id: Aktivita E2E "%1"|WFRuntime|  
|[1104 — WorkflowActivityResume](1104-workflowactivityresume.md)|Informacje|WorkflowInstance Id: Aktivita E2E "%1"|WFRuntime|  
|[1124 — InvokeMethodIsStatic](1124-invokemethodisstatic.md)|Informacje|InvokeMethod "%1" - metoda jest statyczna.|WFRuntime|  
|[1125 — InvokeMethodIsNotStatic](1125-invokemethodisnotstatic.md)|Informacje|InvokeMethod "%1" - metoda nie jest statyczne.|WFRuntime|  
|[1126 — InvokedMethodThrewException](1126-invokedmethodthrewexception.md)|Informacje|Zgłoszono wyjątek metody wywoływane przez działanie "%1". %2|WFRuntime|  
|[1131 — InvokeMethodUseAsyncPattern](1131-invokemethoduseasyncpattern.md)|Informacje|InvokeMethod "%1" - metoda używa wzorca asynchronicznego "%2" i "%3".|WFRuntime|  
|[1132 — InvokeMethodDoesNotUseAsyncPattern](1132-invokemethoddoesnotuseasyncpattern.md)|Informacje|InvokeMethod "%1" - metoda nie korzysta z wzorca asynchronicznego.|WFRuntime|  
|[1140 — FlowchartStart](1140-flowchartstart.md)|Informacje|Schemat blokowy "%1" - Start zostało zaplanowane.|WFActivities|  
|[1141 — FlowchartEmpty](1141-flowchartempty.md)|Ostrzeżenie|Schemat blokowy "%1" - został wykonany przy użyciu nie Nodes.An zgłoszono wyjątek metody wywoływane przez działanie "%1". %2|WFActivities|  
|[1143 — FlowchartNextNull](1143-flowchartnextnull.md)|Informacje|Schemat blokowy "%1'/FlowStep - kolejnego węzła ma wartość null. Schemat blokowy wykonywania zakończy się.|WFActivities|  
|[1146 — FlowchartSwitchCase](1146-flowchartswitchcase.md)|Informacje|Schemat blokowy "%1'/FlowSwitch — przypadek"%2"został wybrany.|WFActivities|  
|[1147 — FlowchartSwitchDefault](1147-flowchartswitchdefault.md)|Informacje|Schemat blokowy "wybrano %1'/FlowSwitch — domyślna wielkość liter.|WFActivities|  
|[1148 — FlowchartSwitchCaseNotFound](1148-flowchartswitchcasenotfound.md)|Informacje|Schemat blokowy "%1'/FlowSwitch — można znaleźć, działanie Case ani domyślna wielkość liter dopasowanie wynik wyrażenia. Schemat blokowy wykonywania zakończy się.|WFActivities|  
|[1150 — CompensationState](1150-compensationstate.md)|Informacje|CompensableActivity "%1" jest w stanie "%2".|WFActivities|  
|[1223 — SwitchCaseNotFound](1223-switchcasenotfound.md)|Informacje|Działanie przełącznika "%1" nie można odnaleźć działania wielkości liter, wynik wyrażenia dopasowania.|WFActivities|  
|[1449 — WfMessageReceived](1449-wfmessagereceived.md)|Informacje|Wiadomość odebrana przez przepływ pracy|WFServices|  
|[1450 — WfMessageSent](1450-wfmessagesent.md)|Informacje|Komunikatu wysłanego z przepływu pracy|WFServices|  
|[2021 — ExecuteWorkItemStart](2021-executeworkitemstart.md)|Pełny|Wykonaj początek elementu roboczego|WFRuntime|  
|[2022 — ExecuteWorkItemStop](2022-executeworkitemstop.md)|Pełny|Wykonywanie pracy Zatrzymaj element|WFRuntime|  
|[2023 — SendMessageChannelCacheMiss](2023-sendmessagechannelcachemiss.md)|Pełny|Pozwól na pomijanie SendMessageChannelCache|WFRuntime|  
|[2024 — InternalCacheMetadataStart](2024-internalcachemetadatastart.md)|Pełny|Rozpoczęto InternalCacheMetadata działania "%1".|WFRuntime|  
|[2025 — InternalCacheMetadataStop](2025-internalcachemetadatastop.md)|Pełny|InternalCacheMetadata zatrzymana na działania "%1".|WFRuntime|  
|[2026 — CompileVbExpressionStart](2026-compilevbexpressionstart.md)|Pełny|Kompilowanie wyrażenie VB "%1"|WFRuntime|  
|[2027 — CacheRootMetadataStart](2027-cacherootmetadatastart.md)|Pełny|Data rozpoczęcia CacheRootMetadata działania "%1"|WFRuntime|  
|[2028 — CacheRootMetadataStop](2028-cacherootmetadatastop.md)|Pełny|CacheRootMetadata zatrzymana na aktywność: %1.|WFRuntime|  
|[2029 — CompileVbExpressionStop](2029-compilevbexpressionstop.md)|Pełny|Zakończono kompilowania VB wyrażenia.|WFRuntime|  
|[2576 — TryCatchExceptionFromTry](2576-trycatchexceptionfromtry.md)|Informacje|Działania TryCatch "%1" został zgłoszony wyjątek typu "%2".|WFActivities|  
|[2577 — TryCatchExceptionDuringCancelation](2577-trycatchexceptionduringcancelation.md)|Ostrzeżenie|Działanie podrzędne działania TryCatch '%1' został zgłoszony wyjątek w trakcie anulowania.|WFActivities|  
|[2578 — TryCatchExceptionFromCatchOrFinally](2578-trycatchexceptionfromcatchorfinally.md)|Ostrzeżenie|Catch lub Finally działania, który jest skojarzony z działania TryCatch "%1" został zgłoszony wyjątek.|WFActivities|  
|[3501 — InferredContractDescription](3501-inferredcontractdescription.md)|Informacje|Element ContractDescription o nazwie = "%1" i Namespace = "%2" została wykryta z WorkflowService.|WFServices|  
|[3502 — InferredOperationDescription](3502-inferredoperationdescription.md)|Informacje|Obiekt OperationDescription o nazwie = "%1" w kontrakcie "%2" została wykryta z WorkflowService. IsOneWay=%3.|WFServices|  
|[3503 — DuplicateCorrelationQuery](3503-duplicatecorrelationquery.md)|Ostrzeżenie|Znaleziono zduplikowane CorrelationQuery, w której = "%1". To zapytanie zduplikowane nie będzie używane, podczas obliczania korelacji.|WFServices|  
|[3507 — ServiceEndpointAdded](3507-serviceendpointadded.md)|Informacje|Punkt końcowy usługi został dodany dla adresu "%1", powiązania "%2" i kontraktu "%3".|WFServices|  
|[3508 — TrackingProfileNotFound](3508-trackingprofilenotfound.md)|Pełny|TrackingProfile "%1" dla ActivityDefinitionId "%2" nie można odnaleźć. TrackingProfile nie znajduje się w pliku konfiguracji, albo ActivityDefinitionId jest niezgodny.|WFServices|  
|[3550 — BufferOutOfOrderMessageNoInstance](3550-bufferoutofordermessagenoinstance.md)|Informacje|W tej chwili nie można wykonać operacji "%1". Nastąpi wtedy podjąć kolejną próbę, gdy wystąpienie usługi jest gotowy do przetwarzania tej operacji.|WFServices|  
|[3551 — BufferOutOfOrderMessageNoBookmark](3551-bufferoutofordermessagenobookmark.md)|Informacje|Nie można wykonać operacji "%2" na wystąpienie usługi "%1" w tej chwili. Nastąpi wtedy podjąć kolejną próbę, gdy wystąpienie usługi jest gotowy do przetwarzania tej operacji.|WFServices|  
|[3552 — MaxPendingMessagesPerChannelExceeded](3552-maxpendingmessagesperchannelexceeded.md)|Ostrzeżenie|Ograniczenie "MaxPendingMessagesPerChannel" limit "%1" został trafiony. Aby zwiększyć ten limit, Dopasuj właściwość MaxPendingMessagesPerChannel BufferedReceiveServiceBehavior.|WFServices limitu przydziału|  
|[3557 — TransactedReceiveScopeEndCommitFailed](3557-transactedreceivescopeendcommitfailed.md)|Informacje|Wywołanie EndCommit na Commitabletransakction o identyfikatorze = '%1' zgłosił TransactionException — z następującym komunikatem: "%2".|WFServices|  
|[4201 — EndSqlCommandExecute](4201-endsqlcommandexecute.md)|Pełny|Kończy wykonywanie polecenia SQL: %1|WFInstanceStore|  
|[4202 — StartSqlCommandExecute](4202-startsqlcommandexecute.md)|Pełny|Rozpoczynanie wykonywania polecenia SQL: %1|WFInstanceStore|  
|[4203 — RenewLockSystemError](4203-renewlocksystemerror.md)|Błąd|Nie można rozszerzyć wygaśnięcia blokady, wygaśnięcia blokady już przekazany lub właściciel blokady został usunięty. Aborting SqlWorkflowInstanceStore.|WFInstanceStore|  
|[4205 — FoundProcessingError](4205-foundprocessingerror.md)|Błąd|Polecenie nie powiodło się: %1|WFInstanceStore|  
|[4206 — UnlockInstanceException](4206-unlockinstanceexception.md)|Błąd|Wystąpił wyjątek %1 podczas próby odblokowania wystąpienia.|WFInstanceStore|  
|[4207 — MaximumRetriesExceededForSqlCommand](4207-maximumretriesexceededforsqlcommand.md)|Informacje|Wykonano rezygnacji ponowieniem uruchomienia polecenia SQL jako maksymalną liczbę ponownych prób.|WFInstanceStore limitu przydziału|  
|[4208 — RetryingSqlCommandDueToSqlError](4208-retryingsqlcommandduetosqlerror.md)|Informacje|Ponawianie próby za pomocą polecenia SQL ze względu na %1. numer błędu SQL.|WFInstanceStore|  
|[4209 — TimeoutOpeningSqlConnection](4209-timeoutopeningsqlconnection.md)|Błąd|Limit czasu podczas próby otwarcia połączenia SQL. Operacja nie została ukończona w ciągu przydzielonego limitu czasu %1. Czas przydzielony na tę operację mógł stanowić część większego limitu czasu.|WFInstanceStore|  
|[4210 — SqlExceptionCaught](4210-sqlexceptioncaught.md)|Ostrzeżenie|Przechwycono wyjątek SQL o numerze %1 komunikat %2.|WFInstanceStore|  
|[4211 — QueuingSqlRetry](4211-queuingsqlretry.md)|Ostrzeżenie|Kolejkowania ponownych prób z opóźnieniem %1 MS SQL.|WFInstanceStore|  
|[4212 — LockRetryTimeout](4212-lockretrytimeout.md)|Ostrzeżenie|Limit czasu, próbując uzyskać blokadę wystąpienia.  Operacja nie została ukończona w ciągu przydzielonego limitu czasu %1. Czas przydzielony na tę operację mógł stanowić część większego limitu czasu.|WFInstanceStore|  
|[4213 — RunnableInstancesDetectionError](4213-runnableinstancesdetectionerror.md)|Błąd|Wykrywania wystąpień możliwych do uruchomienia nie powiodła się z powodu następującego wyjątku|WFInstanceStore|  
|[4214 — InstanceLocksRecoveryError](4214-instancelocksrecoveryerror.md)|Błąd|Odzyskiwanie wystąpienia blokady nie powiodło się z powodu następującego wyjątku|WFInstanceStore|  
|[39456 — TrackingRecordDropped](39456-trackingrecorddropped.md)|Ostrzeżenie|Rozmiar śledzenia rekord %1 przekracza maksymalną dozwoloną przez sesję funkcji ETW dla dostawcy %2|WFTracking|  
|[39457 — TrackingRecordRaised](39457-trackingrecordraised.md)|Informacje|Rekord śledzenia %1 do %2.|WFRuntime|  
|[39458 — TrackingRecordTruncated](39458-trackingrecordtruncated.md)|Ostrzeżenie|Obcięte śledzenia rekord %1 zapisywane do sesji ETW za pomocą dostawcy %2. Usunięto użytkownika/zmienne/adnotacji danych|WFTracking|  
|[39459 — TrackingDataExtracted](39459-trackingdataextracted.md)|Pełny|Dane śledzenia %1 wyodrębnione w działaniu %2.|WFRuntime|  
|[39460 — TrackingValueNotSerializable](39460-trackingvaluenotserializable.md)|Ostrzeżenie|Wyodrębnione argumentu/zmiennej "%1" nie jest możliwy do serializacji.|WFTracking|  
|[57398 — MaxInstancesExceeded](57398-maxinstancesexceeded.md)|Ostrzeżenie|System osiągnięty limit ustawiony dla ograniczenia "MaxConcurrentInstances". Limit dla tego ograniczania zostało ustawione na %1. Wartość ograniczenia przepustowości można zmienić, modyfikując atrybut "maxConcurrentInstances" w elemencie serviceThrottle lub modyfikując właściwość "MaxConcurrentInstances" Zachowanie elementu ServiceThrottlingBehavior.|WFServices|
