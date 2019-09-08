---
title: Odwołanie do zdarzenia śledzenia analitycznego
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 1b44e6b0abf0fc48b43ae17cbd24780e46ae518d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798126"
---
# <a name="analytic-trace-event-reference"></a>Odwołanie do zdarzenia śledzenia analitycznego
Poniższa tabela zawiera definicje poziomów zdarzeń, identyfikatorów i komunikatów skojarzonych ze śledzeniem analitycznym WCF.  
  
## <a name="event-reference"></a>Odwołanie do zdarzenia  
  
|Identyfikator zdarzenia|Poziom zdarzenia|Komunikat zdarzenia|słowa kluczowe|  
|--------------|-----------------|-------------------|--------------|  
|[131 — BufferPoolAllocation](131-bufferpoolallocation.md)|Pełny|Pula przydziela liczbę bajtów (% 1).|Infrastruktura|  
|[132 — BufferPoolChangeQuota](132-bufferpoolchangequota.md)|Pełny|Puli buforów rozmiaru% 1, zmiana przydziału przez% 2.|Infrastruktura|  
|[133 — ActionItemScheduled](133-actionitemscheduled.md)|Pełny|Wywołano wywołanie zwrotne harmonogramu wątków we/wy.|Infrastruktura|  
|[134 — ActionItemCallbackInvoked](134-actionitemcallbackinvoked.md)|Pełny|Wywołano wywołanie zwrotne harmonogramu wątków we/wy.|Infrastruktura|  
|[201 — ClientMessageInspectorAfterReceiveInvoked](201-clientmessageinspectorafterreceiveinvoked.md)|Informacje|Dyspozytor wywołał element "AfterReceiveReply" na ClientMessageInspector typu "% 1".|Rozwiązywanie problemów, ServiceModel|  
|[202 — ClientMessageInspectorBeforeSendInvoked](202-clientmessageinspectorbeforesendinvoked.md)|Informacje|Dyspozytor wywołał element "BeforeSendRequest" na ClientMessageInspector typu "% 1".|Rozwiązywanie problemów, ServiceModel|  
|[203 — ClientParameterInspectorAfterCallInvoked](203-clientparameterinspectoraftercallinvoked.md)|Informacje|Dyspozytor wywołał element "AfterCall" w ClientParameterInspector. typu '% 1 '.|Rozwiązywanie problemów, ServiceModel|  
|[204 — ClientParameterInspectorBeforeCallInvoked](204-clientparameterinspectorbeforecallinvoked.md)|Informacje|Dyspozytor wywołał element "BeforeCall" na ClientParameterInspector typu "% 1".|Rozwiązywanie problemów, ServiceModel|  
|[205 — OperationInvoked](205-operationinvoked.md)|Informacje|OperationInvoker wywołała metodę '% 1 '.|EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[206 — ErrorHandlerInvoked](206-errorhandlerinvoked.md)|Informacje|Dyspozytor wywołał ErrorHandler typu '% 1 ' z wyjątkiem typu '% 3 '.  ErrorHandled = = '% 2 '.|Rozwiązywanie problemów, ServiceModel|  
|[207 — FaultProviderInvoked](207-faultproviderinvoked.md)|Informacje|Dyspozytor wywołał wywołał obiekt faultprovider typu '% 1 ' z wyjątkiem typu '% 2 '.|Rozwiązywanie problemów, ServiceModel|  
|[208 — MessageInspectorAfterReceiveInvoked](208-messageinspectorafterreceiveinvoked.md)|Informacje|Dyspozytor wywołał element "AfterReceiveReply" na MessageInspector typu "% 1".|Rozwiązywanie problemów, ServiceModel|  
|[209 — MessageInspectorBeforeSendInvoked](209-messageinspectorbeforesendinvoked.md)|Informacje|Dyspozytor wywołał element "BeforeSendRequest" na MessageInspector typu "% 1".|Rozwiązywanie problemów, ServiceModel|  
|[210 — MessageThrottleExceeded](210-messagethrottleexceeded.md)|Ostrzeżenie|Osiągnięto limit przepustnicy "% 1" wynoszący "% 2".|HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[211 — ParameterInspectorAfterCallInvoked](211-parameterinspectoraftercallinvoked.md)|Informacje|Dyspozytor wywołał element "AfterCall" na ParameterInspector typu "% 1".|Rozwiązywanie problemów, ServiceModel|  
|[212 — ParameterInspectorBeforeCallInvoked](212-parameterinspectorbeforecallinvoked.md)|Informacje|Dyspozytor wywołał element "BeforeCall" na ParameterInspector typu "% 1".|Rozwiązywanie problemów, ServiceModel|  
|[213 — ServiceHostStarted](213-servicehoststarted.md)|LogAlways|Uruchomiono ServiceHost: '% 1 '.|HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[214 — OperationCompleted](214-operationcompleted.md)|Informacje|OperationInvoker ukończył wywołanie metody "% 1".  Czas trwania wywołania metody to "% 2" MS.|HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[215 — MessageReceivedByTransport](215-messagereceivedbytransport.md)|Informacje|Transport odebrał komunikat z '% 1 '.|Rozwiązywanie problemów, ServiceModel|  
|[216 — MessageSentByTransport](216-messagesentbytransport.md)|Informacje|Transport wysłał komunikat do "% 1".|Rozwiązywanie problemów, ServiceModel|  
|[217 — ClientOperationPrepared](217-clientoperationprepared.md)|Informacje|Klient wykonuje operację "% 1" zdefiniowaną w kontrakcie "% 2". Komunikat zostanie wysłany do "% 3".|Rozwiązywanie problemów, ServiceModel|  
|[218 — ClientOperationCompleted](218-clientoperationcompleted.md)|Informacje|Klient zakończył wykonywanie operacji "% 1" zdefiniowanej w kontrakcie "% 2". Wiadomość została wysłana do '% 3 '.|Rozwiązywanie problemów, ServiceModel|  
|[219 — ServiceException](219-serviceexception.md)|Błąd|Podczas przetwarzania komunikatu Wystąpił nieobsługiwany wyjątek typu "% 2".  Pełny wyjątek ToString:% 1.|HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[220 — MessageSentToTransport](220-messagesenttotransport.md)|Informacje|Dyspozytor wysłał komunikat do transportu. Identyfikator korelacji = = '% 1 '.|EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[221 — MessageReceivedFromTransport](221-messagereceivedfromtransport.md)|Informacje|Dyspozytor odebrał komunikat z transportu. Identyfikator korelacji = = '% 1 '.|EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[222 — OperationFailed](222-operationfailed.md)|Ostrzeżenie|Metoda "% 1" zgłosiła nieobsługiwany wyjątek podczas wywoływania przez OperationInvoker. Czas trwania wywołania metody to "% 2" MS.|HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[223 — OperationFaulted](223-operationfaulted.md)|Ostrzeżenie|Metoda "% 1" zgłosiła wyjątek FaultException w przypadku wywołania przez OperationInvoker. Czas trwania wywołania metody to "% 2" MS.|HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[224 — MessageThrottleAtSeventyPercent](224-messagethrottleatseventypercent.md)|Ostrzeżenie|Limit przepustnicy "% 1" wynoszący "% 2" wynosi 70%.|HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[226 — IdleServicesClosed](226-idleservicesclosed.md)|LogAlways|% 1 bezczynnych usług z łącznej liczby aktywowanych usług% 2.|HealthMonitoring WebHost|  
|[301 — UserDefinedErrorOccurred](301-userdefinederroroccurred.md)|Błąd|Nazwa: '% 1 ', odwołanie: '% 2 ', ładunek:% 3.|UserEvents, HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[302 — UserDefinedWarningOccurred](302-userdefinedwarningoccurred.md)|Ostrzeżenie|Nazwa: '% 1 ', odwołanie: '% 2 ', ładunek:% 3.|UserEvents, HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[303 — UserDefinedInformationEventOccured](303-userdefinedinformationeventoccured.md)|Informacje|Nazwa: '% 1 ', odwołanie: '% 2 ', ładunek:% 3.|UserEvents, HealthMonitoring, EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|[401— StopSignPostEvent](401-stopsignpostevent.md)|Informacje|Granica działania.|Rozwiązywanie problemów|  
|[402 — StartSignpostEvent](402-startsignpostevent.md)|Informacje|Granica działania.|Rozwiązywanie problemów|  
|[403 — SuspendSignpostEvent](403-suspendsignpostevent.md)|Informacje|Granica działania.|Rozwiązywanie problemów|  
|[404 — ResumeSignpostEvent](404-resumesignpostevent.md)|Informacje|Granica działania.|Rozwiązywanie problemów|  
|[451 — MessageLogInfo](451-messageloginfo.md)|Informacje|%1|Rozwiązywanie problemów, WCFMessageLogging|  
|[452 — MessageLogWarning](452-messagelogwarning.md)|Ostrzeżenie|%1|Rozwiązywanie problemów, WCFMessageLogging|  
|[499 — TransferEmitted](499-transferemitted.md)|LogAlways|Wyemitowano zdarzenie transferu.|Rozwiązywanie problemów, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 — CompilationStart](501-compilationstart.md)|Informacje|Rozpocznij kompilację.|WebHost|  
|[502 — CompilationStop](502-compilationstop.md)|Informacje|Zakończ kompilację.|WebHost|  
|[503 — ServiceHostFactoryCreationStart](503-servicehostfactorycreationstart.md)|Informacje|Obiektu ServiceHostFactory Rozpocznij tworzenie.|WebHost|  
|[504 — ServiceHostFactoryCreationStop](504-servicehostfactorycreationstop.md)|Informacje|Obiektu ServiceHostFactory.|WebHost|  
|[505 — CreateServiceHostStart](505-createservicehoststart.md)|Informacje|Rozpocznij wykonywania metody CreateServiceHost.|WebHost|  
|[506 — CreateServiceHostStop](506-createservicehoststop.md)|Informacje|Zakończ wykonywania metody CreateServiceHost.|WebHost|  
|[507 — HostedTransportConfigurationManagerConfigInitStart](507-hostedtransportconfigurationmanagerconfiginitstart.md)|Informacje|Obiektu hostedtransportconfigurationmanager rozpoczęcie inicjowania konfiguracji.|WebHost|  
|[508 — HostedTransportConfigurationManagerConfigInitStop](508-hostedtransportconfigurationmanagerconfiginitstop.md)|Informacje|Inicjalizacja konfiguracji końca obiektu hostedtransportconfigurationmanager.|WebHost|  
|[509 — ServiceHostOpenStart](509-servicehostopenstart.md)|Informacje|Inicjalizacja konfiguracji końca obiektu hostedtransportconfigurationmanager.|ServiceHost|  
|[510 — ServiceHostOpenStop](510-servicehostopenstop.md)|Informacje|Ukończono otwieranie ServiceHost.|ServiceHost|  
|[513 — WebHostRequestStart](513-webhostrequeststart.md)|Informacje|Odebrano żądanie ze ścieżką wirtualną "% 2" z domeny aplikacji "% 1".|WebHost|  
|[514 — WebHostRequestStop](514-webhostrequeststop.md)|Informacje|WebHostRequest.|WebHost|  
|[601 — CBAEntryRead](601-cbaentryread.md)|Pełny|Przetworzono adres względny elementu serviceactivation: "% 1", znormalizowany adres względny "% 2".||  
|[602 — CBAMatchFound](602-cbamatchfound.md)|Pełny|Żądanie przychodzące jest zgodne z elementem serviceactivation o adresie "% 1".||  
|[603 — AspNetRoutingService](603-aspnetroutingservice.md)|Pełny|Żądanie przychodzące jest zgodne z usługą WCF zdefiniowaną w marszrucie Asp.Net o adresie% 1.|RoutingServices|  
|[604 — AspNetRoute](604-aspnetroute.md)|Pełny|Dodano nową trasę Asp.Net '% 1 ' z ServiceType '% 2 ' i właściwości servicehostfactorytype '% 3 '.|RoutingServices|  
|[605 — IncrementBusyCount](605-incrementbusycount.md)|Pełny|IncrementBusyCount. Źródło:% 1|WebHost|  
|[606 — DecrementBusyCount](606-decrementbusycount.md)|Pełny|DecrementBusyCount. Źródło:% 1|WebHost|  
|[701 — ServiceChannelOpenStart](701-servicechannelopenstart.md)|Pełny|ServiceChannelOpen uruchomiono.|WebHost|  
|[702 — ServiceChannelOpenStop](702-servicechannelopenstop.md)|Informacje|Ukończono ServiceChannelOpen.|Modelu|  
|[703 — ServiceChannelCallStart](703-servicechannelcallstart.md)|Informacje|ServiceChannelCall uruchomiono.|Modelu|  
|[704 — ServiceChannelBeginCallStart](704-servicechannelbegincallstart.md)|Informacje|Rozpoczęto asynchroniczne wywołania ServiceChannel.|Modelu|  
|[706 — HttpSendMessageStart](706-httpsendmessagestart.md)|Pełny|Rozpoczęto wysyłanie żądania HTTP.|HTTP|  
|[707 — HttpSendStop](707-httpsendstop.md)|Pełny|Zatrzymano żądanie wysłania http.|HTTP|  
|[708 — HttpMessageReceiveStart](708-httpmessagereceivestart.md)|Pełny|Odebrano komunikat z transportu HTTP.|HTTP|  
|[709 — DispatchMessageStart](709-dispatchmessagestart.md)|Informacje|Rozpoczęto wysyłanie komunikatów.|Modelu|  
|[710 — HttpContextBeforeProcessAuthentication](710-httpcontextbeforeprocessauthentication.md)|Pełny|Rozpocznij uwierzytelnianie na potrzeby wysyłania komunikatów.|Modelu|  
|[711 — DispatchMessageBeforeAuthorization](711-dispatchmessagebeforeauthorization.md)|Pełny|Rozpocznij autoryzację na potrzeby wysyłania komunikatów.|Modelu|  
|[712 — DispatchMessageStop](712-dispatchmessagestop.md)|Informacje|Ukończono rozsyłanie komunikatów.|Modelu|  
|[715 — ClientChannelOpenStart](715-clientchannelopenstart.md)|Informacje|Otwarty Start ServiceChannel.|Modelu|  
|[716 — ClientChannelOpenStop](716-clientchannelopenstop.md)|Informacje|Zatrzymywanie otwierania ServiceChannel.|Modelu|  
|[717 — HttpSendStreamedMessageStart](717-httpsendstreamedmessagestart.md)|Informacje|Rozpoczęto wysyłanie przesyłanego strumieniowo komunikatów http.|HTTP|  
|[1400 — ChannelInitializationTimeout](1400-channelinitializationtimeout.md)|Błąd|1%|Modelu|  
|[1401 — CloseTimeout](1401-closetimeout.md)|Błąd|1%|Modelu|  
|[1402 — IdleTimeout](1402-idletimeout.md)|Błąd|% 1 klucz puli połączeń:% 2|Modelu|  
|[1403 — LeaseTimeout](1403-leasetimeout.md)|Informacje|% 1 klucz puli połączeń:% 2|Modelu|  
|[1405 — OpenTimeout](1405-opentimeout.md)|Błąd|%1|Modelu|  
|[1406 — ReceiveTimeout](1406-receivetimeout.md)|Błąd|%1|Modelu|  
|[1407 — SendTimeout](1407-sendtimeout.md)|Błąd|%1|Modelu|  
|[1409 — InactivityTimeout](1409-inactivitytimeout.md)|Informacje|%1|Modelu|  
|[1416 — MaxReceivedMessageSizeExceeded](1416-maxreceivedmessagesizeexceeded.md)|Błąd|%1|Działa|  
|[1417 — MaxSentMessageSizeExceeded](1417-maxsentmessagesizeexceeded.md)|Błąd|%1|Działa|  
|[1418 — MaxOutboundConnectionsPerEndpointExceeded](1418-maxoutboundconnectionsperendpointexceeded.md)|Informacje|%1|Działa|  
|[1419 — MaxPendingConnectionsExceeded](1419-maxpendingconnectionsexceeded.md)|Informacje|%1|Działa|  
|[1420 — ReaderQuotaExceeded](1420-readerquotaexceeded.md)|Błąd|%1|Działa|  
|[1422 — NegotiateTokenAuthenticatorStateCacheExceeded](1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Błąd|%1|Działa|  
|[1423 — NegotiateTokenAuthenticatorStateCacheRatio](1423-negotiatetokenauthenticatorstatecacheratio.md)|Pełny|Współczynnik pamięci podręcznej stanu wystawcy negocjowania tokenu:% 1/% 2|Działa|  
|[1424 — SecuritySessionRatio](1424-securitysessionratio.md)|Pełny|Współczynnik sesji zabezpieczeń:% 1/% 2|Działa|  
|[1430 — PendingConnectionsRatio](1430-pendingconnectionsratio.md)|Pełny|Współczynnik oczekujących połączeń:% 1/% 2|Działa|  
|[1431 — ConcurrentCallsRatio](1431-concurrentcallsratio.md)|Pełny|Współczynnik współbieżnych sesji:% 1/% 2|Działa|  
|[1432 — ConcurrentSessionsRatio](1432-concurrentsessionsratio.md)|Pełny|Współczynnik współbieżnych sesji:% 1/% 2|Działa|  
|[1433 — OutboundConnectionsPerEndpointRatio](1433-outboundconnectionsperendpointratio.md)|Pełny|Współczynnik połączeń wychodzących na punkt końcowy:% 1/% 2|Działa|  
|[1436 — PendingMessagesPerChannelRatio](1436-pendingmessagesperchannelratio.md)|Pełny|Współczynnik komunikatów oczekujących na kanał:% 1/% 2|Działa|  
|[1438 — ConcurrentInstancesRatio](1438-concurrentinstancesratio.md)|Pełny|Współczynnik współbieżnych wystąpień:% 1/% 2|Działa|  
|[1439 — PendingAcceptsAtZero](1439-pendingacceptsatzero.md)|Informacje|Brak oczekujących zaakceptowanych od zera|Działa|  
|[1441 — MaxSessionSizeReached](1441-maxsessionsizereached.md)|Ostrzeżenie|1%|Działa|  
|[1442 — ReceiveRetryCountReached](1442-receiveretrycountreached.md)|Ostrzeżenie|Osiągnięto liczbę ponownych prób odebrania komunikatu MSMQ o identyfikatorze "% 1"|Działa|  
|[1443 — MaxRetryCyclesExceededMsmq](1443-maxretrycyclesexceededmsmq.md)|Błąd|Przekroczono maksymalną liczbę cykli ponawiania prób w wiadomości MSMQ o identyfikatorze "% 1".|Działa|  
|[1445 — ReadPoolMiss](1445-readpoolmiss.md)|Pełny|Utworzono nowy element "% 1"|Działa|  
|[1446 — WritePoolMiss](1446-writepoolmiss.md)|Pełny|Utworzono nowy element "% 1"|Działa|  
|[1451 — MaxRetryCyclesExceeded](1451-maxretrycyclesexceeded.md)|Błąd|1%|Działa|  
|[3300 — ReceiveContextCompleteFailed](3300-receivecontextcompletefailed.md)|Ostrzeżenie|Nie można ukończyć% 1.|Ukierunkowan|  
|[3301 — ReceiveContextAbandonFailed](3301-receivecontextabandonfailed.md)|Ostrzeżenie|Nie można porzucić% 1.|Ukierunkowan|  
|[3303 — ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|Ostrzeżenie|Odbieranie kontekstu nie powiodło się.|Modelu|  
|[3303 — ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|Informacje|% 1 został porzucony z wyjątkiem% 2.|Ukierunkowan|  
|[3305 — ClientBaseCachedChannelFactoryCount](3305-clientbasecachedchannelfactorycount.md)|Informacje|Liczba fabryk kanałów w pamięci podręcznej: '% 1 '.  Maksymalna liczba fabryk kanałów w pamięci podręcznej to "% 2".|Modelu|  
|[3306 — ClientBaseChannelFactoryAgedOutofCache](3306-clientbasechannelfactoryagedoutofcache.md)|Informacje|Fabryka kanałów została już przestarzała z pamięci podręcznej, ponieważ pamięć podręczna osiągnęła swój limit równy "% 1".|Modelu|  
|[3307 — ClientBaseChannelFactoryCacheHit](3307-clientbasechannelfactorycachehit.md)|Informacje|Znaleziono pasującą fabrykę kanału w pamięci podręcznej.|Modelu|  
|[3308 — ClientBaseUsingLocalChannelFactory](3308-clientbaseusinglocalchannelfactory.md)|Informacje|Nie jest używana Fabryka kanałów z pamięci podręcznej, tj. Buforowanie wyłączone na przykład.|Modelu|  
|[3309 — QueryCompositionExecuted](3309-querycompositionexecuted.md)|Informacje|Składanie zapytania przy użyciu '% 1 ' zostało wykonane na identyfikatorze URI żądania: '% 2 '.|Modelu|  
|[3310 — DispatchFailed](3310-dispatchfailed.md)|Błąd|Operacja "% 1" została wysłana z błędami.|Modelu|  
|[3311 — DispatchSuccessful](3311-dispatchsuccessful.md)|Informacje|Operacja "% 1" została wysłana pomyślnie.|Modelu|  
|[3312 — MessageReadByEncoder](3312-messagereadbyencoder.md)|Informacje|Koder odczytał komunikat o rozmiarze% 1 b.|Ukierunkowan|  
|[3312 — MessageReadByEncoder](3312-messagereadbyencoder.md)|Informacje|Koder zapisał komunikat o rozmiarze% 1 b.|Ukierunkowan|  
|[3314 — SessionIdleTimeout](3314-sessionidletimeout.md)|Błąd|Przerywanie sesji dla bezczynnego kanału do identyfikatora URI: '% 1 '.|Modelu|  
|[3319 — SocketAcceptEnqueued](3319-socketacceptenqueued.md)|Pełny|Rozpoczęto akceptowanie połączenia.|TCP|  
|[3320 — SocketAccepted](3320-socketaccepted.md)|Pełny|Odbiornik listenerid:% 1 zaakceptował gniazdo socketid:% 2.|TCP|  
|[3321 — ConnectionPoolMiss](3321-connectionpoolmiss.md)|Pełny|Pula dla% 1 nie ma dostępnego połączenia i% 2 zajętych połączeń.|Ukierunkowan|  
|[3322 — DispatchFormatterDeserializeRequestStart](3322-dispatchformatterdeserializerequeststart.md)|Pełny|Dyspozytor rozpoczął deserializacja komunikatu żądania.|Modelu|  
|[3323 — DispatchFormatterDeserializeRequestStop](3323-dispatchformatterdeserializerequeststop.md)|Pełny|Dyspozytor ukończył deserializowanie komunikatu żądania.|Modelu|  
|[3324 — DispatchFormatterSerializeReplyStart](3324-dispatchformatterserializereplystart.md)|Pełny|Dyspozytor rozpoczął serializację komunikatu odpowiedzi.|Modelu|  
|[3325 — DispatchFormatterSerializeReplyStop](3325-dispatchformatterserializereplystop.md)|Pełny|Dyspozytor ukończył serializację komunikatu odpowiedzi.|Modelu|  
|[3326 — ClientFormatterSerializeRequestStart](3326-clientformatterserializerequeststart.md)|Pełny|Rozpoczęto serializację żądania klienta.|Modelu|  
|[3327 — ClientFormatterSerializeRequestStop](3327-clientformatterserializerequeststop.md)|Pełny|Klient ukończył serializację komunikatu żądania.|Modelu|  
|[3328 — ClientFormatterDeserializeReplyStart](3328-clientformatterdeserializereplystart.md)|Pełny|Klient rozpoczął deserializowanie komunikatu odpowiedzi.|Modelu|  
|[3329 — ClientFormatterDeserializeReplyStop](3329-clientformatterdeserializereplystop.md)|Pełny|Klient ukończył deserializowanie komunikatu odpowiedzi.|Modelu|  
|[3330 — SecurityNegotiationStart](3330-securitynegotiationstart.md)|Pełny|Rozpoczęto negocjowanie zabezpieczeń.|Zabezpieczenia|  
|[3331 — SecurityNegotiationStop](3331-securitynegotiationstop.md)|Pełny|Ukończono negocjowanie zabezpieczeń.|Zabezpieczenia|  
|[3332 — SecurityTokenProviderOpened](3332-securitytokenprovideropened.md)|Pełny|Ukończono otwieranie SecurityTokenProvider.|Zabezpieczenia|  
|[3333 — OutgoingMessageSecured](3333-outgoingmessagesecured.md)|Pełny|Komunikat wychodzący został zabezpieczony.|Zabezpieczenia|  
|[3334 — IncomingMessageVerified](3334-incomingmessageverified.md)|Pełny|Zweryfikowano komunikat przychodzący.|Security ServiceModel|  
|[3335 — GetServiceInstanceStart](3335-getserviceinstancestart.md)|Pełny|Rozpoczęto pobieranie wystąpienia usługi.|Modelu|  
|[3336 — GetServiceInstanceStop](3336-getserviceinstancestop.md)|Pełny|Pobrano wystąpienie usługi.|Modelu|  
|[3337 — ChannelReceiveStart](3337-channelreceivestart.md)|Pełny|ChannelHandlerId:% 1 — uruchomiono pętlę odbierania komunikatów.|Ukierunkowan|  
|[3338 — ChannelReceiveStop](3338-channelreceivestop.md)|Pełny|ChannelHandlerId:% 1 — zatrzymano pętlę odbierania komunikatów.|Ukierunkowan|  
|[3339 — ChannelFactoryCreated](3339-channelfactorycreated.md)|Pełny|Utworzono obiekt ChannelFactory.|Modelu|  
|[3340 — PipeConnectionAcceptStart](3340-pipeconnectionacceptstart.md)|Pełny|Rozpoczęto akceptowanie połączenia potoku w% 1.|Ukierunkowan|  
|[3341 — PipeConnectionAcceptStop](3341-pipeconnectionacceptstop.md)|Pełny|Połączenie potoku zostało zaakceptowane.|Ukierunkowan|  
|[3342 — EstablishConnectionStart](3342-establishconnectionstart.md)|Pełny|Rozpoczęto ustanawianie połączenia dla% 1.|Ukierunkowan|  
|[3343 — EstablishConnectionStop](3343-establishconnectionstop.md)|Pełny|Nawiązano połączenie.|Ukierunkowan|  
|[3345 — SessionPreambleUnderstood](3345-sessionpreambleunderstood.md)|Pełny|Nazwa preambuły sesji dla '% 1 ' została rozpoznana.|Ukierunkowan|  
|[3346 — ConnectionReaderSendFault](3346-connectionreadersendfault.md)|Błąd|Wystąpił błąd podczas wysyłania czytnika połączeń '% 1 '.|Ukierunkowan|  
|[3347 — SocketAcceptClosed](3347-socketacceptclosed.md)|Pełny|Zamknął zaakceptowanie gniazda.|TCP|  
|[3348 — ServiceHostFaulted](3348-servicehostfaulted.md)|Krytyczny|Błąd hosta usługi.|TCP|  
|[3349 — ListenerOpenStart](3349-listeneropenstart.md)|Pełny|Otwieranie odbiornika dla '% 1 '.|Ukierunkowan|  
|[3350 — ListenerOpenStop](3350-listeneropenstop.md)|Pełny|Ukończono otwieranie odbiornika.|Ukierunkowan|  
|[3351 — ServerMaxPooledConnectionsQuotaReached](3351-servermaxpooledconnectionsquotareached.md)|Pełny|Osiągnięto przydział maksymalnej liczby połączeń obsługiwanych przez pule serwera.|Działa|  
|[3352 — TcpConnectionTimedOut](3352-tcpconnectiontimedout.md)|Błąd|Gniazdo socketid:% 1 do zdalnego adresu% 2 przekroczyło limit czasu.|TCP|  
|[3353 — TcpConnectionResetError](3353-tcpconnectionreseterror.md)|Ostrzeżenie|Gniazdo socketid:% 1 do adresu zdalnego% 2 ma błąd resetowania połączenia.|TCP|  
|[3354 — ServiceSecurityNegotiationCompleted](3354-servicesecuritynegotiationcompleted.md)|Pełny|Ukończono negocjowanie zabezpieczeń usługi.|Zabezpieczenia|  
|[3355 — SecurityNegotiationProcessingFailure](3355-securitynegotiationprocessingfailure.md)|Błąd|Przetwarzanie negocjacji zabezpieczeń nie powiodło się.|Zabezpieczenia|  
|[3356 — SecurityIdentityVerificationSuccess](3356-securityidentityverificationsuccess.md)|Pełny|Weryfikacja zabezpieczeń zakończyła się pomyślnie.|Zabezpieczenia|  
|[3357 — SecurityIdentityVerificationFailure](3357-securityidentityverificationfailure.md)|Błąd|Weryfikacja zabezpieczeń nie powiodła się.|Zabezpieczenia|  
|[3358 — PortSharingDuplicatedSocket](3358-portsharingduplicatedsocket.md)|Pełny|Zduplikowano gniazdo dla% 1.|ActivationServices|  
|[3359 — SecurityImpersonationSuccess](3359-securityimpersonationsuccess.md)|Pełny|Personifikacja zabezpieczeń zakończyła się pomyślnie.|Zabezpieczenia|  
|[3360 — SecurityImpersonationFailure](3360-securityimpersonationfailure.md)|Ostrzeżenie|Personifikacja zabezpieczeń nie powiodła się.|Zabezpieczenia|  
|[3361 — HttpChannelRequestAborted](3361-httpchannelrequestaborted.md)|Ostrzeżenie|Żądanie kanału http zostało przerwane.|HTTP|  
|[3362 — HttpChannelResponseAborted](3362-httpchannelresponseaborted.md)|Ostrzeżenie|Odpowiedź kanału http została przerwana.|HTTP|  
|[3363 — HttpAuthFailed](3363-httpauthfailed.md)|Ostrzeżenie|Uwierzytelnianie HTTP nie powiodło się.|HTTP|  
|[3364 — SharedListenerProxyRegisterStart](3364-sharedlistenerproxyregisterstart.md)|Pełny|Rozpoczęto rejestrację obiektu sharedlistenerproxy dla identyfikatora URI "% 1".|ActivationServices|  
|[3365 — SharedListenerProxyRegisterStop](3365-sharedlistenerproxyregisterstop.md)|Pełny|Zatrzymywanie rejestru obiektu sharedlistenerproxy.|ActivationServices|  
|[3366 — SharedListenerProxyRegisterFailed](3366-sharedlistenerproxyregisterfailed.md)|Błąd|Rejestrowanie obiektu sharedlistenerproxy nie powiodło się ze stanem "% 1".|ActivationServices|  
|[3367 — ConnectionPoolPreambleFailed](3367-connectionpoolpreamblefailed.md)|Błąd|ConnectionPoolPreambleFailed.|Ukierunkowan|  
|[3368 — SslOnInitiateUpgrade](3368-ssloninitiateupgrade.md)|Pełny|SslOnAcceptUpgradeStart|Zabezpieczenia|  
|[3369 — SslOnAcceptUpgrade](3369-sslonacceptupgrade.md)|Pełny|SslOnAcceptUpgradeStop|Zabezpieczenia|  
|[3370 — BinaryMessageEncodingStart](3370-binarymessageencodingstart.md)|Pełny|Obiekt BinaryMessageEncoder rozpoczął rozpoczął kodowanie komunikatu.|Ukierunkowan|  
|[3371 — MtomMessageEncodingStart](3371-mtommessageencodingstart.md)|Pełny|Obiekt mtommessageencoder rozpoczął rozpoczął kodowanie komunikatu.|Ukierunkowan|  
|[3372 — TextMessageEncodingStart](3372-textmessageencodingstart.md)|Pełny|Obiekt textmessageencoder rozpoczął rozpoczął kodowanie komunikatu.|Ukierunkowan|  
|[3373 — BinaryMessageDecodingStart](3373-binarymessagedecodingstart.md)|Pełny|Obiekt BinaryMessageEncoder rozpoczął rozpoczął dekodowanie komunikatu.|Ukierunkowan|  
|[3374 — MtomMessageDecodingStart](3374-mtommessagedecodingstart.md)|Pełny|Obiekt mtommessageencoder rozpoczął rozpoczął dekodowanie komunikatu.|Ukierunkowan|  
|[3375 — TextMessageDecodingStart](3375-textmessagedecodingstart.md)|Pełny|Obiekt textmessageencoder rozpoczął rozpoczął dekodowanie komunikatu.|Ukierunkowan|  
|[3376 — HttpResponseReceiveStart](3376-httpresponsereceivestart.md)|Informacje|Transport HTTP rozpoczął odebranie komunikatu.|HTTP|  
|[3377 — SocketReadStop](3377-socketreadstop.md)|Pełny|Gniazdo socketid:% 1 odczytano bajty "% 2" odczytane z "% 3".|TCP|  
|[3378 — SocketAsyncReadStop](3378-socketasyncreadstop.md)|Pełny|Gniazdo socketid:% 1 odczytano bajty "% 2" odczytane z "% 3".|TCP|  
|[3379 — SocketWriteStart](3379-socketwritestart.md)|Pełny|Gniazdo socketid:% 1 zapisuje "% 2" bajtów do "% 3".|TCP|  
|[3380 — SocketAsyncWriteStart](3380-socketasyncwritestart.md)|Pełny|Gniazdo socketid:% 1 zapisuje "% 2" bajtów do "% 3".|TCP|  
|[3381 — SequenceAcknowledgementSent](3381-sequenceacknowledgementsent.md)|Pełny|Wysłano potwierdzenie sesji SessionId:% 1.|Ukierunkowan|  
|[3382 — ClientReliableSessionReconnect](3382-clientreliablesessionreconnect.md)|Informacje|Ponowne nawiązywanie połączenia z identyfikatorem sesji:% 1.|Ukierunkowan|  
|[3383 — ReliableSessionChannelFaulted](3383-reliablesessionchannelfaulted.md)|Informacje|Błąd sesji SessionId:% 1.|Ukierunkowan|  
|[3384 — WindowsStreamSecurityOnInitiateUpgrade](3384-windowsstreamsecurityoninitiateupgrade.md)|Pełny|WindowsStreamSecurity inicjowania zabezpieczeń.|Zabezpieczenia|  
|[3385 — WindowsStreamSecurityOnAcceptUpgrade](3385-windowsstreamsecurityonacceptupgrade.md)|Pełny|Zabezpieczenia przesyłania strumieniowego systemu Windows przy akceptowaniu uaktualnienia.|Zabezpieczenia|  
|[3386 — SocketConnectionAbort](3386-socketconnectionabort.md)|Ostrzeżenie|Gniazdo socketid:% 1 przerywa.|TCP|  
|[3388 — HttpGetContextStart](3388-httpgetcontextstart.md)|Pełny|HttpGetContext.|HTTP|  
|[3389 — ClientSendPreambleStart](3389-clientsendpreamblestart.md)|Pełny|Klient rozpoczął wysyłanie preambuły.|Ukierunkowan|  
|[3390 — ClientSendPreambleStop](3390-clientsendpreamblestop.md)|Pełny|Klient zatrzymał wysyłanie preambuły.|Ukierunkowan|  
|[3391 — HttpMessageReceiveFailed](3391-httpmessagereceivefailed.md)|Ostrzeżenie|Odbieranie komunikatu http nie powiodło się.|HTTP|  
|[3392 — TransactionScopeCreate](3392-transactionscopecreate.md)|Informacje|Element TransactionScope jest tworzony z właściwościami LocalIdentifier: '% 1 ' i DistributedIdentifier: '% 2 '.|Modelu|  
|[3393 — StreamedMessageReadByEncoder](3393-streamedmessagereadbyencoder.md)|Informacje|Koder odczytał komunikat przesyłany strumieniowo.|Ukierunkowan|  
|[3394 — StreamedMessageWrittenByEncoder](3394-streamedmessagewrittenbyencoder.md)|Informacje|Koder zapisał komunikat przesyłany strumieniowo.|Ukierunkowan|  
|[3395 — MessageWrittenAsynchronouslyByEncoder](3395-messagewrittenasynchronouslybyencoder.md)|Informacje|Koder zapisał komunikat asynchronicznie.|Ukierunkowan|  
|[3396 — BufferedAsyncWriteStart](3396-bufferedasyncwritestart.md)|Informacje|Buforze BufferId:% 1 zakończył zapisywanie bajtów "% 2" w strumieniu bazowym.|Ukierunkowan|  
|[3397 — BufferedAsyncWriteStop](3397-bufferedasyncwritestop.md)|Informacje|Koder zapisał komunikat asynchronicznie.|Ukierunkowan|  
|[3398 — PipeSharedMemoryCreated](3398-pipesharedmemorycreated.md)|Pełny|Udostępniona pamięć potoku została utworzona w lokalizacji "% 1".|Ukierunkowan|  
|[3399 — NamedPipeCreated](3399-namedpipecreated.md)|Pełny|Utworzono nazwany potok '% 1 '.|Ukierunkowan|  
|[3401 — SignatureVerificationStart](3401-signatureverificationstart.md)|Pełny|Rozpoczęto weryfikację podpisu.|Zabezpieczenia|  
|[3402 — SignatureVerificationSuccess](3402-signatureverificationsuccess.md)|Pełny|Weryfikacja podpisu zakończyła się pomyślnie.|Zabezpieczenia|  
|[3403 — WrappedKeyDecryptionStart](3403-wrappedkeydecryptionstart.md)|Pełny|Rozpoczęto odszyfrowywanie klucza otoki.|Zabezpieczenia|  
|[3404 — WrappedKeyDecryptionSuccess](3404-wrappedkeydecryptionsuccess.md)|Pełny|Odszyfrowywanie klucza opakowanego zakończyło się pomyślnie.|Zabezpieczenia|  
|[3405 — EncryptedDataProcessingStart](3405-encrypteddataprocessingstart.md)|Pełny|Rozpoczęto przetwarzanie zaszyfrowanych danych.|Zabezpieczenia|  
|[3406 — EncryptedDataProcessingSuccess](3406-encrypteddataprocessingsuccess.md)|Pełny|Przetwarzanie zaszyfrowanych danych zakończyło się pomyślnie.|Zabezpieczenia|  
|[3407 — HttpPipelineProcessInboundRequestStart](3407-httppipelineprocessinboundrequeststart.md)|Pełny|Obsługa komunikatów http rozpoczęła przetwarzanie żądania przychodzącego.|HTTP|  
|[3408 — HttpPipelineBeginProcessInboundRequestStart](3408-httppipelinebeginprocessinboundrequeststart.md)|Pełny|Obsługa komunikatów http rozpoczęła asynchroniczne przetwarzanie żądania przychodzącego.|HTTP|  
|[3409 — HttpPipelineProcessInboundRequestStop](3409-httppipelineprocessinboundrequeststop.md)|Pełny|Obsługa komunikatów http ukończyła przetwarzanie żądania przychodzącego.|HTTP|  
|[3410 — HttpPipelineFaulted](3410-httppipelinefaulted.md)|Ostrzeżenie|Obsługa komunikatów HTTP jest uszkodzona.|HTTP|  
|[3411 — HttpPipelineTimeoutException](3411-httppipelinetimeoutexception.md)|Błąd|Przekroczono limit czasu połączenia z użyciem protokołu WebSocket.|HTTP|  
|[3412 — HttpPipelineProcessResponseStart](3412-httppipelineprocessresponsestart.md)|Pełny|Obsługa komunikatów http rozpoczęła przetwarzanie odpowiedzi.|HTTP|  
|[3413 — HttpPipelineBeginProcessResponseStart](3413-httppipelinebeginprocessresponsestart.md)|Pełny|Obsługa komunikatów http rozpoczęła asynchroniczne przetwarzanie odpowiedzi.|HTTP|  
|[3414 — HttpPipelineProcessResponseStop](3414-httppipelineprocessresponsestop.md)|Pełny|Obsługa komunikatów http ukończyła przetwarzanie odpowiedzi.|HTTP|  
|[3415 — WebSocketConnectionRequestSendStart](3415-websocketconnectionrequestsendstart.md)|Pełny|Żądanie połączenia obiektu WebSocket z '% 1 ' Send Start.|HTTP|  
|[3416 — WebSocketConnectionRequestSendStop](3416-websocketconnectionrequestsendstop.md)|Pełny|Wysłano żądanie połączenia gniazda WebSocketId:% 1.|HTTP|  
|[3417 — WebSocketConnectionAcceptStart](3417-websocketconnectionacceptstart.md)|Pełny|Rozpoczęto akceptację połączenia obiektu WebSocket.|HTTP|  
|[3418 — WebSocketConnectionAccepted](3418-websocketconnectionaccepted.md)|Pełny|Połączenie gniazda WebSocketId:% 1 zostało zaakceptowane.|HTTP|  
|[3419 — WebSocketConnectionDeclined](3419-websocketconnectiondeclined.md)|Błąd|Połączenie obiektu WebSocket zostało odrzucone z kodem stanu "% 1"|HTTP|  
|[3420 — WebSocketConnectionFailed](3420-websocketconnectionfailed.md)|Błąd|Żądanie połączenia obiektu WebSocket nie powiodło się: "% 1"|HTTP|  
|[3421 — WebSocketConnectionAborted](3421-websocketconnectionaborted.md)|Błąd|Połączenie gniazda WebSocketId:% 1 zostało przerwane.|HTTP|  
|[3422 — WebSocketAsyncWriteStart](3422-websocketasyncwritestart.md)|Pełny|Gniazdo WebSocketId:% 1 zapisuje "% 2" bajtów do "% 3".|HTTP|  
|[3423 — WebSocketAsyncWriteStop](3423-websocketasyncwritestop.md)|Pełny|Gniazdo WebSocketId:% 1 asynchroniczne zatrzymanie zapisu.|HTTP|  
|[3424 — WebSocketAsyncReadStart](3424-websocketasyncreadstart.md)|Pełny|Gniazdo WebSocketId:% 1 Rozpocznij odczyt.|HTTP|  
|[3425 — WebSocketAsyncReadStop](3425-websocketasyncreadstop.md)|Pełny|Gniazdo WebSocketId:% 1 odczytano "% 2" b z "% 3".|HTTP|  
|[3426 — WebSocketCloseSent](3426-websocketclosesent.md)|Pełny|Gniazdo WebSocketId:% 1 wysyła komunikat zamknięcia do "% 2" ze stanem zamknięcia "% 3".|HTTP|  
|[3427 — WebSocketCloseOutputSent](3427-websocketcloseoutputsent.md)|Pełny|Gniazdo WebSocketId:% 1 wysyła komunikat zamknięcia wyjścia do "% 2" ze stanem zamknięcia "% 3".|HTTP|  
|[3428 — WebSocketConnectionClosed](3428-websocketconnectionclosed.md)|Pełny|Połączenie gniazda WebSocketId:% 1 zostało zamknięte.|HTTP|  
|[3429 — WebSocketCloseStatusReceived](3429-websocketclosestatusreceived.md)|Pełny|Gniazdo WebSocketId:% 1 Odebrano komunikat zamknięcia połączenia ze stanem "% 2".|HTTP|  
|[3430 — WebSocketUseVersionFromClientWebSocketFactory](3430-websocketuseversionfromclientwebsocketfactory.md)|Pełny|Używanie wartości WebSocketVersion z fabryki protokołu WebSocket klienta typu '% 1 '.|HTTP|  
|[3431 — WebSocketCreateClientWebSocketWithFactory](3431-websocketcreateclientwebsocketwithfactory.md)|Pełny|Tworzenie obiektu WebSocket klienta za pomocą fabryki typu '% 1 '.|HTTP|  
|[3553 — XamlServicesLoadStart](3553-xamlservicesloadstart.md)|Informacje|XamlServicesLoad|WebHost|  
|[3554 — XamlServicesLoadStop](3554-xamlservicesloadstop.md)|Informacje|XamlServicesLoad Stop|WebHost|  
|[3555 — CreateWorkflowServiceHostStart](3555-createworkflowservicehoststart.md)|Informacje|Rozpoczęcie obiektu WorkflowServiceHost|WebHost|  
|[3556 — CreateWorkflowServiceHostStop](3556-createworkflowservicehoststop.md)|Informacje|Zatrzymaj obiekt WorkflowServiceHost|WebHost|  
|[3558 — ServiceActivationStart](3558-serviceactivationstart.md)|Informacje|Rozpoczęcie aktywacji usługi|WebHost|  
|[3559 — ServiceActivationStop](3559-serviceactivationstop.md)|Informacje|Zatrzymanie aktywacji usługi|WebHost|  
|[3560 — ServiceActivationAvailableMemory](3560-serviceactivationavailablememory.md)|Pełny|Dostępna pamięć (w bajtach):% 1|Działa|  
|[3800 — RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|Informacje|Usługa routingu zamyka klienta '% 1 '.|RoutingServices|  
|[3800 — RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|Ostrzeżenie|Wystąpił błąd klienta usługi routingu "% 1".|RoutingServices|  
|[3802 — RoutingServiceCompletingOneWay](3802-routingservicecompletingoneway.md)|Informacje|Usługa routingu kończy wykonywanie komunikatu jednokierunkowego.|RoutingServices|  
|[3803 — RoutingServiceProcessingFailure](3803-routingserviceprocessingfailure.md)|Błąd|Wystąpił błąd usługi routingu podczas przetwarzania komunikatu w punkcie końcowym o adresie '% 1 '.|RoutingServices|  
|[3804 — RoutingServiceCreatingClientForEndpoint](3804-routingservicecreatingclientforendpoint.md)|Informacje|Usługa routingu tworzy klienta dla punktu końcowego: '% 1 '.|RoutingServices|  
|[3805 — RoutingServiceDisplayConfig](3805-routingservicedisplayconfig.md)|Pełny|Usługa routingu jest skonfigurowana z RouteOnHeadersOnly:% 1, SoapProcessingEnabled:% 2, EnsureOrderedDispatch:% 3.|RoutingServices|  
|[3807 — RoutingServiceCompletingTwoWay](3807-routingservicecompletingtwoway.md)|Informacje|Trwa uzupełnianie komunikatu odpowiedzi na żądanie usługi routingu.|RoutingServices|  
|[3809 — RoutingServiceMessageRoutedToEndpoints](3809-routingservicemessageroutedtoendpoints.md)|Pełny|Usługa routingu skierowała komunikat o IDENTYFIKATORze "% 1" do listy punktów końcowych:% 2.|RoutingServices|  
|[3810 — RoutingServiceConfigurationApplied](3810-routingserviceconfigurationapplied.md)|Informacje|Do usługi routingu został zastosowany nowy zastosowano.|RoutingServices|  
|[3815 — RoutingServiceProcessingMessage](3815-routingserviceprocessingmessage.md)|Informacje|Usługa routingu przetwarza komunikat o IDENTYFIKATORze: "% 1", Akcja: "% 2", adres URL ruchu przychodzącego: "% 3" odebrany w transakcji:% 4.|RoutingServices|  
|[3816 — RoutingServiceTransmittingMessage](3816-routingservicetransmittingmessage.md)|Informacje|Usługa routingu przesyła komunikat o IDENTYFIKATORze:% 1 [operacja% 2] do "% 3".|RoutingServices|  
|[3817 — RoutingServiceCommittingTransaction](3817-routingservicecommittingtransaction.md)|Informacje|Usługa routingu zatwierdza transakcję o identyfikatorze: '% 1 '.|RoutingServices|  
|[3818 — RoutingServiceDuplexCallbackException](3818-routingserviceduplexcallbackexception.md)|Błąd|Składnik usługi routingu% 1 napotkał wyjątek dwustronnego wywołania zwrotnego.|RoutingServices|  
|[3819 — RoutingServiceMovedToBackup](3819-routingservicemovedtobackup.md)|Informacje|Komunikat usługi routingu o IDENTYFIKATORze: "% 1" [operacja% 2] został przeniesiony do kopii zapasowej punktu końcowego "% 3".|RoutingServices|  
|[3820 — RoutingServiceCreatingTransaction](3820-routingservicecreatingtransaction.md)|Informacje|Usługa routingu utworzyła nową transakcję o identyfikatorze '% 1 ' na potrzeby przetwarzania komunikatów.|RoutingServices|  
|[3821 — RoutingServiceCloseFailed](3821-routingserviceclosefailed.md)|Ostrzeżenie|Wystąpił błąd usługi routingu podczas zamykania klienta wychodzącego '% 1 '.|RoutingServices|  
|[3822 — RoutingServiceSendingResponse](3822-routingservicesendingresponse.md)|Informacje|Usługa routingu wysyła komunikat odpowiedzi z akcją "% 1".|RoutingServices|  
|[3823 — RoutingServiceSendingFaultResponse](3823-routingservicesendingfaultresponse.md)|Ostrzeżenie|Usługa routingu wysyła komunikat odpowiedzi o błędzie z akcją "% 1".|RoutingServices|  
|[3824 — RoutingServiceCompletingReceiveContext](3824-routingservicecompletingreceivecontext.md)|Pełny|Usługa routingu wywołuje metodę ReceiveContext. Complete dla komunikatu o IDENTYFIKATORze:% 1.|RoutingServices|  
|[3825 — RoutingServiceAbandoningReceiveContext](3825-routingserviceabandoningreceivecontext.md)|Ostrzeżenie|Usługa routingu wywołuje metodę ReceiveContext. Abandon dla komunikatu o IDENTYFIKATORze:% 1.|RoutingServices|  
|[3826 — RoutingServiceUsingExistingTransaction](3826-routingserviceusingexistingtransaction.md)|Pełny|Usługa routingu wyśle komunikaty przy użyciu istniejącej transakcji "% 1".|RoutingServices|  
|[3827 — RoutingServiceTransmitFailed](3827-routingservicetransmitfailed.md)|Ostrzeżenie|Wystąpił błąd usługi routingu podczas wysyłania komunikatu do '% 1 '.|RoutingServices|  
|[3828 — RoutingServiceFilterTableMatchStart](3828-routingservicefiltertablematchstart.md)|Informacje|Rozpoczęcie dopasowywania obiektem usługi routingu.|RoutingServices|  
|[3829 — RoutingServiceFilterTableMatchStop](3829-routingservicefiltertablematchstop.md)|Informacje|Obiektem usługi routingu.|RoutingServices|  
|[3830 — RoutingServiceAbortingChannel](3830-routingserviceabortingchannel.md)|Pełny|Usługa routingu wywołuje metodę Abort w kanale: "% 1".|RoutingServices|  
|[3831 — RoutingServiceHandledException](3831-routingservicehandledexception.md)|Pełny|Usługa routingu obsłużył wyjątek.|RoutingServices|  
|[3832 — RoutingServiceTransmitSucceeded](3832-routingservicetransmitsucceeded.md)|Informacje|Usługa routingu pomyślnie przesłała komunikat o IDENTYFIKATORze: "% 1 [operacja% 2] do"% 3 ".|RoutingServices|  
|[4001 — TransportListenerSessionsReceived](4001-transportlistenersessionsreceived.md)|Pełny|Odebrano sesję odbiornika transportu za pośrednictwem "% 1"|ActivationServices|  
|[4002 — FailFastException](4002-failfastexception.md)|Krytyczny|FailFastException.|ActivationServices|  
|[4003 — ServiceStartPipeError](4003-servicestartpipeerror.md)|Błąd|Błąd potoku uruchomienia usługi.|ActivationServices|  
|[4008 — DispatchSessionStart](4008-dispatchsessionstart.md)|Pełny|Rozpoczęto wysyłanie sesji.|ActivationServices|  
|[4008 — DispatchSessionStart](4008-dispatchsessionstart.md)|Ostrzeżenie|Wysyłanie sesji dla elementu "% 1" nie powiodło się, ponieważ oczekująca Kolejka sesji jest zapełniona elementami oczekującymi na "% 2".|ActivationServices|  
|[4011 — MessageQueueRegisterStart](4011-messagequeueregisterstart.md)|Pełny|Rozpoczęto rejestrowanie kolejki komunikatów.|ActivationServices|  
|[4012 — MessageQueueRegisterAbort](4012-messagequeueregisterabort.md)|Błąd|Rejestracja kolejki komunikatów została przerwana ze stanem "% 1" dla identyfikatora URI: "% 2".|ActivationServices|  
|[4013 — MessageQueueUnregisterSucceeded](4013-messagequeueunregistersucceeded.md)|Pełny|Wyrejestrowanie kolejki komunikatów dla identyfikatora URI "% 1" zakończyło się pomyślnie.|ActivationServices|  
|[4014 — MessageQueueRegisterFailed](4014-messagequeueregisterfailed.md)|Błąd|Rejestracja kolejki komunikatów dla identyfikatora URI "% 1" nie powiodła się. stan: "% 2".|ActivationServices|  
|[4015 — MessageQueueRegisterCompleted](4015-messagequeueregistercompleted.md)|Informacje|Rejestracja kolejki komunikatów dla identyfikatora URI "% 1" została zakończona.|ActivationServices|  
|[4016 — MessageQueueDuplicatedSocketError](4016-messagequeueduplicatedsocketerror.md)|Błąd|Kolejka komunikatów nie może zduplikować gniazda.|ActivationServices|  
|[4019 — MessageQueueDuplicatedSocketComplete](4019-messagequeueduplicatedsocketcomplete.md)|Pełny|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 — TcpTransportListenerListeningStart](4020-tcptransportlistenerlisteningstart.md)|Pełny|Odbiornik transportu TCP rozpoczął nasłuchiwanie na identyfikatorze URI: '% 1 '.|ActivationServices|  
|[4021 — TcpTransportListenerListeningStop](4021-tcptransportlistenerlisteningstop.md)|Pełny|Odbiornik transportu TCP nasłuchuje.|ActivationServices|  
|[4022 — WebhostUnregisterProtocolFailed](4022-webhostunregisterprotocolfailed.md)|Błąd|Kod błędu:% 1|ActivationServices|  
|[4023 — WasCloseAllListenerChannelInstancesCompleted](4023-wasclosealllistenerchannelinstancescompleted.md)|Informacje|Ukończono Zamykanie wszystkich wystąpień kanałów odbiornika.|ActivationServices|  
|[4024 — WasCloseAllListenerChannelInstancesFailed](4024-wasclosealllistenerchannelinstancesfailed.md)|Błąd|Kod błędu:% 1|ActivationServices|  
|[4025 — OpenListenerChannelInstanceFailed](4025-openlistenerchannelinstancefailed.md)|Błąd|Kod błędu:% 1|ActivationServices|  
|[4026 — WasConnected](4026-wasconnected.md)|Pełny|Nawiązano połączenie.|ActivationServices|  
|[4027 — WasDisconnected](4027-wasdisconnected.md)|Pełny|ZOSTAŁO rozłączone.|ActivationServices|  
|[4028 — PipeTransportListenerListeningStart](4028-pipetransportlistenerlisteningstart.md)|Pełny|Odbiornik transportu potokowego rozpoczął nasłuchiwanie na identyfikatorze URI:% 1.|ActivationServices|  
|[4029 — PipeTransportListenerListeningStop](4029-pipetransportlistenerlisteningstop.md)|Pełny|Zatrzymanie nasłuchiwania odbiornika transportu potokowego.|ActivationServices|  
|[4030 — DispatchSessionSuccess](4030-dispatchsessionsuccess.md)|Informacje|Wysyłanie sesji zakończyło się pomyślnie.|ActivationServices|  
|[4031 — DispatchSessionFailed](4031-dispatchsessionfailed.md)|Błąd|Dystrybucja sesji nie powiodła się.|ActivationServices|  
|[4032 — WasConnectionTimedout](4032-wasconnectiontimedout.md)|Krytyczny|Przekroczono limit czasu połączenia.|ActivationServices|  
|[4033 — RoutingTableLookupStart](4033-routingtablelookupstart.md)|Pełny|Rozpoczęto wyszukiwanie w tabeli routingu.|ActivationServices|  
|[4034 — RoutingTableLookupStop](4034-routingtablelookupstop.md)|Pełny|Ukończono wyszukiwanie w tabeli routingu.|ActivationServices|  
|[4035 — PendingSessionQueueRatio](4035-pendingsessionqueueratio.md)|Pełny|Współczynnik kolejki sesji oczekujących:% 1/% 2|Działa|  
|[4600 — MessageLogEventSizeExceeded](4600-messagelogeventsizeexceeded.md)|Ostrzeżenie|Nie można zarejestrować komunikatu, ponieważ przekracza on rozmiar zdarzenia ETW|WCFMessageLogging|  
|[4801 — DiscoveryClientInClientChannelFailedToClose](4801-discoveryclientinclientchannelfailedtoclose.md)|Ostrzeżenie|Nie można zamknąć obiekt DiscoveryClient utworzonego wewnątrz DiscoveryClientChannel i w związku z tym został przerwany.|Odnajdywanie|  
|[4802 — DiscoveryClientProtocolExceptionSuppressed](4802-discoveryclientprotocolexceptionsuppressed.md)|Informacje|Element ProtocolException został pominięty podczas zamykania obiekt DiscoveryClient. Może to być spowodowane tym, że DiscoveryService nadal próbuje wysłać odpowiedź do obiekt DiscoveryClient.|Odnajdywanie|  
|[4803 — DiscoveryClientReceivedMulticastSuppression](4803-discoveryclientreceivedmulticastsuppression.md)|Informacje|Obiekt DiscoveryClient otrzymał komunikat o pominięciu multiemisji z obiektu DiscoveryProxy.|Odnajdywanie|  
|[4804 — DiscoveryMessageReceivedAfterOperationCompleted](4804-discoverymessagereceivedafteroperationcompleted.md)|Informacje|Komunikat% 1 o atrybucie messageId równym "% 2" został porzucony przez obiekt DiscoveryClient, ponieważ operacja% 3 została ukończona.|Odnajdywanie|  
|[4805 — DiscoveryMessageWithInvalidContent](4805-discoverymessagewithinvalidcontent.md)|Ostrzeżenie|Komunikat% 1 o atrybucie messageId równym "% 2" został porzucony, ponieważ miał nieprawidłową zawartość.|Odnajdywanie|  
|[4806 — DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Ostrzeżenie|Komunikat% 1 o atrybucie messageId równym "% 2" i RelatesTo = "% 3" został porzucony przez obiekt DiscoveryClient, ponieważ została ukończona odpowiadająca operacja% 4 lub wartość relatesta jest nieprawidłowa.|Odnajdywanie|  
|[4807 — DiscoveryMessageWithInvalidReplyTo](4807-discoverymessagewithinvalidreplyto.md)|Ostrzeżenie|Komunikat z żądaniem odnajdowania o atrybucie messageId równym "% 1" został porzucony, ponieważ miał nieprawidłowy adres ReplyTo.|Odnajdywanie|  
|[4808 — DiscoveryMessageWithNoContent](4808-discoverymessagewithnocontent.md)|Ostrzeżenie|Komunikat% 1 został porzucony, ponieważ nie miał zawartości.|Odnajdywanie|  
|[4809 — DiscoveryMessageWithNullMessageId](4809-discoverymessagewithnullmessageid.md)|Ostrzeżenie|Komunikat% 1 został porzucony, ponieważ nagłówek komunikatu nie zawierał wymaganej właściwości MessageId.|Odnajdywanie|  
|[4810 — DiscoveryMessageWithNullMessageSequence](4810-discoverymessagewithnullmessagesequence.md)|Ostrzeżenie|Komunikat% 1 o atrybucie messageId równym "% 2" został porzucony przez obiekt DiscoveryClient, ponieważ nie miał właściwości DiscoveryMessageSequence.|Odnajdywanie|  
|[4811 — DiscoveryMessageWithNullRelatesTo](4811-discoverymessagewithnullrelatesto.md)|Ostrzeżenie|Komunikat% 1 o atrybucie messageId równym "% 2" został porzucony przez obiekt DiscoveryClient, ponieważ nagłówek komunikatu nie zawierał wymaganej właściwości relatesta.|Odnajdywanie|  
|[4812 — DiscoveryMessageWithNullReplyTo](4812-discoverymessagewithnullreplyto.md)|Ostrzeżenie|Komunikat z żądaniem odnajdowania o atrybucie messageId równym "% 1" został porzucony, ponieważ nie miał adresu ReplyTo.|Odnajdywanie|  
|[4813 — DuplicateDiscoveryMessage](4813-duplicatediscoverymessage.md)|Ostrzeżenie|Komunikat% 1 o atrybucie messageId równym "% 2" został porzucony, ponieważ był duplikatem.|Odnajdywanie|  
|[4814 — EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|Informacje|Możliwość odnajdowania punktu końcowego z atrybutem EndpointAddress = '% 1 ' i ListenUri = '% 2 ' została wyłączona.|Odnajdywanie|  
|[4814 — EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|Informacje|Możliwość odnajdowania punktu końcowego z atrybutem EndpointAddress o wartości "% 1" i ListenUri o wartości "% 2" została włączona.|Odnajdywanie|  
|[4816 — FindInitiatedInDiscoveryClientChannel](4816-findinitiatedindiscoveryclientchannel.md)|Pełny|Operacja znajdowania została zainicjowana w DiscoveryClientChannel w celu odnalezienia punktów końcowych.|Odnajdywanie|  
|[4817 — InnerChannelCreationFailed](4817-innerchannelcreationfailed.md)|Ostrzeżenie|DiscoveryClientChannel nie mógł utworzyć kanału z wykrytym punktem końcowym z elementem EndpointAddress = '% 1 ' i za pośrednictwem = '% 2 '. DiscoveryClientChannel podejmie teraz próbę użycia następnego dostępnego odnalezionego punktu końcowego.|Odnajdywanie|  
|[4818 — InnerChannelOpenFailed](4818-innerchannelopenfailed.md)|Ostrzeżenie|DiscoveryClientChannel nie mógł otworzyć kanału z wykrytym punktem końcowym z elementem EndpointAddress = '% 1 ' i za pośrednictwem = '% 2 '. DiscoveryClientChannel podejmie teraz próbę użycia następnego dostępnego odnalezionego punktu końcowego.|Odnajdywanie|  
|[4819 — InnerChannelOpenSucceeded](4819-innerchannelopensucceeded.md)|Informacje|DiscoveryClientChannel pomyślnie wykrył punkt końcowy i otworzył kanał przy jego użyciu. Klient jest połączony z usługą przy użyciu elementu EndpointAddress = '% 1 ' i za pośrednictwem = '% 2 '.|Odnajdywanie|  
|[4820 — SynchronizationContextReset](4820-synchronizationcontextreset.md)|Informacje|SynchronizationContext został zresetowany do oryginalnej wartości% 1 przez DiscoveryClientChannel.|Odnajdywanie|  
|[4821 — SynchronizationContextSetToNull](4821-synchronizationcontextsettonull.md)|Informacje|SynchronizationContext została ustawiona na wartość null przez DiscoveryClientChannel przed zainicjowaniem operacji znajdowania.|Odnajdywanie|  
|[5001 — DCSerializeWithSurrogateStart](5001-dcserializewithsurrogatestart.md)|Pełny|Serializacja obiektu DataContract% 1 z surogatami została rozpoczęta.|Serializacja|  
|[5002 — DCSerializeWithSurrogateStop](5002-dcserializewithsurrogatestop.md)|Pełny|Serializacja obiektu DataContract z surogatami została zatrzymana.|Serializacja|  
|[5003 — DCDeserializeWithSurrogateStart](5003-dcdeserializewithsurrogatestart.md)|Pełny|Serializacja obiektu DataContract% 1 z surogatami została rozpoczęta.|Serializacja|  
|[5004 — DCDeserializeWithSurrogateStop](5004-dcdeserializewithsurrogatestop.md)|Pełny|Serializacja obiektu DataContract z surogatami została zatrzymana.|Serializacja|  
|[5005 — ImportKnownTypesStart](5005-importknowntypesstart.md)|Pełny|ImportKnownTypes.|Serializacja|  
|[5006 — ImportKnownTypesStop](5006-importknowntypesstop.md)|Pełny|ImportKnownTypes.|Serializacja|  
|[5007 — DCResolverResolve](5007-dcresolverresolve.md)|Pełny|Uruchamianie programu rozpoznawania obiektów DataContract (% 1).|Serializacja|  
|[5008 — DCGenWriterStart](5008-dcgenwriterstart.md)|Pełny|Generowanie obiektu DataContract — składnik zapisywania% 1 dla% 2.|Serializacja|  
|[5009 — DCGenWriterStop](5009-dcgenwriterstop.md)|Pełny|Zatrzymywanie modułu zapisującego generowania obiektu DataContract.|Serializacja|  
|[5010 — DCGenReaderStart](5010-dcgenreaderstart.md)|Pełny|Generowanie obiektu DataContract — czytnik% 1 dla% 2.|Serializacja|  
|[5011 — DCGenReaderStop](5011-dcgenreaderstop.md)|Pełny|Zatrzymano generowanie obiektu DataContract.|Serializacja|  
|[5012 — DCJsonGenReaderStart](5012-dcjsongenreaderstart.md)|Pełny|Generowanie pliku JSON — czytnik% 1 dla% 2.|Serializacja|  
|[5013 — DCJsonGenReaderStop](5013-dcjsongenreaderstop.md)|Pełny|Zatrzymano generowanie czytnika JSON.|Serializacja|  
|[5014 — DCJsonGenWriterStart](5014-dcjsongenwriterstart.md)|Pełny|Generowanie pliku JSON dla składnika zapisywania% 1 dla% 2 zostało rozpoczęte.|Serializacja|  
|[5015 — DCJsonGenWriterStop](5015-dcjsongenwriterstop.md)|Pełny|Generowanie pliku JSON — zatrzymanie składnika zapisywania.|Serializacja|  
|[5016 — GenXmlSerializableStart](5016-genxmlserializablestart.md)|Pełny|Generuj kod XML możliwy do serializacji dla "% 1".|Serializacja|  
|[5017 — GenXmlSerializableStop](5017-genxmlserializablestop.md)|Pełny|Generuj zatrzymywanie serializacji XML.|Serializacja|  
|[5203 — JsonMessageDecodingStart](5203-jsonmessagedecodingstart.md)|Pełny|Obiekt jsonmessageencoder rozpoczął rozpoczął dekodowanie komunikatu.|Ukierunkowan|  
|[5204 — JsonMessageEncodingStart](5204-jsonmessageencodingstart.md)|Pełny|Obiekt jsonmessageencoder rozpoczął rozpoczął kodowanie komunikatu.|Ukierunkowan|  
|[5402 — TokenValidationStarted](5402-tokenvalidationstarted.md)|Pełny|Rozpoczęto walidację obiektu SecurityToken (typ '% 1 ' i identyfikator '% 2 ').|Zabezpieczenia|  
|[5403 — TokenValidationSuccess](5403-tokenvalidationsuccess.md)|Pełny|Walidacja elementu SecurityToken (typ '% 1 ' i identyfikator '% 2 ') zakończyła się pomyślnie.|Zabezpieczenia|  
|[5404 — TokenValidationFailure](5404-tokenvalidationfailure.md)|Błąd|Walidacja elementu SecurityToken (typ '% 1 ' i identyfikator '% 2 ') nie powiodła się. %3|Zabezpieczenia|  
|[5405 — GetIssuerNameSuccess](5405-getissuernamesuccess.md)|Pełny|Pobieranie nazwy wystawcy:% 1 z obiektu tokenId:% 2 powiodło się.|Zabezpieczenia|  
|[5406 — GetIssuerNameFailure](5406-getissuernamefailure.md)|Błąd|Pobieranie nazwy wystawcy z obiektu tokenId:% 1 nie powiodło się.|Zabezpieczenia|  
|[5600 — FederationMessageProcessingStarted](5600-federationmessageprocessingstarted.md)|Pełny|Rozpoczęto przetwarzanie komunikatu federacyjnego.|Zabezpieczenia|  
|[5601 — FederationMessageProcessingSuccess](5601-federationmessageprocessingsuccess.md)|Pełny|Przetwarzanie komunikatu federacyjnego zakończyło się pomyślnie.|Zabezpieczenia|  
|[5602 — FederationMessageCreationStarted](5602-federationmessagecreationstarted.md)|Pełny|Rozpoczęto tworzenie komunikatu federacyjnego z formularza post.|Zabezpieczenia|  
|[5603 — FederationMessageCreationSuccess](5603-federationmessagecreationsuccess.md)|Pełny|Tworzenie komunikatu federacyjnego z formularza post zakończyło się pomyślnie.|Zabezpieczenia|  
|[5604 — SessionCookieReadingStarted](5604-sessioncookiereadingstarted.md)|Pełny|Rozpoczęto odczytywanie tokenu sesji z pliku cookie sesji.|Zabezpieczenia|  
|[5605 — SessionCookieReadingSuccess](5605-sessioncookiereadingsuccess.md)|Pełny|Odczytywanie tokenu sesji z pliku cookie sesji zakończyło się pomyślnie.|Zabezpieczenia|  
|[5606 — PrincipalSettingFromSessionTokenStarted](5606-principalsettingfromsessiontokenstarted.md)|Pełny|Uruchomiono ustawienie podmiotu zabezpieczeń na podstawie tokenu sesji.|Zabezpieczenia|  
|[5607 — PrincipalSettingFromSessionTokenSuccess](5607-principalsettingfromsessiontokensuccess.md)|Pełny|Ustawienie podmiotu zabezpieczeń na podstawie tokenu sesji zakończyło się pomyślnie.|Zabezpieczenia|  
|[57393 — AppDomainUnload](57393-appdomainunload.md)|Informacje|Zwalnianie elementu AppDomain. Element AppDomain. FriendlyName% 1, ProcessName% 2, identyfikator procesu% 3.|Infrastruktura|  
|[57394 — HandledException](57394-handledexception.md)|Informacje|Obsługa wyjątku.|Infrastruktura|  
|[57395 — ShipAssertExceptionMessage](57395-shipassertexceptionmessage.md)|Błąd|Wystąpił nieoczekiwany błąd. Aplikacje nie powinny podejmować prób obsługi tego błędu. W celach diagnostycznych ten komunikat w języku angielskim jest kojarzony z niepowodzeniem:% 1.|Infrastruktura|  
|[57396 — ThrowingException](57396-throwingexception.md)|Ostrzeżenie|Zgłaszanie wyjątku. Źródło% 1.|Infrastruktura|  
|[57397 — UnhandledException](57397-unhandledexception.md)|Krytyczny|Nieobsługiwany wyjątek.|Infrastruktura|  
|[57399 — TraceCodeEventLogCritical](57399-tracecodeeventlogcritical.md)|Krytyczny|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57400 — TraceCodeEventLogError](57400-tracecodeeventlogerror.md)|Błąd|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57401 — TraceCodeEventLogInfo](57401-tracecodeeventloginfo.md)|Informacje|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57402 — TraceCodeEventLogVerbose](57402-tracecodeeventlogverbose.md)|Pełny|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57403 — TraceCodeEventLogWarning](57403-tracecodeeventlogwarning.md)|Ostrzeżenie|Zapisano w dzienniku zdarzeń.|Infrastruktura|  
|[57404 — HandledExceptionWarning](57404-handledexceptionwarning.md)|Ostrzeżenie|Obsługa wyjątku.|Infrastruktura|  
|[62326 — HttpHandlerPickedForUrl](62326-httphandlerpickedforurl.md)|Informacje|Adres URL '% 1 ' zawiera dokument XAML z typem elementu głównego '% 2 '. Typ procedury obsługi HTTP '% 3 ' jest wybrany do obsługi wszystkich żądań wysyłanych do tego adresu URL.|WebHost|
