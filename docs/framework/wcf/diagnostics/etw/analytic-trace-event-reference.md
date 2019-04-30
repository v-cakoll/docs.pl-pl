---
title: Odwołanie do zdarzenia śledzenia analitycznego
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 0f8b4c15f2afefbc62b98dca66dcf3ccc31b1dc0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753039"
---
# <a name="analytic-trace-event-reference"></a>Odwołanie do zdarzenia śledzenia analitycznego
W poniższej tabeli opisano poziomów zdarzeń, identyfikatory i komunikatów skojarzonych z WCF analityczne śledzenia.  
  
## <a name="event-reference"></a>Odwołanie do zdarzenia  
  
|Identyfikator zdarzenia|Poziom zdarzenia|Komunikat zdarzenia|słowa kluczowe|  
|--------------|-----------------|-------------------|--------------|  
|[131 — BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Pełny|Pula przydzielanie %1 bajtów.|Infrastruktura|  
|[132 — BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Pełny|Obiekt bufferpool ma rozmiar %1, zmieniając limit przydziału przez użytkownika %2.|Infrastruktura|  
|[133 — ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Pełny|We/Wy wątek wywołano wywołanie zwrotne harmonogramu.|Infrastruktura|  
|[134 — ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Pełny|We/Wy wątek wywołano wywołanie zwrotne harmonogramu.|Infrastruktura|  
|[201 — ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Informacje|Dyspozytor wywoływane "AfterReceiveReply" na ClientMessageInspector typu "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[202 — ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Informacje|Dyspozytor wywoływane "BeforeSendRequest" na ClientMessageInspector typu "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[203 — ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Informacje|Dyspozytor wywoływane "AfterCall" na ClientParameterInspector. typu "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[204 — ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Informacje|Dyspozytor wywoływane "BeforeCall" na ClientParameterInspector typu "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[205 — OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Informacje|OperationInvoker wywołał metodę "%1".|EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[206 — ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Informacje|Dyspozytor wywoływane ErrorHandler typu "%1" z powodu wyjątku typu "%3".  ErrorHandled == "%2".|Rozwiązywanie problemów, modelu ServiceModel|  
|[207 — FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Informacje|Dyspozytor wywoływane FaultProvider typu "%1", z wyjątkiem typu "%2".|Rozwiązywanie problemów, modelu ServiceModel|  
|[208 — MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Informacje|Dyspozytor wywoływane "AfterReceiveReply" na MessageInspector typu "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[209 — MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Informacje|Dyspozytor wywoływane "BeforeSendRequest" na MessageInspector typu "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[210 — MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Ostrzeżenie|Osiągnięto limit przepustowości "%1" z "%2".|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[211 — ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Informacje|Dyspozytor wywoływane "AfterCall" na ParameterInspector typu "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[212 — ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Informacje|Dyspozytor wywoływane "BeforeCall" na ParameterInspector typu "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[213 — ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|ServiceHost pracy: "%1".|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[214 — OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Informacje|OperationInvoker wykonać wywołanie metody "%1".  Czas trwania wywołania metody wynosiła ms "%2".|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[215 — MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Informacje|Transport otrzymał komunikat z "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[216 — MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Informacje|Transport wiadomości do "%1".|Rozwiązywanie problemów, modelu ServiceModel|  
|[217 — ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Informacje|Klient jest wykonywanie operacji "%1" zdefiniowanej w kontrakcie "%2". '% 3' zostanie wysłany komunikat.|Rozwiązywanie problemów, modelu ServiceModel|  
|[218 — ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Informacje|Klient ukończyć wykonywanie operacji "%1" zdefiniowanej w kontrakcie "%2". Wiadomość została wysłana do "%3".|Rozwiązywanie problemów, modelu ServiceModel|  
|[219 — ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Błąd|Wystąpił nieobsługiwany wyjątek typu "%2" podczas przetwarzania komunikatu.  ToString — pełny wyjątek: %1.|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[220 — MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Informacje|Dyspozytor wysłano komunikat do transportu. Identyfikator korelacji == "%1".|EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[221 — MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Informacje|Dyspozytor otrzymał komunikat z transportu. Identyfikator korelacji == "%1".|EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[222 — OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Ostrzeżenie|Metoda "%1" spowodowała nieobsługiwany wyjątek podczas wywoływania przez OperationInvoker. Czas trwania wywołania metody wynosiła ms "%2".|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[223 — OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Ostrzeżenie|Metoda "%1" zwróciła wyjątek FaultException —, po wywołaniu przez OperationInvoker. Czas trwania wywołania metody wynosiła ms "%2".|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[224 — MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Ostrzeżenie|Ograniczenie przepustowości "%1" z "%2" jest tylko na 70%.|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[226 — IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|%1 bezczynności usług poza %2 łączna liczba aktywacji usług zamknięte.|HealthMonitoring WebHost|  
|[301 — UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Błąd|Nazwa: "%1", odwołania: "%2", ładunek: %3.|EndToEndMonitoring UserEvents, HealthMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[302 — UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Ostrzeżenie|Nazwa: "%1", odwołania: "%2", ładunek: %3.|EndToEndMonitoring UserEvents, HealthMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[303 — UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Informacje|Nazwa: "%1", odwołania: "%2", ładunek: %3.|EndToEndMonitoring UserEvents, HealthMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|[401— StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Informacje|Hranice aktivity|Rozwiązywanie problemów|  
|[402 — StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Informacje|Hranice aktivity|Rozwiązywanie problemów|  
|[403 — SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Informacje|Hranice aktivity|Rozwiązywanie problemów|  
|[404 — ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Informacje|Hranice aktivity|Rozwiązywanie problemów|  
|[451 — MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Informacje|%1|Rozwiązywanie problemów, WCFMessageLogging|  
|[452 — MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Ostrzeżenie|%1|Rozwiązywanie problemów, WCFMessageLogging|  
|[499 — TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|Transferuje zdarzenie emitowane.|Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 — CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Informacje|Rozpocznij kompilację.|WebHost|  
|[502 — CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Informacje|Zakończ kompilację.|WebHost|  
|[503 — ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Informacje|Elementu ServiceHostFactory Rozpocznij tworzenie.|WebHost|  
|[504 — ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Informacje|Tworzenie z zakończenia elementu ServiceHostFactory.|WebHost|  
|[505 — CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Informacje|Begin CreateServiceHost.|WebHost|  
|[506 — CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Informacje|End CreateServiceHost.|WebHost|  
|[507 — HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Informacje|HostedTransportConfigurationManager rozpocząć inicjowanie konfiguracji.|WebHost|  
|[508 — HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Informacje|HostedTransportConfigurationManager konec inicializace konfigurace.|WebHost|  
|[509 — ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Informacje|HostedTransportConfigurationManager konec inicializace konfigurace.|ServiceHost|  
|[510 — ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Informacje|Otwórz ServiceHost zakończone.|ServiceHost|  
|[513 — WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Informacje|Odebrano żądanie przy użyciu ścieżki wirtualnej "%2" z "%1" w elemencie AppDomain.|WebHost|  
|[514 — WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Informacje|Zatrzymanie WebHostRequest.|WebHost|  
|[601 — CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Pełny|Przetworzony ServiceActivation Element adresu względnego: "%1" znormalizowanych adresu względnego "%2".||  
|[602 — CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Pełny|Przychodzące żądanie dopasowuje element ServiceActivation przy użyciu adresu "%1".||  
|[603 — AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Pełny|Przychodzące żądanie dopasowuje usługi WCF zdefiniowane trasy Asp.Net z adresem %1.|RoutingServices|  
|[604 — AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Pełny|Dodaje się nową trasę Asp.Net "%1" z "%2" typ serviceType i serviceHostFactoryType "%3".|RoutingServices|  
|[605 — IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Pełny|Wywołuje się IncrementBusyCount. Źródło: %1|WebHost|  
|[606 — DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Pełny|Wywołuje się DecrementBusyCount. Źródło: %1|WebHost|  
|[701 — ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Pełny|ServiceChannelOpen pracę.|WebHost|  
|[702 — ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Informacje|ServiceChannelOpen ukończone.|ServiceModel|  
|[703 — ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Informacje|ServiceChannelCall pracę.|ServiceModel|  
|[704 — ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Informacje|Wywołania asynchroniczne ServiceChannel pracę.|ServiceModel|  
|[706 — HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Pełny|Początek żądania wysyłania HTTP.|HTTP|  
|[707 — HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Pełny|Zatrzymanie żądania wysyłania HTTP.|HTTP|  
|[708 — HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Pełny|Wiadomość odebrana transportu http.|HTTP|  
|[709 — DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Informacje|Wysyła komunikat o pracę.|ServiceModel|  
|[710 — HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Pełny|Rozpocznij uwierzytelniania w przypadku wysyłania komunikatu.|ServiceModel|  
|[711 — DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Pełny|Rozpocznij autoryzacji do wysyłania wiadomości.|ServiceModel|  
|[712 — DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Informacje|Komunikat wysyła ukończone.|ServiceModel|  
|[715 — ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Informacje|Otwórz uruchomienie ServiceChannel.|ServiceModel|  
|[716 — ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Informacje|Otwórz zatrzymanie ServiceChannel.|ServiceModel|  
|[717 — HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Informacje|Http wysyła komunikat przesyłane strumieniowo pracę.|HTTP|  
|[1400 — ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Błąd|1%|ServiceModel|  
|[1401 — CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Błąd|1%|ServiceModel|  
|[1402 — IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Błąd|%1 połączenia puli klucz: %2|ServiceModel|  
|[1403 — LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Informacje|%1 połączenia puli klucz: %2|ServiceModel|  
|[1405 — OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Błąd|%1|ServiceModel|  
|[1406 — ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Błąd|%1|ServiceModel|  
|[1407 — SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Błąd|%1|ServiceModel|  
|[1409 — InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Informacje|%1|ServiceModel|  
|[1416 — MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Błąd|%1|Limit przydziału|  
|[1417 — MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Błąd|%1|Limit przydziału|  
|[1418 — MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Informacje|%1|Limit przydziału|  
|[1419 — MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Informacje|%1|Limit przydziału|  
|[1420 — ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Błąd|%1|Limit przydziału|  
|[1422 — NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Błąd|%1|Limit przydziału|  
|[1423 — NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Pełny|Negocjowania współczynnik pamięci podręcznej stanu wystawcy uwierzytelniania tokenu: %1 / %2|Limit przydziału|  
|[1424 — SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Pełny|Współczynnik sesji zabezpieczeń: %1 / %2|Limit przydziału|  
|[1430 — PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Pełny|Oczekujące współczynnik połączenia: %1 / %2|Limit przydziału|  
|[1431 — ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Pełny|Współczynnik równoczesnych sesji: %1 / %2|Limit przydziału|  
|[1432 — ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Pełny|Współczynnik równoczesnych sesji: %1 / %2|Limit przydziału|  
|[1433 — OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Pełny|Połączenia wychodzące na stosunek punkt końcowy: %1 / %2|Limit przydziału|  
|[1433 — OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Pełny|Połączenia wychodzące na stosunek punkt końcowy: %1 / %2|Limit przydziału|  
|[1436 — PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Pełny|Oczekujące wiadomości na kanale współczynnik: %1 / %2|Limit przydziału|  
|[1438 — ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Pełny|Współczynnik równoczesnych wystąpień: %1 / %2|Limit przydziału|  
|[1439 — PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Informacje|Zero oczekujące akceptuje w lewo|Limit przydziału|  
|[1441 — MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Ostrzeżenie|1%|Limit przydziału|  
|[1442 — ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Ostrzeżenie|Odbieranie liczbę ponownych prób osiągnęła wiadomości usługi MSMQ o identyfikatorze "%1"|Limit przydziału|  
|[1443 — MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Błąd|Maksymalna liczba ponownych prób cyklów Przekroczono wiadomości usługi MSMQ o identyfikatorze "%1"|Limit przydziału|  
|[1445 — ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Pełny|Tworzenia nowych "%1"|Limit przydziału|  
|[1446 — WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Pełny|Tworzenia nowych "%1"|Limit przydziału|  
|[1451 — MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Błąd|1%|Limit przydziału|  
|[3300 — ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Ostrzeżenie|Nie można ukończyć %1.|Kanał|  
|[3301 — ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Ostrzeżenie|Nie można Abandon %1.|Kanał|  
|[3303 — ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Ostrzeżenie|Kontekstu odbierania wystąpił błąd.|ServiceModel|  
|[3303 — ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Informacje|%1 zostało porzucone. wyjątek %2.|Kanał|  
|[3305 — ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Informacje|Liczba fabryki kanałów pamięci podręcznej wynosi: "%1".  Co najwyżej fabryki kanałów "%2" mogą być buforowane.|ServiceModel|  
|[3306 — ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Informacje|Fabryka kanałów ma zostały przestarzałe z pamięci podręcznej, ponieważ w pamięci podręcznej osiągnięto limit "%1".|ServiceModel|  
|[3307 — ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Informacje|Użyć zgodnych fabryki kanałów znalezionych w pamięci podręcznej.|ServiceModel|  
|[3308 — ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Informacje|Z pamięci podręcznej, nie za pomocą fabryki kanałów, czyli Buforowanie wyłączone dla wystąpienia.|ServiceModel|  
|[3309 — QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Informacje|Tworzenia zapytania przy użyciu "%1" została wykonana w identyfikatorze Uri żądania: "%2".|ServiceModel|  
|[3310 — DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Błąd|Operacja "%1" zostało wysłane z błędami.|ServiceModel|  
|[3311 — DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Informacje|Operacja "%1" został pomyślnie wysłany.|ServiceModel|  
|[3312 — MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informacje|Wiadomość z bajtów "%1" została odczytana przez koder.|Kanał|  
|[3312 — MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informacje|Komunikat o rozmiarze "%1" b został napisany przez koder.|Kanał|  
|[3314 — SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Błąd|Sesja Trwa przerywanie bezczynności kanału do identyfikatora uri: "%1".|ServiceModel|  
|[3319 — SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Pełny|Rozpoczęto akceptować połączenia.|TCP|  
|[3320 — SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Pełny|SocketId:% ListenerId:% 1 zaakceptowane 2.|TCP|  
|[3321 — ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Pełny|Puli dla %1 nie ma dostępnego połączenia i %2 zajęty połączeń.|Kanał|  
|[3322 — DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Pełny|Dyspozytor do deserializacji komunikatu żądania.|ServiceModel|  
|[3323 — DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Pełny|Dyspozytor ukończone deserializacji komunikatu żądania.|ServiceModel|  
|[3324 — DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Pełny|Dyspozytor pracę serializacji komunikatu odpowiedzi.|ServiceModel|  
|[3325 — DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Pełny|Dyspozytor wykonać serializacji komunikatu odpowiedzi.|ServiceModel|  
|[3326 — ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Pełny|Rozpoczęto serializacji żądania klienta.|ServiceModel|  
|[3327 — ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Pełny|Klient wykonać serializacji komunikatu żądania.|ServiceModel|  
|[3328 — ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Pełny|Klient uruchomiony podczas deserializacji komunikatu odpowiedzi.|ServiceModel|  
|[3329 — ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Pełny|Klient wykonać deserializacji komunikatu odpowiedzi.|ServiceModel|  
|[3330 — SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Pełny|Rozpoczęto negocjowanie zabezpieczeń.|Zabezpieczenia|  
|[3331 — SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Pełny|Ukończono negocjowanie zabezpieczeń.|Zabezpieczenia|  
|[3332 — SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Pełny|Otwieranie SecurityTokenProvider ukończone.|Zabezpieczenia|  
|[3333 — OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Pełny|Wychodzący komunikat został zabezpieczony.|Zabezpieczenia|  
|[3334 — IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Pełny|Przychodząca wiadomość została zweryfikowana.|Zabezpieczenia elementu ServiceModel|  
|[3335 — GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Pełny|Rozpoczęto pobieranie wystąpienia usługi.|ServiceModel|  
|[3336 — GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Pełny|Pobrać wystąpienia usługi.|ServiceModel|  
|[3337 — ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Pełny|ChannelHandlerId:% 1 - komunikat otrzymują pętli pracę.|Kanał|  
|[3338 — ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Pełny|ChannelHandlerId:% 1 - komunikat otrzymują pętli zatrzymana.|Kanał|  
|[3339 — ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Pełny|Utworzony element ChannelFactory.|ServiceModel|  
|[3340 — PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Pełny|Połączenie potoku zaakceptować uruchomiono na komputerze %1.|Kanał|  
|[3341 — PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Pełny|Połączenie potoku akceptowane.|Kanał|  
|[3342 — EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Pełny|Ustanawianie połączenia pracę dla %1.|Kanał|  
|[3343 — EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Pełny|Nawiązano połączenie.|Kanał|  
|[3345 — SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Pełny|Zrozumienie Preambuła sesji dla "%1".|Kanał|  
|[3346 — ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Błąd|Wysyłanie błędów "%1" czytnik połączenia.|Kanał|  
|[3347 — SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Pełny|Gniazda zaakceptować zamknięte.|TCP|  
|[3348 — ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Krytyczny|Host usługi jest błędny.|TCP|  
|[3349 — ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Pełny|Odbiornik otwierania dla "%1".|Kanał|  
|[3350 — ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Pełny|Otwórz odbiornika ukończone.|Kanał|  
|[3351 — ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Pełny|Osiągnięto przydział maksymalnej liczbie połączeń w puli serwera.|Limit przydziału|  
|[3352 — TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Błąd|Upłynął limit czasu SocketId:% 1 zdalny adres %2.|TCP|  
|[3353 — TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Ostrzeżenie|SocketId:% 1 zdalny adres %2 miał błąd resetowania połączenia.|TCP|  
|[3354 — ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Pełny|Ukończono negocjowanie zabezpieczeń usługi.|Zabezpieczenia|  
|[3355 — SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Błąd|Przetwarzanie negocjowanie zabezpieczeń nie powiodło się.|Zabezpieczenia|  
|[3356 — SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Pełny|Weryfikacja zakończyła się pomyślnie.|Zabezpieczenia|  
|[3357 — SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Błąd|Weryfikacja zabezpieczeń nie powiodło się.|Zabezpieczenia|  
|[3358 — PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Pełny|Gniazda duplikowana dla %1.|ActivationServices|  
|[3359 — SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Pełny|Personifikacja zabezpieczeń zakończyło się pomyślnie.|Zabezpieczenia|  
|[3360 — SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Ostrzeżenie|Personifikacja zabezpieczeń nie powiodła się.|Zabezpieczenia|  
|[3361 — HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Ostrzeżenie|Żądanie kanał HTTP zostało przerwane.|HTTP|  
|[3362 — HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Ostrzeżenie|Przerwano odpowiedzi kanał HTTP.|HTTP|  
|[3363 — HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Ostrzeżenie|Uwierzytelnianie HTTP nie powiodło się.|HTTP|  
|[3364 — SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Pełny|Rejestracja SharedListenerProxy pracę dla identyfikatora uri "%1".|ActivationServices|  
|[3365 — SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Pełny|Zatrzymaj rejestrowanie SharedListenerProxy.|ActivationServices|  
|[3366 — SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Błąd|Zarejestruj się SharedListenerProxy nie powiodło się ze stanem "%1".|ActivationServices|  
|[3367 — ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Błąd|ConnectionPoolPreambleFailed.|Kanał|  
|[3368 — SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Pełny|SslOnAcceptUpgradeStart|Zabezpieczenia|  
|[3369 — SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Pełny|SslOnAcceptUpgradeStop|Zabezpieczenia|  
|[3370 — BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Pełny|BinaryMessageEncoder pracę, kodowania wiadomości.|Kanał|  
|[3371 — MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Pełny|MtomMessageEncoder pracę, kodowania wiadomości.|Kanał|  
|[3372 — TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Pełny|TextMessageEncoder pracę, kodowania wiadomości.|Kanał|  
|[3373 — BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Pełny|BinaryMessageEncoder do dekodowania komunikatu.|Kanał|  
|[3374 — MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Pełny|MtomMessageEncoder do dekodowania komunikatu.|Kanał|  
|[3375 — TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Pełny|TextMessageEncoder do dekodowania komunikatu.|Kanał|  
|[3376 — HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Informacje|Transportu HTTP do odbierania wiadomości.|HTTP|  
|[3377 — SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Pełny|Bajty odczytu "%2" SocketId:% 1 odczytu z "%3".|TCP|  
|[3378 — SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Pełny|Bajty odczytu "%2" SocketId:% 1 odczytu z "%3".|TCP|  
|[3379 — SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Pełny|SocketId:% 1 Bajty zapisu "%2" do "%3".|TCP|  
|[3380 — SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Pełny|SocketId:% 1 Bajty zapisu "%2" do "%3".|TCP|  
|[3381 — SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Pełny|Wysyłane potwierdzenie SessionId:% 1.|Kanał|  
|[3382 — ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Informacje|Ponowne łączenie SessionId:% 1.|Kanał|  
|[3383 — ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Informacje|Błędne SessionId:% 1.|Kanał|  
|[3384 — WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Pełny|WindowsStreamSecurity zainicjować uaktualnienie zabezpieczeń.|Zabezpieczenia|  
|[3385 — WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Pełny|Przesyłania strumieniowego zabezpieczeń na akceptowanie uaktualniania systemu Windows.|Zabezpieczenia|  
|[3386 — SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Ostrzeżenie|Trwa przerywanie działania SocketId:% 1.|TCP|  
|[3388 — HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Pełny|Początek HttpGetContext.|HTTP|  
|[3389 — ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Pełny|Klient wysyłania Preambuła rozpoczęcia.|Kanał|  
|[3390 — ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Pełny|Klient wysyłając polecenia Zatrzymaj preambuły.|Kanał|  
|[3391 — HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Ostrzeżenie|Nie można otrzymać komunikat HTTP.|HTTP|  
|[3392 — TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Informacje|TransactionScope jest tworzona przy użyciu LocalIdentifier: "%1" i DistributedIdentifier: "%2".|ServiceModel|  
|[3393 — StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Informacje|Strumieniowa wiadomość została przeczytana przez koder.|Kanał|  
|[3394 — StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Informacje|Strumieniowa wiadomość został napisany przez koder.|Kanał|  
|[3395 — MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Informacje|Komunikat został zapisany asynchronicznie przez koder.|Kanał|  
|[3396 — BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Informacje|Bajty zapisu BufferId:% 1 ukończone "%2" do zasadniczego strumienia.|Kanał|  
|[3397 — BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Informacje|Komunikat został zapisany asynchronicznie przez koder.|Kanał|  
|[3398 — PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Pełny|Przekazać pamięci współdzielonej, utworzone w "%1".|Kanał|  
|[3399 — NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Pełny|"%1" utworzył nazwany potok.|Kanał|  
|[3401 — SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Pełny|Weryfikacja podpisu pracę.|Zabezpieczenia|  
|[3402 — SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Pełny|Weryfikacja podpisu zakończyło się pomyślnie.|Zabezpieczenia|  
|[3403 — WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Pełny|Opakowana odszyfrowywania klucza uruchomienia.|Zabezpieczenia|  
|[3404 — WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Pełny|Opakowana odszyfrowywania klucza zakończyło się pomyślnie.|Zabezpieczenia|  
|[3405 — EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Pełny|Zaszyfrowany czas rozpoczęcia przetwarzania danych.|Zabezpieczenia|  
|[3406 — EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Pełny|Przetwarzanie danych zaszyfrowanych zakończyło się pomyślnie.|Zabezpieczenia|  
|[3407 — HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Pełny|Program obsługi komunikatów HTTP pracę, przetwarza żądanie przychodzące.|HTTP|  
|[3408 — HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Pełny|Program obsługi komunikatów HTTP do asynchronicznego przetwarzania żądania przychodzącego.|HTTP|  
|[3409 — HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Pełny|Program obsługi komunikatów HTTP zakończone przetwarzania przychodzącego żądania.|HTTP|  
|[3410 — HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Ostrzeżenie|Program obsługi komunikatów HTTP jest błędne.|HTTP|  
|[3411 — HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Błąd|Upłynął limit czasu połączenia protokołu WebSocket.|HTTP|  
|[3412 — HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Pełny|Program obsługi komunikatów HTTP do przetwarzania odpowiedzi.|HTTP|  
|[3413 — HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Pełny|Program obsługi komunikatów HTTP do przetwarzania odpowiedzi asynchronicznie.|HTTP|  
|[3414 — HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Pełny|Program obsługi komunikatów HTTP zakończone przetwarzania odpowiedzi.|HTTP|  
|[3415 — WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Pełny|Żądanie połączenia protokołu WebSocket do "%1" Wyślij rozpoczęcia.|HTTP|  
|[3416 — WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Pełny|Wysłane żądanie połączenia WebSocketId:% 1.|HTTP|  
|[3417 — WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Pełny|Połączenie WebSocket zaakceptować rozpoczęcia.|HTTP|  
|[3418 — WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Pełny|Połączenie WebSocketId:% 1 akceptowane.|HTTP|  
|[3419 — WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Błąd|Połączenie WebSocket odrzucone z kodem stanu "%1"|HTTP|  
|[3420 — WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Błąd|Żądanie połączenia protokołu WebSocket nie powiodło się: "%1"|HTTP|  
|[3421 — WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Błąd|WebSocketId:% 1 połączenie zostało przerwane.|HTTP|  
|[3422 — WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Pełny|WebSocketId:% 1 Bajty zapisu "%2" do "%3".|HTTP|  
|[3423 — WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Pełny|Zatrzymanie asynchroniczny zapis WebSocketId:% 1.|HTTP|  
|[3424 — WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Pełny|Początek WebSocketId:% 1 odczytu.|HTTP|  
|[3425 — WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Pełny|WebSocketId:% 1 odczytu bajtów "%2" z "%3".|HTTP|  
|[3426 — WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Pełny|Wysyłanie WebSocketId:% 1 Zamknij komunikat "%2" ze stanem Zamknij "%3".|HTTP|  
|[3427 — WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Pełny|Wysyłanie WebSocketId:% 1 Zamknij komunikat wyjściowy do "%2" ze stanem Zamknij "%3".|HTTP|  
|[3428 — WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Pełny|WebSocketId:% 1 połączenie zamknięte.|HTTP|  
|[3429 — WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Pełny|Połączenie WebSocketId:% 1 Zamknij komunikat o stanie "%2".|HTTP|  
|[3430 — WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Pełny|Przy użyciu WebSocketVersion z klienta protokołu WebSocket fabryki typu "%1".|HTTP|  
|[3431 — WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Pełny|Tworzenie klienta protokołu WebSocket za pomocą fabryki typu "%1".|HTTP|  
|[3553 — XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Informacje|Początek xamlServicesLoad|WebHost|  
|[3554 — XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Informacje|XamlServicesLoad Stop|WebHost|  
|[3555 — CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Informacje|Początek CreateWorkflowServiceHost|WebHost|  
|[3556 — CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Informacje|CreateWorkflowServiceHost Stop|WebHost|  
|[3558 — ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Informacje|Uruchomienie aktywacji usługi|WebHost|  
|[3559 — ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Informacje|Usługa aktywacji Stop|WebHost|  
|[3560 — ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Pełny|Dostępna pamięć (w bajtach): %1|Limit przydziału|  
|[3800 — RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Informacje|Usługa routingu dobiega końca klienta "%1".|RoutingServices|  
|[3800 — RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Ostrzeżenie|Klient usługi routingu "%1" Wystąpił błąd.|RoutingServices|  
|[3802 — RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Informacje|Usługa routingu wiadomości jednym ze sposobów jest kończonych.|RoutingServices|  
|[3803 — RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Błąd|Usługa routingu nie powiodło się podczas przetwarzania komunikatu w punkcie końcowym przy użyciu adresu "%1".|RoutingServices|  
|[3804 — RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Informacje|Usługa routingu jest utworzenie klienta dla punktu końcowego: "%1".|RoutingServices|  
|[3805 — RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Pełny|Usługa routingu jest skonfigurowana z RouteOnHeadersOnly: %1, SoapProcessingEnabled: %2, EnsureOrderedDispatch: %3.|RoutingServices|  
|[3807 — RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Informacje|Sobie radzi z komunikatu odpowiedzi żądania usługa routingu.|RoutingServices|  
|[3809 — RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Pełny|Usługa routingu kierowane wiadomości o identyfikatorze: "%1" do %2 endpoint list.|RoutingServices|  
|[3810 — RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Informacje|Nowe RoutingConfiguration zostały doliczone do usługa routingu.|RoutingServices|  
|[3815 — RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Informacje|Usługa routingu przetwarza komunikat o identyfikatorze: "%1", akcja: "%2" dla ruchu przychodzącego adresu URL: "%3" odebrane w transakcji: %4.|RoutingServices|  
|[3816 — RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Informacje|Usługa routingu przesyła komunikat o identyfikatorze: "%1" [operacji %2], "% 3".|RoutingServices|  
|[3817 — RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Informacje|Usługa routingu jest zatwierdzanie transakcji o identyfikatorze: "%1".|RoutingServices|  
|[3818 — RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Błąd|Składnik usługi routingu %1 napotkała wyjątek dwustronnego wywołania zwrotnego.|RoutingServices|  
|[3819 — RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Informacje|Routing wiadomości usługi o identyfikatorze: "%1" [operacji %2] przeniesione do endpoint kopii zapasowych "%3".|RoutingServices|  
|[3820 — RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Informacje|Usługa routingu utworzyć nową transakcję o identyfikatorze "%1" do przetwarzania komunikatów.|RoutingServices|  
|[3821 — RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Ostrzeżenie|Usługa routingu nie powiodło się podczas zamykania wychodzącego klienta "%1".|RoutingServices|  
|[3822 — RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Informacje|Usługa routingu ponownie wysyła komunikat odpowiedzi z akcji "%1".|RoutingServices|  
|[3823 — RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Ostrzeżenie|Usługa routingu wysyła ponownie odporności komunikat odpowiedzi z akcji "%1".|RoutingServices|  
|[3824 — RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Pełny|Usługa routingu wywołuje ReceiveContext.Complete komunikatu o identyfikatorze: "%1".|RoutingServices|  
|[3825 — RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Ostrzeżenie|Usługa routingu wywołuje ReceiveContext.Abandon komunikatu o identyfikatorze: "%1".|RoutingServices|  
|[3826 — RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Pełny|Usługa routingu będzie wysyłać komunikatów za pomocą istniejącej transakcji "%1".|RoutingServices|  
|[3827 — RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Ostrzeżenie|Usługa routingu nie powiodło się podczas wysyłania do "%1".|RoutingServices|  
|[3828 — RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Informacje|Routing Service MessageFilterTable Match Start.|RoutingServices|  
|[3829 — RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Informacje|Routing Service MessageFilterTable Match Stop.|RoutingServices|  
|[3830 — RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Pełny|Usługa routingu jest wywołanie przerwania na kanale: "%1".|RoutingServices|  
|[3831 — RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Pełny|Usługa routingu obsłużonych wyjątek.|RoutingServices|  
|[3832 — RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Informacje|Usługa routingu pomyślnie przesłanych wiadomości o identyfikatorze: "%1 [operacji %2]"% 3".|RoutingServices|  
|[4001 — TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Pełny|Sesja transportowa odbiornika, odebrania z "%1"|ActivationServices|  
|[4002 — FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Krytyczny|FailFastException.|ActivationServices|  
|[4003 — ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Błąd|Błąd potoku można uruchomić usługi.|ActivationServices|  
|[4008 — DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Pełny|Rozpoczęto wysyłanie sesji.|ActivationServices|  
|[4008 — DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Ostrzeżenie|Wysyłania sesji dla "%1" nie powiodło się, ponieważ oczekujących sesji kolejka jest pełna z "%2", oczekujące elementy.|ActivationServices|  
|[4011 — MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Pełny|Kolejka komunikatów zarejestrować rozpoczęcia.|ActivationServices|  
|[4012 — MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Błąd|Komunikat kolejki rejestracji zostało przerwane ze stanem: "%1" dla identyfikatora uri: "%2".|ActivationServices|  
|[4013 — MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Pełny|Kolejka komunikatów wyrejestrować powiodła się dla identyfikatora uri: "%1".|ActivationServices|  
|[4014 — MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Błąd|Komunikat kolejki rejestracji dla identyfikatora uri: "%1" nie powiodło się ze stanem: "%2".|ActivationServices|  
|[4015 — MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Informacje|Rejestracja kolejki komunikatów zakończone dla identyfikatora uri "%1".|ActivationServices|  
|[4016 — MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Błąd|Kolejka komunikatów nie powiodło się duplikowania gniazda.|ActivationServices|  
|[4019 — MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Pełny|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 — TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Pełny|Odbiornik transportu TCP rozpoczyna nasłuchiwanie w identyfikatorze uri: "%1".|ActivationServices|  
|[4021 — TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Pełny|Odbiornik transportu TCP nasłuchuje.|ActivationServices|  
|[4022 — WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Błąd|Kod błędu: % 1|ActivationServices|  
|[4023 — WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Informacje|Został zamyka wszystkie wystąpienia kanałów odbiornika ukończone.|ActivationServices|  
|[4024 — WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Błąd|Kod błędu: % 1|ActivationServices|  
|[4025 — OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Błąd|Kod błędu: % 1|ActivationServices|  
|[4026 — WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Pełny|WAS Connected.|ActivationServices|  
|[4027 — WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Pełny|ZOSTAŁ rozłączony.|ActivationServices|  
|[4028 — PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Pełny|Nasłuchiwanie rozpoczniesz pracę z uri:% 1 odbiornik transportu potoku.|ActivationServices|  
|[4029 — PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Pełny|Transport potoku odbiornika zatrzymanie nasłuchiwania.|ActivationServices|  
|[4030 — DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Informacje|Wysyłanie sesji zakończyło się pomyślnie.|ActivationServices|  
|[4031 — DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Błąd|Wysyłanie sesji nie powiodło się.|ActivationServices|  
|[4032 — WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Krytyczny|ZOSTAŁ upłynął limit czasu połączenia.|ActivationServices|  
|[4033 — RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Pełny|Wyszukiwanie w tabeli routingu pracę.|ActivationServices|  
|[4034 — RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Pełny|Ukończono wyszukiwania tabeli routingu.|ActivationServices|  
|[4035 — PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Pełny|Oczekujące współczynnik kolejki sesji: %1 / %2|Limit przydziału|  
|[4600 — MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Ostrzeżenie|Nie jest zarejestrowany komunikat o błędzie, ponieważ jego rozmiar przekracza rozmiar zdarzenia ETW.|WCFMessageLogging|  
|[4801 — DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Ostrzeżenie|Klasa DiscoveryClient utworzony wewnątrz DiscoveryClientChannel nie powiodło się zamknięcie i dlatego została przerwana.|Odnajdywanie|  
|[4802 — DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Informacje|Protocolexception — zostało pominięte podczas zamykania klasa DiscoveryClient. Być może nadal próby wysłania odpowiedzi klasa DiscoveryClient discoveryservice i.|Odnajdywanie|  
|[4803 — DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Informacje|Klasa DiscoveryClient odebrał komunikat multiemisji pomijanie z DiscoveryProxy.|Odnajdywanie|  
|[4804 — DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Informacje|Komunikat %1 z messageId = "%2" zostało porzucone, klasa DiscoveryClient, ponieważ odpowiednia Operacja %3 zostało ukończone.|Odnajdywanie|  
|[4805 — DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Ostrzeżenie|Komunikat %1 z messageId = "%2" zostało porzucone, ponieważ ma on nieprawidłową zawartość.|Odnajdywanie|  
|[4806 — DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Ostrzeżenie|Komunikat %1 z messageId = "%2" i relatesTo = "%3" zostało porzucone, klasa DiscoveryClient, ponieważ odpowiednia operacja %4 zostało ukończone lub wartość relatesTo jest nieprawidłowa.|Odnajdywanie|  
|[4807 — DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Ostrzeżenie|Komunikat żądania odnajdywania z messageId = "%1" został porzucony, ponieważ miał nieprawidłowy adres.|Odnajdywanie|  
|[4808 — DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Ostrzeżenie|Komunikat %1 zostało porzucone, ponieważ nie ma żadnej zawartości.|Odnajdywanie|  
|[4809 — DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Ostrzeżenie|Komunikat %1 zostało porzucone, ponieważ nagłówek wiadomości nie zawiera wymaganej właściwości MessageId.|Odnajdywanie|  
|[4810 — DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Ostrzeżenie|Komunikat %1 z messageId = "%2" zostało porzucone, klasa DiscoveryClient, ponieważ nie ma właściwości DiscoveryMessageSequence.|Odnajdywanie|  
|[4811 — DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Ostrzeżenie|Komunikat %1 z messageId = "%2" zostało porzucone, klasa DiscoveryClient, ponieważ nagłówek wiadomości nie zawiera wymaganej właściwości RelatesTo.|Odnajdywanie|  
|[4812 — DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Ostrzeżenie|Komunikat żądania odnajdywania z messageId = "%1" został porzucony, ponieważ nie ma adresu ReplyTo.|Odnajdywanie|  
|[4813 — DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Ostrzeżenie|Komunikat %1 z messageId = "%2" został porzucony, ponieważ jest duplikatem.|Odnajdywanie|  
|[4814 — EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informacje|Odnajdowanie punktu końcowego za pomocą EndpointAddress = "%1" i identyfikatorze ListenUri = "%2" został wyłączony.|Odnajdywanie|  
|[4814 — EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informacje|Odnajdowanie punktu końcowego za pomocą EndpointAddress = "%1" i identyfikatorze ListenUri = "%2" został włączony.|Odnajdywanie|  
|[4816 — FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Pełny|Zainicjowano operację Znajdź w DiscoveryClientChannel, aby wykryć punkty końcowe:.|Odnajdywanie|  
|[4817 — InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Ostrzeżenie|DiscoveryClientChannel nie można utworzyć kanału o wykrytych punktu końcowego za pomocą EndpointAddress = "%1" i za pośrednictwem = "%2". DiscoveryClientChannel podejmie teraz próbę użycia następnego dostępnego odnalezionych punktu końcowego.|Odnajdywanie|  
|[4818 — InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Ostrzeżenie|DiscoveryClientChannel nie powiodło się otworzenie kanału z punktem końcowym odnalezione za pomocą EndpointAddress = "%1" i za pośrednictwem = "%2". DiscoveryClientChannel podejmie teraz próbę użycia następnego dostępnego odnalezionych punktu końcowego.|Odnajdywanie|  
|[4819 — InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Informacje|DiscoveryClientChannel pomyślnie odnaleźć punktu końcowego i otwarty kanał korzystania z niego. Klient jest połączony z usługą za pomocą EndpointAddress = "%1" i za pośrednictwem = "%2".|Odnajdywanie|  
|[4820 — SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Informacje|SynchronizationContext została zresetowana do wartości oryginalnej %1 DiscoveryClientChannel.|Odnajdywanie|  
|[4821 — SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Informacje|SynchronizationContext została ustawiona na wartość null przez DiscoveryClientChannel przed rozpoczęciem operacji wyszukiwania.|Odnajdywanie|  
|[5001 — DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Pełny|DataContract serializować %1 z surogaty rozpoczęcia.|Serializacja|  
|[5002 — DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Pełny|DataContract serializacji z surogaty stop.|Serializacja|  
|[5003 — DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Pełny|DataContract deserializacji %1 z surogaty rozpoczęcia.|Serializacja|  
|[5004 — DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Pełny|DataContract deserializacji za pomocą surogaty zatrzymania.|Serializacja|  
|[5005 — ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Pełny|Początek ImportKnownTypes.|Serializacja|  
|[5006 — ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Pełny|Zatrzymaj ImportKnownTypes.|Serializacja|  
|[5007 — DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Pełny|Rozpoznawanie %1 start rozpoznawania nazw schematu DataContract.|Serializacja|  
|[5008 — DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Pełny|DataContract Generowanie zapisywania %1 w %2 start.|Serializacja|  
|[5009 — DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Pełny|DataContract Generowanie zatrzymania składnika zapisywania.|Serializacja|  
|[5010 — DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Pełny|DataContract Generowanie czytnika %1 w %2 start.|Serializacja|  
|[5011 — DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Pełny|Zatrzymanie generowanie schematu DataContract.|Serializacja|  
|[5012 — DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Pełny|JSON Generowanie czytnika %1 w %2 start.|Serializacja|  
|[5013 — DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Pełny|Zatrzymanie generowania czytnika JSON.|Serializacja|  
|[5014 — DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Pełny|JSON Generowanie zapisywania %1 w %2 start.|Serializacja|  
|[5015 — DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Pełny|JSON Generowanie zatrzymania składnika zapisywania.|Serializacja|  
|[5016 — GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Pełny|Generowanie Xml można serializować do uruchamiania "%1".|Serializacja|  
|[5017 — GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Pełny|Generowanie stop serializacji Xml.|Serializacja|  
|[5203 — JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Pełny|JsonMessageEncoder do dekodowania komunikatu.|Kanał|  
|[5204 — JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Pełny|JsonMessageEncoder pracę, kodowania wiadomości.|Kanał|  
|[5402 — TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Pełny|Rozpoczęto weryfikację SecurityToken (typ "%1" i identyfikatorze "%2").|Zabezpieczenia|  
|[5403 — TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Pełny|Pomyślnie przeprowadzono weryfikację SecurityToken (typ "%1" i identyfikatorze "%2").|Zabezpieczenia|  
|[5404 — TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Błąd|Nie można zweryfikować SecurityToken (typ "%1" i identyfikatorze "%2"). %3|Zabezpieczenia|  
|[5405 — GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Pełny|Pobieranie wystawcy Nazwa: % 1 z tokenId:% 2 zakończyło się pomyślnie.|Zabezpieczenia|  
|[5406 — GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Błąd|Nie można pobrać nazwy wystawcy z tokenId:% 1.|Zabezpieczenia|  
|[5600 — FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Pełny|Rozpoczęto przetwarzanie komunikatów federacji.|Zabezpieczenia|  
|[5601 — FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Pełny|Przetwarzanie komunikatów Federacji zakończyło się pomyślnie.|Zabezpieczenia|  
|[5602 — FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Pełny|Tworzenie komunikatu federacji z post formularza pracy.|Zabezpieczenia|  
|[5603 — FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Pełny|Tworzenie komunikatu federacji z post formularza zakończyło się pomyślnie.|Zabezpieczenia|  
|[5604 — SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Pełny|Rozpoczęto odczytywanie tokenu sesji z pliku cookie sesji.|Zabezpieczenia|  
|[5605 — SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Pełny|Odczytywanie tokenu sesji z pliku cookie sesji zakończyło się pomyślnie.|Zabezpieczenia|  
|[5606 — PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Pełny|Podmiot zabezpieczeń jest ustawienie z tokenu relace pracę.|Zabezpieczenia|  
|[5607 — PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Pełny|Ustawienia jednostki z tokenu relace zakończyło się pomyślnie.|Zabezpieczenia|  
|[57393 — AppDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Informacje|Zwalnianie obiektu AppDomain. AppDomain.FriendlyName %1, ProcessName %2, ProcessId %3.|Infrastruktura|  
|[57394 — HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Informacje|Obsługa wyjątku.|Infrastruktura|  
|[57395 — ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Błąd|Wystąpił nieoczekiwany błąd. Aplikacje nie powinny podejmować próby obsługi tego błędu. W celach diagnostycznych ten komunikat w języku angielskim jest skojarzony z określonym błędem: %1.|Infrastruktura|  
|[57396 — ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Ostrzeżenie|Zostanie zgłoszony wyjątek. Źródło %1.|Infrastruktura|  
|[57397 — UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Krytyczny|Nieobsługiwany wyjątek.|Infrastruktura|  
|[57399 — TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Krytyczny|Zapisano w elemencie EventLog.|Infrastruktura|  
|[57400 — TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Błąd|Zapisano w elemencie EventLog.|Infrastruktura|  
|[57401 — TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Informacje|Zapisano w elemencie EventLog.|Infrastruktura|  
|[57402 — TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Pełny|Zapisano w elemencie EventLog.|Infrastruktura|  
|[57403 — TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Ostrzeżenie|Zapisano w elemencie EventLog.|Infrastruktura|  
|[57404 — HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Ostrzeżenie|Obsługa wyjątku.|Infrastruktura|  
|[62326 — HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Informacje|Dokument XAML hostów adresu url "%1" z elementem głównym typu "%2". Typ programu obsługi HTTP "%3" jest pobierany do obsługi wszystkich żądań wykonanych w odniesieniu do tego adresu url.|WebHost|
