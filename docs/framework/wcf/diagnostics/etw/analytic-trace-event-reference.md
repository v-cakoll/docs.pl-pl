---
title: "Odwołanie do zdarzenia śledzenia analitycznego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
caps.latest.revision: "50"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b47456ecea86652e80bb60f155bffd6100e1fc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="analytic-trace-event-reference"></a>Odwołanie do zdarzenia śledzenia analitycznego
W poniższej tabeli opisano poziomów zdarzeń, identyfikatory, oraz komunikatów związanych z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] śledzenie danych analitycznych.  
  
## <a name="event-reference"></a>Odwołanie do zdarzenia  
  
|Identyfikator zdarzenia|Poziom zdarzenia|Komunikat zdarzenia|Słowa kluczowe|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Pełny|Pula alokacji %1 bajtów.|Infrastruktura|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Pełny|Obiekt bufferpool ma rozmiar %1, Zmiana limitu przydziału przez użytkownika %2.|Infrastruktura|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Pełny|Wątków We/Wy wywołano wywołanie zwrotne harmonogramu.|Infrastruktura|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Pełny|Wątków We/Wy wywołano wywołanie zwrotne harmonogramu.|Infrastruktura|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Informacje|Dyspozytor wywołał "AfterReceiveReply" w obiekcie ClientMessageInspector typu "%1".|Rozwiązywanie problemów, ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Informacje|Dyspozytor wywołał "BeforeSendRequest" w obiekcie ClientMessageInspector typu "%1".|Rozwiązywanie problemów, ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Informacje|Dyspozytor wywołał metodę "AfterCall" w obiekcie ClientParameterInspector. typu "%1".|Rozwiązywanie problemów, ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Informacje|Dyspozytor wywołał metodę "BeforeCall" w obiekcie ClientParameterInspector typu "%1".|Rozwiązywanie problemów, ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Informacje|Obiekt OperationInvoker wywołał metodę "%1".|EndToEndMonitoring rozwiązywania problemów, ServiceModel|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Informacje|Dyspozytor wywołał obiekt ErrorHandler typu "%1" za pomocą wyjątku typu '%3'.  Obsłużony błąd == "%2".|Rozwiązywanie problemów, ServiceModel|  
|[207 — FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Informacje|Dyspozytor wywołał obiekt FaultProvider typu "%1" za pomocą wyjątku typu '%2'.|Rozwiązywanie problemów, ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Informacje|Dyspozytor wywołał "AfterReceiveReply" w obiekcie MessageInspector typu "%1".|Rozwiązywanie problemów, ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Informacje|Dyspozytor wywołał "BeforeSendRequest" w obiekcie MessageInspector typu "%1".|Rozwiązywanie problemów, ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Ostrzeżenie|Osiągnięto limit przepustnicy "%1" z "%2".|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Informacje|Dyspozytor wywołał metodę "AfterCall" w obiekcie ParameterInspector typu "%1".|Rozwiązywanie problemów, ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Informacje|Dyspozytor wywołał metodę "BeforeCall" w obiekcie ParameterInspector typu "%1".|Rozwiązywanie problemów, ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|Rozpoczęto ServiceHost: "%1".|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Informacje|Obiekt OperationInvoker ukończył wywołanie metody '%1'.  Wywołanie metody trwało "%2" ms.|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Informacje|Transportu odebrała wiadomość od "%1".|Rozwiązywanie problemów, ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Informacje|Transportu wysłała wiadomość do "%1".|Rozwiązywanie problemów, ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Informacje|Klient wykonuje operację "%1" zdefiniowana w kontrakcie "%2". Wiadomość zostanie wysłana do "%3".|Rozwiązywanie problemów, ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Informacje|Klient wykonał operacji "%1" zdefiniowanej w kontrakcie "%2". Wiadomość została wysłana do "%3".|Rozwiązywanie problemów, ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Błąd|Podczas przetwarzania komunikatu wystąpił nieobsługiwany wyjątek typu "%2".  ToString pełny wyjątek: %1.|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Informacje|Dyspozytor wysłał wiadomość do transportu. Identyfikator korelacji == "%1".|EndToEndMonitoring rozwiązywania problemów, ServiceModel|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Informacje|Dyspozytor odebrał wiadomość od transportu. Identyfikator korelacji == "%1".|EndToEndMonitoring rozwiązywania problemów, ServiceModel|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Ostrzeżenie|Metoda "%1" spowodowała zgłoszenie nieobsługiwanego wyjątku, gdy została wywołana przez obiekt OperationInvoker. Wywołanie metody trwało "%2" ms.|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Ostrzeżenie|Metoda "%1" spowodowała zgłoszenie wyjątku FaultException, gdy została wywołana przez obiekt OperationInvoker. Wywołanie metody trwało "%2" ms.|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Ostrzeżenie|Limit przepustnicy "%1" z "%2" wynosi 70%.|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|%1 nieaktywnych usług: poza całkowita %2 aktywowanych usług.|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Błąd|Nazwa: '%1', odwołania: "%2", ładunku: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Ostrzeżenie|Nazwa: '%1', odwołania: "%2", ładunku: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Informacje|Nazwa: '%1', odwołania: "%2", ładunku: %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|[401 — StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Informacje|Granica aktywności.|Rozwiązywanie problemów|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Informacje|Granica aktywności.|Rozwiązywanie problemów|  
|[403 — SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Informacje|Granica aktywności.|Rozwiązywanie problemów|  
|[404 — ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Informacje|Granica aktywności.|Rozwiązywanie problemów|  
|[451 — MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Informacje|%1|Rozwiązywanie problemów, WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Ostrzeżenie|%1|Rozwiązywanie problemów, WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|Zdarzenia transferu wysyłanego.|Rozwiązywanie problemów, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking ServiceHost, WCFMessageLogging|  
|[501 — CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Informacje|Rozpocznij kompilację.|WebHost|  
|[502 — CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Informacje|Zakończ kompilację.|WebHost|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Informacje|Elementu ServiceHostFactory Rozpocznij tworzenie.|WebHost|  
|[504 - ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Informacje|Tworzenie celu elementu ServiceHostFactory.|WebHost|  
|[505 — CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Informacje|Rozpocznij CreateServiceHost.|WebHost|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Informacje|CreateServiceHost zakończenia.|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Informacje|Inicjowania konfiguracji obiektu hostedtransportconfigurationmanager.|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Informacje|Zakończenie inicjowania konfiguracji obiektu HostedTransportConfigurationManager.|WebHost|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Informacje|Zakończenie inicjowania konfiguracji obiektu HostedTransportConfigurationManager.|Element ServiceHost|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Informacje|Otwórz ServiceHost ukończona.|Element ServiceHost|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Informacje|Odebrano żądanie za pośrednictwem ścieżki wirtualnej "%2" z domeny aplikacji "%1".|WebHost|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Informacje|Zatrzymaj WebHostRequest.|WebHost|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Pełny|Przetworzono adres względny elementu ServiceActivation: %1, znormalizowany adres względny "%2".||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Pełny|Żądanie przychodzące odpowiada elementowi serviceactivation o adresie "%1".||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Pełny|Żądanie przychodzące odpowiada usłudze WCF zdefiniowanej w trasie Asp.Net o adresie %1.|RoutingServices|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Pełny|Dodawany jest nową trasę Asp.Net "%1" o właściwości serviceType "%2" i właściwości serviceHostFactoryType "%3".|RoutingServices|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Pełny|Wywołuje się IncrementBusyCount. Źródło: %1|WebHost|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Pełny|Wywołuje się DecrementBusyCount. Źródło: %1|WebHost|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Pełny|Rozpoczęto ServiceChannelOpen.|WebHost|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Informacje|ServiceChannelOpen ukończone.|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Informacje|Rozpoczęto ServiceChannelCall.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Informacje|Asynchroniczne wywołania obiektu ServiceChannel uruchomiona.|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Pełny|Rozpoczęto wysyłanie żądania HTTP.|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Pełny|Zatrzymano wysyłanie żądania HTTP.|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Pełny|Odebrano komunikat z transportu http.|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Informacje|Podczas wysyłania wiadomości uruchomiona.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Pełny|Rozpocznij uwierzytelnianie na potrzeby rozsyłania komunikatów.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Pełny|Rozpocznij autoryzację na potrzeby rozsyłania komunikatów.|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Informacje|Potrzeby rozsyłania komunikatów zakończone.|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Informacje|Otwórz początek obiektu ServiceChannel.|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Informacje|Zatrzymaj Otwórz obiektu ServiceChannel.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Informacje|Http rozpoczęto wysyłanie strumieniowego komunikatu.|HTTP|  
|[1400 - limitu czasu ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Błąd|1%|ServiceModel|  
|[1401 - CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Błąd|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Błąd|%1 klucz puli połączeń: %2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Informacje|%1 klucz puli połączeń: %2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Błąd|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Błąd|%1|ServiceModel|  
|[1407 - właściwości SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Błąd|%1|ServiceModel|  
|[1409 - limit czasu nieaktywności](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Informacje|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Błąd|%1|limit przydziału|  
|[1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Błąd|%1|limit przydziału|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Informacje|%1|limit przydziału|  
|[1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Informacje|%1|limit przydziału|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Błąd|%1|limit przydziału|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Błąd|%1|limit przydziału|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Pełny|Współczynnik pamięci podręcznej stanów wystawcy uwierzytelnienia tokenu negocjowania: %1 / %2|limit przydziału|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Pełny|Współczynnik sesji zabezpieczeń: %1 / %2|limit przydziału|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Pełny|Współczynnik połączeń oczekujących: %1 / %2|limit przydziału|  
|[1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Pełny|Stosunek liczby równoczesnych sesji: %1 / %2|limit przydziału|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Pełny|Stosunek liczby równoczesnych sesji: %1 / %2|limit przydziału|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Pełny|Punkt końcowy współczynnik połączeń wychodzących na: %1 / %2|limit przydziału|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Pełny|Punkt końcowy współczynnik połączeń wychodzących na: %1 / %2|limit przydziału|  
|[1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Pełny|Kanał współczynnik komunikatów oczekujących na: %1 / %2|limit przydziału|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Pełny|Stosunek liczby równoczesnych wystąpień: %1 / %2|limit przydziału|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Informacje|Pozostało zero oczekujących akceptacji.|limit przydziału|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Ostrzeżenie|1%|limit przydziału|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Ostrzeżenie|Osiągnięto przy komunikacie usługi MSMQ o identyfikatorze "%1" liczbę ponownych prób odebrania|limit przydziału|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Błąd|Maksymalną liczbę cykli ponownych prób przekroczona przy komunikacie usługi MSMQ o identyfikatorze "%1"|limit przydziału|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Pełny|Tworzenia nowych '%1'|limit przydziału|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Pełny|Tworzenia nowych '%1'|limit przydziału|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Błąd|1%|limit przydziału|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Ostrzeżenie|Nie można ukończyć %1.|Kanał|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Ostrzeżenie|Nie powiodło się porzucenia %1.|Kanał|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Ostrzeżenie|Kontekstu odbierania wystąpił błąd.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Informacje|%1 został porzucony z powodu wyjątku %2.|Kanał|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Informacje|Liczba buforowanych fabryk kanałów: "%1".  Co najwyżej "%2" fabryk kanałów, które mogą być buforowane.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Informacje|Fabryka kanałów została usunięta z pamięci podręcznej, ponieważ pamięć podręczna osiągnęła swój limit równy "%1".|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Informacje|Użyto pasującej fabryki kanałów znalezionych w pamięci podręcznej.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Informacje|Nie jest używana fabryka kanałów z pamięci podręcznej, tj. że buforowanie jest wyłączne dla wystąpienia.|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Informacje|Składanie zapytania przy użyciu "%1" zostało wykonane na identyfikator Uri żądania: "%2".|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Błąd|Operacja "%1" została wysłana z błędami.|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Informacje|Operacja "%1" została wysłana pomyślnie.|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informacje|Koder odczytał komunikat o rozmiar w bajtach "%1".|Kanał|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Informacje|Komunikat o rozmiar w bajtach '%1' został napisany przez koder.|Kanał|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Błąd|Przerywanie sesji dla bezczynnego kanału do identyfikatora uri: "%1".|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Pełny|Rozpoczęto akceptowanie połączenia.|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Pełny|Socketid ListenerId:% 1 zaakceptowane 2.|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Pełny|Pula dla %1 nie ma dostępnych połączeń i %2 zajętych połączeń.|Kanał|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Pełny|Dyspozytor rozpoczął deserializację komunikatu żądania.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Pełny|Dyspozytor ukończył deserializację komunikatu żądania.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Pełny|Dyspozytor rozpoczął serializację komunikatu odpowiedzi.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Pełny|Dyspozytor ukończył serializację komunikatu odpowiedzi.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Pełny|Rozpoczęto serializację żądania klienta.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Pełny|Klient ukończył serializowanie komunikatu żądania.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Pełny|Klient rozpoczął deserializowanie komunikatu odpowiedzi.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Pełny|Klient ukończył deserializowanie komunikatu odpowiedzi.|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Pełny|Rozpoczęto negocjacji zabezpieczeń.|Zabezpieczenia|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Pełny|Ukończono negocjowanie zabezpieczeń.|Zabezpieczenia|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Pełny|Obiekt SecurityTokenProvider otwierania ukończone.|Zabezpieczenia|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Pełny|Komunikat wychodzący został zabezpieczony.|Zabezpieczenia|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Pełny|Zweryfikowano komunikat przychodzący.|Zabezpieczenia ServiceModel|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Pełny|Rozpoczęto pobieranie wystąpienia usługi.|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Pełny|Pobrać wystąpienia usługi.|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Pełny|Uruchomiono pętlę odbierania ChannelHandlerId:% 1 - wiadomości.|Kanał|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Pełny|Zatrzymano pętlę odbierania ChannelHandlerId:% 1 - wiadomości.|Kanał|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Pełny|Utworzony obiekt ChannelFactory.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Pełny|Akceptowanie połączenia potoku uruchomiony na komputerze %1.|Kanał|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Pełny|Połączenie z potokiem akceptowane.|Kanał|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Pełny|Rozpoczęto ustanawianie połączenia dla %1.|Kanał|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Pełny|Nawiązano połączenie.|Kanał|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Pełny|Rozumiem preambuły sesji dla "%1".|Kanał|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Błąd|Błąd '%1' wysyłania czytniku połączeń.|Kanał|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Pełny|Gniazda zaakceptować zamknięte.|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Krytyczny|Wystąpił błąd usługi hosta.|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Pełny|Odbiornik otwierania dla "%1".|Kanał|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Pełny|Otwórz odbiornika ukończone.|Kanał|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Pełny|Osiągnięto przydział maksymalnej liczby puli połączeń serwera.|limit przydziału|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Błąd|Socketid 1 do adresu zdalnego %2 został przekroczony.|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Ostrzeżenie|Socketid 1 do adresu zdalnego %2 wystąpił błąd zresetowania połączenia.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Pełny|Ukończono negocjowanie zabezpieczeń usługi.|Zabezpieczenia|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Błąd|Przetwarzanie negocjacji zabezpieczeń nie powiodło się.|Zabezpieczenia|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Pełny|Weryfikacja powiodła się.|Zabezpieczenia|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Błąd|Nie można zweryfikować zabezpieczeń.|Zabezpieczenia|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Pełny|Gniazda duplikowana dla %1.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Pełny|Personifikacja zabezpieczeń zakończyło się pomyślnie.|Zabezpieczenia|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Ostrzeżenie|Personifikacja zabezpieczeń nie powiodła się.|Zabezpieczenia|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Ostrzeżenie|Żądanie kanału HTTP zostało przerwane.|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Ostrzeżenie|Odpowiedź kanału HTTP została przerwana.|HTTP|  
|[3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Ostrzeżenie|Uwierzytelnianie HTTP nie powiodło się.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Pełny|Rozpoczęto rejestrację obiektu SharedListenerProxy dla identyfikatora uri "%1".|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Pełny|Zatrzymaj Register obiektu SharedListenerProxy.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Błąd|Metody register obiektu SharedListenerProxy nie powiodło się ze stanem "%1".|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Błąd|ConnectionPoolPreambleFailed.|Kanał|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Pełny|SslOnAcceptUpgradeStart|Zabezpieczenia|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Pełny|SslOnAcceptUpgradeStop|Zabezpieczenia|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Pełny|Obiekt BinaryMessageEncoder rozpoczął Kodowanie komunikatu.|Kanał|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Pełny|Obiekt MtomMessageEncoder rozpoczął Kodowanie komunikatu.|Kanał|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Pełny|Obiekt TextMessageEncoder rozpoczął Kodowanie komunikatu.|Kanał|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Pełny|Obiekt BinaryMessageEncoder rozpoczął dekodowanie komunikatu.|Kanał|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Pełny|Obiekt MtomMessageEncoder rozpoczął dekodowanie komunikatu.|Kanał|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Pełny|Obiekt TextMessageEncoder rozpoczął dekodowanie komunikatu.|Kanał|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Informacje|Http transport rozpoczął odbieranie komunikatu.|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Pełny|Bajty odczytu "%2" Socketid 1 odczytane z "%3".|TCP|  
|[3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Pełny|Bajty odczytu "%2" Socketid 1 odczytane z "%3".|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Pełny|Socketid 1 bajtów zapisu "%2" do "%3".|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Pełny|Socketid 1 bajtów zapisu "%2" do "%3".|TCP|  
|[3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Pełny|Wysyłane potwierdzenia SessionId:% 1.|Kanał|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Informacje|Ponowne łączenie SessionId:% 1.|Kanał|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Informacje|Wystąpił błąd SessionId:% 1.|Kanał|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Pełny|Obiekt WindowsStreamSecurity inicjuje uaktualnienie zabezpieczeń.|Zabezpieczenia|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Pełny|Przesyłania zabezpieczeń przy akceptowaniu uaktualnienia systemu Windows.|Zabezpieczenia|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Ostrzeżenie|Przerwanie Socketid 1.|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Pełny|Początek HttpGetContext.|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Pełny|Klient rozpoczął wysyłanie preambuły.|Kanał|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Pełny|Klient zatrzymał wysyłanie preambuły.|Kanał|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Ostrzeżenie|Odbieranie komunikatu HTTP nie powiodło się.|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Informacje|Utworzono element TransactionScope z właściwościami LocalIdentifier: "%1" i DistributedIdentifier: "%2".|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Informacje|Koder odczytał przesyłanej strumieniowo komunikat.|Kanał|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Informacje|Koder zapisał przesyłanej strumieniowo komunikat.|Kanał|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Informacje|Zapisano wiadomość asynchronicznie przez koder.|Kanał|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Informacje|Bajty Bufferid 1 Ukończono zapisywanie "%2" do źródłowego strumienia.|Kanał|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Informacje|Zapisano wiadomość asynchronicznie przez koder.|Kanał|  
|[3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Pełny|Przekaż w potoku pamięci współużytkowanej utworzony w '%1'.|Kanał|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Pełny|"%1" utworzył nazwany potok.|Kanał|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Pełny|Rozpoczęto weryfikacji podpisu.|Zabezpieczenia|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Pełny|Weryfikacja podpisu zakończyło się pomyślnie.|Zabezpieczenia|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Pełny|Opakowana Rozpoczęto odszyfrowywanie klucza.|Zabezpieczenia|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Pełny|Odszyfrowywanie klucza z otoką zakończyło się pomyślnie.|Zabezpieczenia|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Pełny|Rozpoczęto przetwarzanie zaszyfrowanych danych.|Zabezpieczenia|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Pełny|Przetwarzanie zaszyfrowanych danych zakończyło się pomyślnie.|Zabezpieczenia|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Pełny|Obsługa komunikatów HTTP rozpoczęła przetwarzanie żądania przychodzącego.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Pełny|Obsługa komunikatów HTTP rozpoczęła asynchroniczne przetwarzanie żądania przychodzącego.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Pełny|Obsługa komunikatów HTTP ukończyła przetwarzanie żądania przychodzącego.|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Ostrzeżenie|Obsługa komunikatów HTTP jest uszkodzona.|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Błąd|Upłynął limit czasu połączenia obiektu WebSocket.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Pełny|Obsługa komunikatów HTTP rozpoczęła przetwarzanie odpowiedzi.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Pełny|Obsługa komunikatów HTTP rozpoczęła asynchroniczne przetwarzanie odpowiedzi.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Pełny|Obsługa komunikatów HTTP ukończyła przetwarzanie odpowiedzi.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Pełny|Rozpoczęto wysyłanie żądania połączenia obiektu WebSocket do "%1".|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Pełny|Wysłane żądanie połączenia gniazda websocketid: % 1.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Pełny|Rozpoczęto akceptację połączenia obiektu WebSocket.|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Pełny|Zaakceptowano połączenia gniazda websocketid: % 1.|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Błąd|Połączenie obiektu WebSocket zostało odrzucone z kodem stanu "%1"|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Błąd|Żądanie połączenia obiektu WebSocket nie powiodło się: "%1"|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Błąd|Połączenie gniazda websocketid: % 1 zostało przerwane.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Pełny|Gniazda websocketid: % 1 bajtów zapisu "%2" do "%3".|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Pełny|Zatrzymaj zapis asynchroniczny gniazda websocketid: % 1.|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Pełny|Początek gniazda websocketid: % 1 do odczytu.|HTTP|  
|[3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Pełny|Gniazda websocketid: % 1 odczytu bajtów "%2" z "%3".|HTTP|  
|[3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Pełny|Gniazda websocketid: % 1 wysyła komunikat zamknięcia do "%2", używając stanu zamknięcia "%3".|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Pełny|Gniazda websocketid: % 1 wysyła komunikat zamknięcia wyjścia do "%2" używając stanu zamknięcia "%3".|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Pełny|Zamknięcie połączenia gniazda websocketid: % 1.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Pełny|Połączenie gniazda websocketid: % 1 odebrało komunikat zamknięcia ze stanu "%2".|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Pełny|Używanie wartości WebSocketVersion z fabryki obiektów WebSocket klienta typu "%1".|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Pełny|Tworzenie obiektu WebSocket klienta za pomocą fabryki typu "%1".|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Informacje|XamlServicesLoad start|WebHost|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Informacje|Zatrzymaj xamlServicesLoad|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Informacje|CreateWorkflowServiceHost start|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Informacje|Zatrzymaj CreateWorkflowServiceHost|WebHost|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Informacje|Uruchomienie usługi aktywacji|WebHost|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Informacje|Usługa aktywacji zatrzymania|WebHost|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Pełny|Dostępna pamięć (w bajtach): %1|limit przydziału|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Informacje|Usługa routingu zamyka klienta '%1'.|RoutingServices|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Ostrzeżenie|Wystąpił błąd klienta usługi routingu '%1'.|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Informacje|Kończy przetwarzanie komunikatu jeden sposób usługa routingu.|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Błąd|Usługa routingu nie powiodło się podczas przetwarzania komunikatu w punkcie końcowym o adresie "%1".|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Informacje|Usługa routingu tworzy klienta dla punktu końcowego: "%1".|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Pełny|Usługi routingu skonfigurowano RouteOnHeadersOnly: %1, SoapProcessingEnabled: %2, EnsureOrderedDispatch: %3.|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Informacje|Komunikat odpowiedzi na żądanie usługa routingu kończy przetwarzanie.|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Pełny|Usługa routingu skierowała komunikat o identyfikatorze: '%1' do %2 list punktów końcowych.|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Informacje|Usługa routingu zastosowaniu nową konfigurację.|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Informacje|Usługa routingu przetwarza komunikat o identyfikatorze: "%1", akcja: "%2", adres URL komunikatów przychodzących: '%3, odebrany w transakcji: %4.|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Informacje|Usługa routingu przesyła komunikat o identyfikatorze: "%1" [operacji %2], do "%3".|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Informacje|Usługa routingu przekazuje transakcję o identyfikatorze: "%1".|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Błąd|Składnik %1 usługi routingu napotkał wyjątek dwustronnego wywołania zwrotnego.|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Informacje|Komunikat usługi routingu o identyfikatorze: "%1" [operacji %2] przeniesiony do zapasowego punktu końcowego "%3".|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Informacje|Usługa routingu utworzyła nową transakcję o identyfikatorze "%1" na potrzeby przetwarzania komunikatów.|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Ostrzeżenie|Usługa routingu wystąpił błąd podczas zamykania klienta w ruchu wychodzącym '%1'.|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Informacje|Usługa routingu odsyła komunikat odpowiedzi z akcji "%1".|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Ostrzeżenie|Usługa routingu odsyła komunikat odpowiedzi Fault z akcją "%1".|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Pełny|Usługa routingu receivecontext.COMPLETE dla komunikatu o identyfikatorze: "%1".|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Ostrzeżenie|Usługa routingu receivecontext.Abandon dla komunikatu o identyfikatorze: "%1".|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Pełny|Usługa routingu wyśle komunikaty przy użyciu istniejącej transakcji "%1".|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Ostrzeżenie|Usługa routingu nie powiodło się podczas wysyłania do "%1".|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Informacje|Rozpoczęto dopasowywanie obiektu MessageFilterTable usługi routingu.|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Informacje|Zatrzymano dopasowywanie obiektu MessageFilterTable usługi routingu.|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Pełny|Usługa routingu wywołuje metodę abort w kanale: "%1".|RoutingServices|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Pełny|Usługa routingu obsłużyła wyjątek.|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Informacje|Usługa routingu pomyślnie przesłała wiadomość o identyfikatorze: "%1 [operacja: %2] do"%3".|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Pełny|Odebrano z za pośrednictwem "%1" sesję odbiornika transportu|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Krytyczny|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Błąd|Błąd potoku uruchamiania usług.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Pełny|Dystrybucja sesji jest uruchomiony.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Ostrzeżenie|Dystrybucja sesji dla "%1" nie powiodło się, ponieważ kolejka sesji oczekujących jest pełna z "%2" oczekujących elementów.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Pełny|Rozpoczęto rejestrowanie kolejki komunikatów.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Błąd|Przerwane ze stanem rejestracja kolejki komunikatów: "%1" dla identyfikatora uri: "%2".|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Pełny|Wyrejestrowywanie kolejki komunikatów zakończyło się pomyślnie dla identyfikatora uri: "%1".|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Błąd|Rejestracja kolejki komunikatów dla identyfikatora uri: "%1" nie powiodła się ze stanem: "%2".|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Informacje|Rejestracja kolejki komunikatów dla identyfikatora uri '%1' została zakończona.|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Błąd|Kolejka komunikatów nie może zduplikować gniazda.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Pełny|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Pełny|Odbiornik transportu TCP rozpoczął nasłuchiwanie na identyfikatorze uri: "%1".|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Pełny|Odbiornik transportu TCP wykonuje nasłuchiwanie.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Błąd|Kod błędu: % 1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Informacje|Zamykanie wszystkich wystąpień kanałów odbiornika ukończone usługi WAS.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Błąd|Kod błędu: % 1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Błąd|Kod błędu: % 1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Pełny|BYŁ połączony.|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Pełny|ZOSTAŁO rozłączone.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Pełny|Odbiornik transportu rozpoczął nasłuchiwanie na uri:% 1.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Pełny|Potok transportu odbiornika nasłuchiwanie.|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Informacje|Dystrybucja sesji zakończyło się pomyślnie.|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Błąd|Dystrybucja sesji nie powiodło się.|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Krytyczny|Połączenie upłynął limit czasu.|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Pełny|Rozpoczęto wyszukiwanie w tabeli routingu.|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Pełny|Ukończono wyszukiwanie w tabeli routingu.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Pełny|Współczynnik kolejki sesji oczekujących: %1 / %2|limit przydziału|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Ostrzeżenie|Nie można zarejestrować komunikatu, ponieważ jego rozmiar przekracza rozmiar zdarzenia ETW|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Ostrzeżenie|Obiektu DiscoveryClient utworzonego w obiekcie DiscoveryClientChannel nie można zamknąć i dlatego została przerwana.|Odnajdywanie|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Informacje|Pominięto wyjątek protokołu podczas zamykania obiektu DiscoveryClient. Może to być spowodowane obiekt DiscoveryService nadal próbuje wysłać odpowiedź do obiektu DiscoveryClient.|Odnajdywanie|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Informacje|Obiekt DiscoveryClient odebrał komunikat o pominięciu multiemisji z obiektu DiscoveryProxy.|Odnajdywanie|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Informacje|Komunikat %1 o atrybucie messageId = "%2" został porzucony przez obiekt DiscoveryClient, ponieważ odpowiadająca mu Operacja %3 została ukończona.|Odnajdywanie|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Ostrzeżenie|Komunikat %1 o atrybucie messageId = "%2" został porzucony, ponieważ miał nieprawidłową zawartość.|Odnajdywanie|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Ostrzeżenie|Komunikat %1 o atrybucie messageId = "%2" i relatesTo = '%3' został porzucony przez obiekt DiscoveryClient, ponieważ odpowiadająca mu operacja %4 została ukończona lub wartość atrybutu relatesTo była nieprawidłowa.|Odnajdywanie|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Ostrzeżenie|Komunikat z żądaniem odnajdowania o atrybucie messageId = "%1" został porzucony, ponieważ miał nieprawidłowy adres ReplyTo.|Odnajdywanie|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Ostrzeżenie|Komunikat %1 został porzucony, ponieważ nie ma żadnej zawartości.|Odnajdywanie|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Ostrzeżenie|Komunikat %1 został porzucony, ponieważ nagłówek komunikatu nie zawierał wymaganej właściwości MessageId.|Odnajdywanie|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Ostrzeżenie|Komunikat %1 o atrybucie messageId = "%2" został porzucony przez obiekt DiscoveryClient, ponieważ nie miał właściwości DiscoveryMessageSequence.|Odnajdywanie|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Ostrzeżenie|Komunikat %1 o atrybucie messageId = "%2" został porzucony przez obiekt DiscoveryClient, ponieważ nagłówek komunikatu nie zawierał wymaganej właściwości RelatesTo.|Odnajdywanie|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Ostrzeżenie|Komunikat z żądaniem odnajdowania o atrybucie messageId = "%1" został porzucony, ponieważ nie miał adresu ReplyTo.|Odnajdywanie|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Ostrzeżenie|Komunikat %1 o atrybucie messageId = "%2" został porzucony, ponieważ był duplikatem.|Odnajdywanie|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informacje|Możliwość odnajdowania punktu końcowego EndpointAddress o wartości "%1" i ListenUri o wartości = "%2" zostało wyłączone.|Odnajdywanie|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Informacje|Możliwość odnajdowania punktu końcowego EndpointAddress o wartości "%1" i ListenUri o wartości = "%2" został włączony.|Odnajdywanie|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Pełny|Operacja Find została zainicjowana w obiekcie DiscoveryClientChannel w celu odnalezienia punktów końcowych.|Odnajdywanie|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Ostrzeżenie|Obiekt DiscoveryClientChannel nie może utworzyć kanału z odnalezionym punktem końcowym, używając atrybutu EndpointAddress o = "%1" i Via o wartości "%2". Obiekt DiscoveryClientChannel podejmie teraz próbę użycia następnego dostępnego odnalezionego punktu końcowego.|Odnajdywanie|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Ostrzeżenie|Obiekt DiscoveryClientChannel nie można otworzyć kanału z odnalezionym punktem końcowym, używając atrybutu EndpointAddress o = "%1" i Via o wartości "%2". Obiekt DiscoveryClientChannel podejmie teraz próbę użycia następnego dostępnego odnalezionego punktu końcowego.|Odnajdywanie|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Informacje|Obiekt DiscoveryClientChannel pomyślnie odnalazł punkt końcowy i otworzył kanał z użyciem jej. Klient jest połączony z usługą przy użyciu parametrów EndpointAddress = "%1" i Via o wartości "%2".|Odnajdywanie|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Informacje|Obiekt DiscoveryClientChannel zresetowano obiektu SynchronizationContext to oryginalnej wartości %1.|Odnajdywanie|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Informacje|Obiektu SynchronizationContext została ustawiona na wartość null w obiekcie DiscoveryClientChannel przed zainicjowaniem operacji Find.|Odnajdywanie|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Pełny|Serializacja obiektu DataContract %1 z surogatami została rozpoczęta.|Serializacja|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Pełny|Serializacja obiektu DataContract z elementami zastępczymi została zatrzymana.|Serializacja|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Pełny|Deserializacja obiektu DataContract %1 z surogatami została rozpoczęta.|Serializacja|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Pełny|Deserializacja obiektu DataContract z elementami zastępczymi została zatrzymana.|Serializacja|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Pełny|Początek ImportKnownTypes.|Serializacja|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Pełny|Zatrzymaj ImportKnownTypes.|Serializacja|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Pełny|Program rozpoznawania obiektów DataContract rozpoznawanie %1 rozpoczęcia.|Serializacja|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Pełny|Generowanie obiektu DataContract — składnik zapisywania %1 dla %2 rozpoczęcia.|Serializacja|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Pełny|Generowanie obiektu DataContract zatrzymania składnika zapisywania.|Serializacja|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Pełny|Generowanie obiektu DataContract — czytnik %1 dla %2 rozpoczęcia.|Serializacja|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Pełny|Zatrzymaj generowanie obiektu DataContract.|Serializacja|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Pełny|Generowanie obiektu JSON czytnik %1 dla %2 rozpoczęcia.|Serializacja|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Pełny|Zatrzymaj generowania czytnika JSON.|Serializacja|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Pełny|Składnik zapisywania %1 dla %2 start generowanie obiektu JSON.|Serializacja|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Pełny|Generowanie obiektu JSON zatrzymania składnika zapisywania.|Serializacja|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Pełny|Generowanie kodu Xml, które można serializować rozpoczęcia '%1'.|Serializacja|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Pełny|Generowanie zostało zatrzymane do serializacji Xml.|Serializacja|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Pełny|Obiekt JsonMessageEncoder rozpoczął dekodowanie komunikatu.|Kanał|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Pełny|Obiekt JsonMessageEncoder rozpoczął Kodowanie komunikatu.|Kanał|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Pełny|Rozpoczęto weryfikację SecurityToken (typu '%1' i identyfikatorze "%2").|Zabezpieczenia|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Pełny|Pomyślnie zweryfikowano SecurityToken (typu '%1' i identyfikatorze "%2").|Zabezpieczenia|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Błąd|Nie można zweryfikować SecurityToken (typu '%1' i identyfikatorze "%2"). %3|Zabezpieczenia|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Pełny|Pobieranie wystawcy Nazwa: % 1 z obiektu tokenid: % 2 zakończyło się pomyślnie.|Zabezpieczenia|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Błąd|Pobieranie nazwy wystawcy z obiektu tokenid: % 1 nie powiodło się.|Zabezpieczenia|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Pełny|Rozpoczęto przetwarzanie komunikatu federacyjnego.|Zabezpieczenia|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Pełny|Przetwarzanie komunikatu federacyjnego zakończyło się pomyślnie.|Zabezpieczenia|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Pełny|Rozpoczęto tworzenie komunikatu federacyjnego na podstawie post formularza.|Zabezpieczenia|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Pełny|Tworzenie komunikatu federacyjnego na podstawie post formularza zakończyło się pomyślnie.|Zabezpieczenia|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Pełny|Rozpoczęto odczytywanie tokenu sesji z pliku cookie sesji.|Zabezpieczenia|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Pełny|Odczytywanie tokenu sesji z pliku cookie sesji zakończyło się pomyślnie.|Zabezpieczenia|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Pełny|Ustawianie podmiotu zabezpieczeń na podstawie tokenu sesji uruchomiona.|Zabezpieczenia|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Pełny|Ustawienie podmiotu zabezpieczeń z tokenu sesji zakończyło się pomyślnie.|Zabezpieczenia|  
|[57393 - appDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Informacje|Zwalnianie elementu AppDomain. AppDomain.FriendlyName %1, ProcessName %2, identyfikator procesu %3.|Infrastruktura|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Informacje|Obsługa wyjątku.|Infrastruktura|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Błąd|Wystąpił nieoczekiwany błąd. Aplikacje nie powinny podejmować próby obsługi tego błędu. W celach diagnostycznych jest skojarzony z awarią ten komunikat w języku angielskim: %1.|Infrastruktura|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Ostrzeżenie|Zgłaszanie wyjątku. Źródło %1.|Infrastruktura|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Krytyczny|Nieobsługiwany wyjątek.|Infrastruktura|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Krytyczny|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Błąd|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Informacje|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Pełny|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Ostrzeżenie|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Ostrzeżenie|Obsługa wyjątku.|Infrastruktura|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Informacje|Adres url '%1' jest obsługiwany dokument XAML z elementem głównym typu "%2". Typ obsługi protokołu HTTP "%3" jest wybierany do obsługi wszystkich żądań kierowanych do tego adresu url.|WebHost|
