---
title: ICorProfilerCallback — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback
helpviewer_keywords:
- ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2f474317493b3aac421ca1270ff461b97cfe027
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598083"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback — Interfejs
Udostępnia metody, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR), aby powiadomić profiler kodu po wystąpieniu zdarzenia, dla których zostały zasubskrybowane przez profiler.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AppDomainCreationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Powiadamia program profilujący, że utworzono domeny aplikacji.|  
|[AppDomainCreationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Powiadamia program profilujący, że trwa tworzenie domeny aplikacji.|  
|[AppDomainShutdownFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Powiadamia program profilujący, że zostało zwolnione z procesu domeny aplikacji.|  
|[AppDomainShutdownStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Powiadamia program profilujący, że Trwa zwalnianie domeny aplikacji z procesu.|  
|[AssemblyLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Powiadamia program profilujący, że zespół zakończył ładowanie.|  
|[AssemblyLoadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Powiadamia program profilujący, że zestaw jest ładowany.|  
|[AssemblyUnloadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Powiadamia program profilujący, że zestaw został zwolniony.|  
|[AssemblyUnloadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Powiadamia program profilujący, że zestaw jest zwalniany.|  
|[ClassLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Powiadamia program profilujący, że klasa została zakończona podczas ładowania.|  
|[ClassLoadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Powiadamia program profilujący, że klasa jest ładowany.|  
|[ClassUnloadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Powiadamia program profilujący, klasa zakończenie zwolnienie.|  
|[ClassUnloadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Powiadamia program profilujący, że klasa jest zwalniany.|  
|[COMClassicVTableCreated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Powiadamia program profilujący, że wywoływana otoka środowiska uruchomieniowego (RCW) dla określonego identyfikatora IID i klasa została utworzona.|  
|[COMClassicVTableDestroyed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Powiadamia program profilujący jest niszczone RCW.|  
|[ExceptionCatcherEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Powiadamia program profilujący, że formant jest przekazywany do odpowiedniego `catch` bloku.|  
|[ExceptionCatcherLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Powiadamia program profilujący, że kontrola jest przekazywana poza odpowiednie `catch` bloku.|  
|[ExceptionCLRCatcherExecute, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Przestarzałe w programie .NET Framework 2.0.|  
|[ExceptionCLRCatcherFound, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Przestarzałe w programie .NET Framework 2.0.|  
|[ExceptionOSHandlerEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Nie zaimplementowano. Profiler, który potrzebuje informacji niezarządzany wyjątek, należy uzyskać te informacje w inny sposób.|  
|[ExceptionOSHandlerLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Nie zaimplementowano. Profiler, który potrzebuje informacji niezarządzany wyjątek, należy uzyskać te informacje w inny sposób.|  
|[ExceptionSearchCatcherFound, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Powiadamia program profilujący, że faza wyszukiwania dla obsługi wyjątków znajduje się program obsługi wyjątku, który został zgłoszony.|  
|[ExceptionSearchFilterEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Powiadamia program profilujący, że filtr użytkownika jest wykonywana.|  
|[ExceptionSearchFilterLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Powiadamia program profilujący, że filtr użytkownika po prostu zakończył wykonywania.|  
|[ExceptionSearchFunctionEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Powiadamia program profilujący, wprowadzenia w fazie wyszukiwania dla obsługi wyjątków funkcji.|  
|[ExceptionSearchFunctionLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Powiadamia program profilujący fazy wyszukiwania dla obsługi wyjątków zakończenie funkcji wyszukiwania.|  
|[ExceptionThrown, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Powiadamia program profilujący został zgłoszony wyjątek.|  
|[ExceptionUnwindFinallyEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Powiadamia program profilujący, że fazy odwijanie wyjątków wprowadzenie obsługi `finally` klauzuli zawarte w określonej funkcji.|  
|[ExceptionUnwindFinallyLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Powiadamia program profilujący, że fazy odwijanie wyjątków opuścił obsługi `finally` klauzuli.|  
|[ExceptionUnwindFunctionEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Powiadamia program profilujący, że faza unwind dla obsługi wyjątków wprowadzony w funkcji.|  
|[ExceptionUnwindFunctionLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Powiadamia program profilujący fazy unwind dla obsługi wyjątków zakończenie rozwinięcia funkcji.|  
|[FunctionUnloadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Powiadamia program profilujący uruchomienia wyładować funkcji środowiska uruchomieniowego.|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Wywoływane w celu zainicjowania programu profilującego, po każdym uruchomieniu nowej aplikacji CLR.|  
|[JITCachedFunctionSearchFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Powiadamia program profilujący, że dla funkcji, która została skompilowana wcześniej przy użyciu NGen.exe zakończył wyszukiwanie.|  
|[JITCachedFunctionSearchStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Powiadamia program profilujący, że wyszukiwania została uruchomiona dla funkcji, która została skompilowana wcześniej przy użyciu NGen.exe.|  
|[JITCompilationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Powiadamia program profilujący, kompilator JIT zakończenie kompilacji funkcji.|  
|[JITCompilationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Powiadamia program profilujący, że kompilator just-in-time (JIT) została uruchomiona kompilować funkcję.|  
|[JITFunctionPitched, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Powiadamia program profilujący, że funkcja, która została skompilowana JIT zostały usunięte z pamięci.|  
|[JITInlining, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Powiadamia program profilujący, że kompilator JIT zostanie Wstawianie funkcji z innej funkcji.|  
|[ManagedToUnmanagedTransition, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Powiadamia program profilujący, że nastąpiło przejście z kodu zarządzanego do kodu niezarządzanego.|  
|[ModuleAttachedToAssembly, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Powiadamia program profilujący, że moduł jest dołączany do własnego zestawu nadrzędnego.|  
|[ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Powiadamia program profilujący, że moduł zakończeniu ładowania.|  
|[ModuleLoadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Powiadamia program profilujący, że moduł jest załadowany.|  
|[ModuleUnloadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Powiadamia program profilujący, moduł zakończenie zwolnienie.|  
|[ModuleUnloadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Powiadamia program profilujący, że Trwa zwalnianie modułu.|  
|[MovedReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Powiadamia program profilujący o odwołania do obiektów, które zostały przeniesione podczas wyrzucania elementów bezużytecznych.|  
|[ObjectAllocated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Powiadamia program profilujący, która została przydzielona pamięci w stercie dla obiektu.|  
|[ObjectReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Powiadamia program profilujący dotyczących obiektów w pamięci, które odwołuje się określony obiekt.|  
|[ObjectsAllocatedByClass, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Powiadamia program profilujący o liczbę wystąpień każdej określonej klasy, które zostały utworzone od czasu poprzedniego wyrzucania elementów bezużytecznych.|  
|[RemotingClientInvocationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Powiadamia program profilujący, że wywołanie komunikacji zdalnej zostało uruchomione ukończone na komputerze klienckim.|  
|[RemotingClientInvocationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Powiadamia program profilujący, że wywołanie komunikacji zdalnej została uruchomiona.|  
|[RemotingClientReceivingReply, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Powiadamia program profilujący po stronie serwera część wywołanie komunikacji zdalnej została zakończona i klient otrzymuje teraz i wkrótce do przetwarzania odpowiedzi.|  
|[RemotingClientSendingMessage, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Powiadamia program profilujący, że klient wysyła żądanie do serwera.|  
|[RemotingServerInvocationReturned, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Powiadamia program profilujący, że proces zostanie zakończony, wywołania metody w odpowiedzi na żądanie wywołania zdalnej metody.|  
|[RemotingServerInvocationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Powiadamia program profilujący, że proces jest wywoływanie metody w odpowiedzi na żądanie wywołania zdalnej metody.|  
|[RemotingServerReceivingMessage, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Powiadamia program profilujący, że proces odbiera żądanie aktywacji lub wywołanie metody zdalnej.|  
|[RemotingServerSendingReply, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Powiadamia program profilujący, że proces zakończył przetwarzanie żądania wywołania zdalnej metody i ma przesłanie odpowiedzi za pośrednictwem kanału.|  
|[RootReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Powiadamia program profilujący informacje na temat odwołań do katalogu głównego po wyrzucania elementów bezużytecznych.|  
|[RuntimeResumeFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe wznowił wszystkie wątki środowiska uruchomieniowego i ma powrót do normalnego działania.|  
|[RuntimeResumeStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe jest wznawiana wszystkie wątki w czasie wykonywania.|  
|[RuntimeSuspendAborted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe została przerwana zawieszenia czasu wykonywania, który został pojawiają się.|  
|[RuntimeSuspendFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe ukończono zawieszenia wszystkie wątki w czasie wykonywania.|  
|[RuntimeSuspendStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe zostanie wstrzymać wszystkie wątki w czasie wykonywania.|  
|[RuntimeThreadResumed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Powiadamia program profilujący, że określony wątek została wznowiona po wstrzymaniu.|  
|[RuntimeThreadSuspended, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Powiadamia program profilujący, że określonego wątku została lub zostanie zawieszone.|  
|[Shutdown, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Powiadamia program profilujący, że aplikacja jest zamykana.|  
|[ThreadAssignedToOSThread, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Powiadamia program profilujący, że wątków zarządzanych wdrażane za pomocą wątku określonego systemu operacyjnego (OS).|  
|[ThreadCreated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Powiadamia program profilujący, że wątek został utworzony.|  
|[ThreadDestroyed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Powiadamia program profilujący wątku została zniszczona.|  
|[UnmanagedToManagedTransition, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Powiadamia program profilujący, że nastąpiło przejście z niezarządzanego kodu do kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metodę `ICorProfilerCallback` (lub [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) występuje w interfejsie powiadomić profiler, gdy zdarzenie, do którego zostały zasubskrybowane przez profiler,. Jest to interfejs podstawowy wywołania zwrotnego, za pomocą którego CLR komunikuje się za pomocą programu profilującego kodu.  
  
 Profiler kodu musi implementować metody `ICorProfilerCallback` interfejsu. Dla programu .NET Framework w wersji 2.0 lub nowszej, program profilujący musi implementować też `ICorProfilerCallback2` metody. Każda implementacja metody musi zwracać wartość HRESULT, która ma wartość S_OK w przypadku powodzenia lub E_FAIL w przypadku niepowodzenia. Obecnie CLR ignoruje HRESULT, który jest zwracany przez każdego wywołania zwrotnego z wyjątkiem [icorprofilercallback::objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 W rejestrze systemu Microsoft Windows, program profilujący kodu należy zarejestrować jego Component Object Model (COM) obiektu, który implementuje `ICorProfilerCallback` i `ICorProfilerCallback2` interfejsów. Profiler kodu subskrybuje do zdarzeń, dla których chce otrzymywać powiadomienia, wywołując [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Zazwyczaj jest to realizowane w implementacji programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Program profilujący jest możliwość odbierania powiadomień ze środowiska wykonawczego, gdy zdarzenie może nastąpić lub tylko podczas wykonywania procesu środowiska uruchomieniowego.  
  
> [!NOTE]
>  Program profilujący rejestruje pojedynczy obiekt COM. Jeśli program profilujący jest przeznaczony dla .NET Framework w wersji 1.0 i 1.1, czy obiekt modelu COM należy zaimplementować tylko metody `ICorProfilerCallback`. Jeśli jest on przeznaczony dla .NET Framework w wersji 2.0 lub nowszej, obiekt COM musi także implementować metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
