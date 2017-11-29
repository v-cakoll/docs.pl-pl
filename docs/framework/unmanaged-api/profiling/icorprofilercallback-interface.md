---
title: "ICorProfilerCallback — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback
helpviewer_keywords: ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type: apiref
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3370dade937d67aa40be263faf3a433d142d932c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback — Interfejs
Udostępnia metody, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do powiadamiania profilera kodu występowania zdarzeń, do których subskrybowanych profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AppDomainCreationFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Powiadamia profilera, czy domena aplikacji została utworzona.|  
|[AppDomainCreationStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Powiadamia profiler jest tworzony domeny aplikacji.|  
|[AppDomainShutdownFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Powiadamia profilera, czy został zwolniony z procesu domeny aplikacji.|  
|[AppDomainShutdownStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Powiadamia profilera, że z procesem Zwalnianie domeny aplikacji.|  
|[AssemblyLoadFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Powiadamia profilera zakończenie zestawu ładowania.|  
|[AssemblyLoadStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Powiadamia profilera, że zestaw jest ładowany.|  
|[AssemblyUnloadFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Powiadamia profilera, że zestaw został usunięty z pamięci.|  
|[AssemblyUnloadStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Powiadamia profiler jest zwalniany zestawu.|  
|[ClassLoadFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Powiadamia profilera, czy klasa została załadowana.|  
|[ClassLoadStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Powiadamia profiler jest ładowany klasy.|  
|[ClassUnloadFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Powiadamia profilera klasy zakończenie zwalnianie.|  
|[ClassUnloadStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Powiadamia profiler jest zwalniany klasy.|  
|[COMClassicVTableCreated — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Powiadamia profilera utworzono wywoływana otoka środowiska uruchomieniowego (otoki RCW) dla określonego identyfikatora IID i klasy.|  
|[COMClassicVTableDestroyed — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Powiadamia profilera otoki RCW jest niszczone.|  
|[ExceptionCatcherEnter — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Powiadamia profiler kontrola jest przekazywana do odpowiedniego `catch` bloku.|  
|[ExceptionCatcherLeave — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Powiadamia profilera, że formant jest przekazywany z odpowiednią `catch` bloku.|  
|[ExceptionCLRCatcherExecute — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Przestarzałe w programie .NET Framework w wersji 2.0.|  
|[ExceptionCLRCatcherFound — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Przestarzałe w programie .NET Framework 2.0.|  
|[ExceptionOSHandlerEnter — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Nie jest zaimplementowana. Profiler wymagające niezarządzany wyjątek informacji należy uzyskać te informacje w inny sposób.|  
|[ExceptionOSHandlerLeave — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Nie jest zaimplementowana. Profiler wymagające niezarządzany wyjątek informacji należy uzyskać te informacje w inny sposób.|  
|[ExceptionSearchCatcherFound — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Powiadamia profilera, że fazy wyszukiwania obsługi wyjątków ma się program obsługi wyjątku, który został zgłoszony.|  
|[ExceptionSearchFilterEnter — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Powiadamia profilera filtr użytkownika jest wykonywana.|  
|[ExceptionSearchFilterLeave — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Powiadamia profilera, że filtr użytkownika właśnie zakończono wykonywanie.|  
|[ExceptionSearchFunctionEnter — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Powiadamia profilera wprowadzenia w fazie wyszukiwania dla obsługi wyjątków funkcji.|  
|[ExceptionSearchFunctionLeave — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Powiadamia profilera fazy wyszukiwania obsługi wyjątków zakończenie funkcję wyszukiwania.|  
|[ExceptionThrown — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Powiadamia profilera zgłosił wyjątek.|  
|[ExceptionUnwindFinallyEnter — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Powiadamia profiler fazy unwind wyjątek wprowadzania Obsługa `finally` klauzuli zawartych w określonej funkcji.|  
|[ExceptionUnwindFinallyLeave — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Powiadamia profiler fazy unwind wyjątek opuścił Obsługa `finally` klauzuli.|  
|[ExceptionUnwindFunctionEnter — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Powiadamia profilera wprowadzenia w fazie unwind dla obsługi wyjątków funkcji.|  
|[ExceptionUnwindFunctionLeave — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Powiadamia profilera fazy unwind dla obsługi wyjątków zakończenie rozwinięcia funkcji.|  
|[FunctionUnloadStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Powiadamia profilera, czy można zwolnić funkcja została uruchomiona środowiska uruchomieniowego.|  
|[Initialize — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Wywołuje się, by zainicjować profilera po każdym uruchomieniu nowej aplikacji CLR.|  
|[JITCachedFunctionSearchFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Powiadamia profilera zakończenie skompilowanego wcześniej przy użyciu NGen.exe funkcji wyszukiwania.|  
|[JITCachedFunctionSearchStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Powiadamia profilera, że dla funkcji skompilowanego wcześniej przy użyciu NGen.exe rozpoczęto wyszukiwanie.|  
|[JITCompilationFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Powiadamia profilera przy użyciu kompilatora JIT zakończenie kompilowania funkcji.|  
|[JITCompilationStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Powiadamia profilera, aby skompilować funkcję została uruchomiona przy użyciu kompilatora just in time (JIT).|  
|[JITFunctionPitched — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Powiadamia profilera, że funkcja, która została skompilowana JIT została usunięta z pamięci.|  
|[JITInlining — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Powiadamia profilera przy użyciu kompilatora JIT o zbliżającym się Wstawianie funkcji z inną funkcję.|  
|[ManagedToUnmanagedTransition — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Powiadamia profilera, że nastąpiło przejście z kodu zarządzanego do kodu niezarządzanego.|  
|[ModuleAttachedToAssembly — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Powiadamia profilera, czy moduł jest dołączony do zestawu jej nadrzędnej.|  
|[ModuleLoadFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Powiadamia profilera zakończenie moduł ładowania.|  
|[ModuleLoadStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Powiadamia profilera, czy moduł jest ładowany.|  
|[ModuleUnloadFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Powiadamia profilera modułu zakończenie zwalnianie.|  
|[ModuleUnloadStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Powiadamia profilera, że Trwa zwalnianie modułu.|  
|[MovedReferences — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Powiadamia profilera o odwołania do obiektów, które zostały przeniesione podczas wyrzucania elementów bezużytecznych.|  
|[ObjectAllocated — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Powiadamia profilera, która została przydzielona pamięci w stercie dla obiekt.|  
|[ObjectReferences — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Powiadamia profilera dotyczących obiektów w pamięci odwołuje się określony obiekt.|  
|[ObjectsAllocatedByClass — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Powiadamia profilera o liczbę wystąpień każdej określonej klasy, które zostały utworzone od czasu poprzedniego wyrzucanie elementów bezużytecznych.|  
|[RemotingClientInvocationFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Powiadamia profilera czy wywołaniem funkcji zdalnych zostało uruchomione do wykonania na kliencie.|  
|[RemotingClientInvocationStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Powiadamia profilera rozpoczęto wywołaniem funkcji zdalnych.|  
|[RemotingClientReceivingReply — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Powiadamia profiler Zakończono po stronie serwera część wywołaniem funkcji zdalnych i teraz odbiera klienta i informacje o przetwarzanie odpowiedzi.|  
|[RemotingClientSendingMessage — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Powiadamia profilera, że klient wysyła żądanie do serwera.|  
|[RemotingServerInvocationReturned — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Powiadamia profilera, proces zostanie zakończony, wywołania metody w odpowiedzi na żądanie wywołania metody zdalnego.|  
|[RemotingServerInvocationStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Powiadamia profilera, że proces jest wywoływanie metody w odpowiedzi na żądanie wywołania metody zdalnego.|  
|[RemotingServerReceivingMessage — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Powiadamia profilera, że proces odbiera żądania aktywacji lub wywołanie metody zdalnego.|  
|[RemotingServerSendingReply — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Powiadamia profilera, że proces zakończył przetwarzanie żądania wywołania metody zdalnego i ma przesyłać odpowiedzi za pośrednictwem kanału.|  
|[RootReferences — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Powiadamia profilera z informacji o odwołaniach głównego po wyrzucanie elementów bezużytecznych.|  
|[RuntimeResumeFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Powiadamia profilera, że środowisko wykonawcze wznowił wszystkie wątki środowiska uruchomieniowego i powrócił do normalnego działania.|  
|[RuntimeResumeStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Powiadamia profilera, że środowisko wykonawcze jest wznawianie wszystkie wątki środowiska wykonawczego.|  
|[RuntimeSuspendAborted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Powiadamia profilera, że środowisko wykonawcze została przerwana zawieszenia środowiska wykonawczego, który powtarzało się.|  
|[RuntimeSuspendFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Powiadamia profilera, czy środowisko uruchomieniowe zostało zakończone zawieszenia wszystkie wątki środowiska wykonawczego.|  
|[RuntimeSuspendStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Powiadamia profilera środowiska uruchomieniowego o zbliżającym się zawiesić wszystkie wątki środowiska wykonawczego.|  
|[RuntimeThreadResumed — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Powiadamia profilera, czy określony wątek ma wznowiona po wstrzymaniu.|  
|[RuntimeThreadSuspended — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Powiadamia profilera określony wątek został lub ma być wstrzymane.|  
|[Shutdown — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Powiadamia profilera, że aplikacja jest zamykana.|  
|[ThreadAssignedToOSThread — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Powiadamia profilera, że zarządzanego wątku jest implementowana przy użyciu wątku określonym systemie operacyjnym (systemu operacyjnego).|  
|[ThreadCreated — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Powiadamia profilera wątek został utworzony.|  
|[ThreadDestroyed — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Powiadamia profilera wątek został zlikwidowany.|  
|[UnmanagedToManagedTransition — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Powiadamia profilera, że nastąpiło przejście z kodu niezarządzanego kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metodę `ICorProfilerCallback` (lub [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) interfejsu powiadomiono profilera, gdy zdarzenie, do którego zostały zasubskrybowane profilera, występuje. Jest interfejsem podstawowym wywołania zwrotnego, za pomocą którego CLR komunikuje się z profilera kodu.  
  
 Profiler kodu musi implementować metody `ICorProfilerCallback` interfejsu. Dla programu .NET Framework w wersji 2.0 lub nowszej profilera musi implementować też `ICorProfilerCallback2` metody. Każda implementacja metody musi zwracać HRESULT, która ma wartość S_OK w przypadku powodzenia lub E_FAIL w przypadku awarii. Obecnie CLR ignoruje HRESULT, zwracane przez każdego wywołania zwrotnego z wyjątkiem [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 W rejestrze systemu Windows profilera kod należy zarejestrować jego obiekt składnika modelu COM (Object), który implementuje `ICorProfilerCallback` i `ICorProfilerCallback2` interfejsów. Profiler kodu subskrybuje zdarzenia, dla których chce otrzymywać powiadomienia przez wywołanie metody [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Zwykle odbywa się w celu wykonania profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profiler może następnie otrzymywanie powiadomień z środowiska uruchomieniowego zdarzenie może nastąpić lub po prostu wystąpił podczas wykonywania procesu obsługi.  
  
> [!NOTE]
>  Profiler rejestruje pojedynczego obiektu COM. Jeśli profiler jest docelowo na .NET Framework w wersji 1.0 lub 1.1, że obiektu COM należy zaimplementować tylko metody `ICorProfilerCallback`. Jeśli jest ona przeznaczona dla .NET Framework w wersji 2.0 lub nowszej, obiektu COM musi także implementować metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback2 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback3 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
