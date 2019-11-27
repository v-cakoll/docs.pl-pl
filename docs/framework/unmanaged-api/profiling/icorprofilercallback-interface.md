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
ms.openlocfilehash: 487f347c19ab513f328a9f1a02601fc72c233eb5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449928"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback — Interfejs
Dostarcza metody, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do powiadamiania profilera kodu o wystąpieniu zdarzeń subskrybowanych przez profiler.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AppDomainCreationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Powiadamia profiler o utworzeniu domeny aplikacji.|  
|[AppDomainCreationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Powiadamia profiler o tworzeniu domeny aplikacji.|  
|[AppDomainShutdownFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Powiadamia profiler o tym, że domena aplikacji została zwolniona z procesu.|  
|[AppDomainShutdownStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Powiadamia profiler o tym, że domena aplikacji jest zwalniana z procesu.|  
|[AssemblyLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Powiadamia profiler o zakończeniu ładowania zestawu.|  
|[AssemblyLoadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Powiadamia program profilujący, że zestaw jest ładowany.|  
|[AssemblyUnloadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Powiadamia program profilujący, że zestaw został zwolniony.|  
|[AssemblyUnloadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Powiadamia program profilujący, że zestaw jest zwolniony.|  
|[ClassLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Powiadamia profiler o zakończeniu ładowania klasy.|  
|[ClassLoadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Powiadamia program profilujący, że Klasa jest ładowana.|  
|[ClassUnloadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Powiadamia profiler o zakończeniu zwalniania klasy.|  
|[ClassUnloadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Powiadamia profiler o tym, że Klasa jest zwalniana.|  
|[COMClassicVTableCreated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Powiadamia program profilujący, że utworzono otokę (OTOKa) środowiska uruchomieniowego dla określonego identyfikatora IID i klasy.|  
|[COMClassicVTableDestroyed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Powiadamia profiler o zniszczeniu OTOKi.|  
|[ExceptionCatcherEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Powiadamia profiler, że sterowanie jest przesyłane do odpowiedniego bloku `catch`.|  
|[ExceptionCatcherLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Powiadamia profiler, że sterowanie jest przesyłane z odpowiedniego bloku `catch`.|  
|[ExceptionCLRCatcherExecute, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Przestarzałe w .NET Framework wersja 2,0.|  
|[ExceptionCLRCatcherFound, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Przestarzałe w .NET Framework 2,0.|  
|[ExceptionOSHandlerEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Nie zaimplementowane. Profiler wymagający niezarządzanych informacji o wyjątku musi uzyskać te informacje w inny sposób.|  
|[ExceptionOSHandlerLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Nie zaimplementowane. Profiler wymagający niezarządzanych informacji o wyjątku musi uzyskać te informacje w inny sposób.|  
|[ExceptionSearchCatcherFound, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Powiadamia profiler, że faza wyszukiwania obsługi wyjątków znalazła procedurę obsługi dla zgłoszonego wyjątku.|  
|[ExceptionSearchFilterEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Powiadamia profiler o wykonywaniu filtru użytkownika.|  
|[ExceptionSearchFilterLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Powiadamia profiler o zakończeniu wykonywania przez filtr użytkownika.|  
|[ExceptionSearchFunctionEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Powiadamia profiler, że faza wyszukiwania obsługi wyjątków wprowadziła funkcję.|  
|[ExceptionSearchFunctionLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Powiadamia profiler, że faza wyszukiwania obsługi wyjątków zakończyła Wyszukiwanie funkcji.|  
|[ExceptionThrown, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Powiadamia profiler o zgłoszonym wyjątku.|  
|[ExceptionUnwindFinallyEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Powiadamia program profilujący, że faza unwind dla obsługi wyjątków wprowadza klauzulę `finally`ą zawartą w określonej funkcji.|  
|[ExceptionUnwindFinallyLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Powiadamia profiler, że faza unwind dla obsługi wyjątków opuściła klauzulę `finally`.|  
|[ExceptionUnwindFunctionEnter, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Powiadamia profiler, że faza unwind w obsłudze wyjątków wprowadziła funkcję.|  
|[ExceptionUnwindFunctionLeave, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Powiadamia profiler, że faza unwind dla obsługi wyjątków zakończyła odwinięcie funkcji.|  
|[FunctionUnloadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Powiadamia profiler o rozpoczęciu pracy przez środowisko uruchomieniowe w celu zwolnienia funkcji.|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Wywołuje się, by zainicjować profiler za każdym razem, gdy zostanie uruchomiona nowa aplikacja środowiska CLR.|  
|[JITCachedFunctionSearchFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Powiadamia profiler o zakończeniu wyszukiwania dla funkcji, która została skompilowana wcześniej przy użyciu programu NGen. exe.|  
|[JITCachedFunctionSearchStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Powiadamia profiler o rozpoczęciu wyszukiwania dla funkcji, która została skompilowana wcześniej przy użyciu programu NGen. exe.|  
|[JITCompilationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Powiadamia profiler, że kompilator JIT zakończył Kompilowanie funkcji.|  
|[JITCompilationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Powiadamia program profilujący, że kompilator just in Time (JIT) rozpoczął Kompilowanie funkcji.|  
|[JITFunctionPitched, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Powiadamia profiler, że funkcja, która została skompilowana JIT, została usunięta z pamięci.|  
|[JITInlining, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Powiadamia program profilujący, że kompilator JIT ma wstawić funkcję w wierszu z inną funkcją.|  
|[ManagedToUnmanagedTransition, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Powiadamia profiler o wystąpieniu przejścia z kodu zarządzanego do kodu niezarządzanego.|  
|[ModuleAttachedToAssembly, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Powiadamia program profilujący, że moduł jest dołączony do jego zestawu nadrzędnego.|  
|[ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Powiadamia profiler o zakończeniu ładowania modułu.|  
|[ModuleLoadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Powiadamia program profilujący, że moduł jest ładowany.|  
|[ModuleUnloadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Powiadamia program profilujący o zakończeniu ładowania modułu.|  
|[ModuleUnloadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Powiadamia program profilujący, że moduł jest zwolniony.|  
|[MovedReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Powiadamia profiler o odwołaniach do obiektów, które zostały przeniesione podczas wyrzucania elementów bezużytecznych.|  
|[ObjectAllocated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Powiadamia program profilujący, że pamięć w stercie została przypisana dla obiektu.|  
|[ObjectReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Powiadamia profiler o obiektach w pamięci, do których odwołuje się określony obiekt.|  
|[ObjectsAllocatedByClass, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Powiadamia profiler o liczbie wystąpień każdej określonej klasy, które zostały utworzone od czasu poprzedniej wyrzucania elementów bezużytecznych.|  
|[RemotingClientInvocationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Powiadamia program profilujący, że wywołanie komunikacji zdalnej zostało uruchomione w celu ukończenia na kliencie.|  
|[RemotingClientInvocationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Powiadamia program profilujący o rozpoczęciu wywołania usług zdalnych.|  
|[RemotingClientReceivingReply, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Powiadamia program profilujący, że została ukończona część połączenia zdalnego po stronie serwera, a klient otrzymuje i informacje o przetwarzaniu odpowiedzi.|  
|[RemotingClientSendingMessage, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Powiadamia program profilujący, że klient wysyła żądanie do serwera.|  
|[RemotingServerInvocationReturned, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Powiadamia program profilujący, że proces zakończył wywoływanie metody w odpowiedzi na żądanie wywołania metody zdalnej.|  
|[RemotingServerInvocationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Powiadamia program profilujący, że proces wywołuje metodę w odpowiedzi na żądanie wywołania metody zdalnej.|  
|[RemotingServerReceivingMessage, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Powiadamia program profilujący, że proces otrzymuje zdalne wywołanie metody lub żądanie aktywacji.|  
|[RemotingServerSendingReply, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Powiadamia program profilujący, że proces zakończył przetwarzanie żądania wywołania metody zdalnej i ma na celu przesłanie odpowiedzi za pośrednictwem kanału.|  
|[RootReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Powiadamia profiler o informacji o odwołaniach głównych po wyrzucaniu elementów bezużytecznych.|  
|[RuntimeResumeFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe wznowił wszystkie wątki środowiska uruchomieniowego i wróciło do normalnego działania.|  
|[RuntimeResumeStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe wznawia wszystkie wątki czasu wykonywania.|  
|[RuntimeSuspendAborted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Powiadamia profiler, że środowisko uruchomieniowe przerywał zawieszanie czasu wykonywania.|  
|[RuntimeSuspendFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe zakończyło zawieszenie wszystkich wątków czasu wykonywania.|  
|[RuntimeSuspendStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Powiadamia profiler, że środowisko uruchomieniowe ma zawiesić wszystkie wątki czasu wykonywania.|  
|[RuntimeThreadResumed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Powiadamia program profilujący, że określony wątek został wznowiony po jego wstrzymaniu.|  
|[RuntimeThreadSuspended, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Powiadamia program profilujący, że określony wątek został lub wkrótce zostanie zawieszony.|  
|[Shutdown, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Powiadamia program profilujący, że aplikacja jest zamykana.|  
|[ThreadAssignedToOSThread, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Powiadamia program profilujący o implementacji wątku zarządzanego przy użyciu określonego wątku systemu operacyjnego (OS).|  
|[ThreadCreated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Powiadamia program profilujący o utworzeniu wątku.|  
|[ThreadDestroyed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Powiadamia profiler o zniszczeniu wątku.|  
|[UnmanagedToManagedTransition, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Powiadamia profiler o wystąpieniu przejścia z niezarządzanego kodu do kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metodę w interfejsie `ICorProfilerCallback` (lub [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) w celu powiadomienia profilera o wystąpieniu zdarzenia subskrybowanego przez profiler. Jest to podstawowy interfejs wywołania zwrotnego, za pomocą którego środowisko CLR komunikuje się z profilerem kodu.  
  
 Profiler kodu musi implementować metody interfejsu `ICorProfilerCallback`. W przypadku .NET Framework w wersji 2,0 lub nowszej profiler musi również zaimplementować metody `ICorProfilerCallback2`. Każda implementacja metody musi zwracać wynik HRESULT, który ma wartość S_OK w przypadku powodzenia lub E_FAIL w przypadku niepowodzenia. Obecnie środowisko CLR ignoruje wartość HRESULT zwracaną przez poszczególne wywołania zwrotne, z wyjątkiem [ICorProfilerCallback:: ObjectReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 W rejestrze systemu Microsoft Windows Profiler kodu musi zarejestrować swój obiekt Component Object Model (COM) implementujący interfejsy `ICorProfilerCallback` i `ICorProfilerCallback2`. Profiler kodu subskrybuje zdarzenia, dla których chce otrzymywać powiadomienie przez wywołanie [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Zwykle jest to wykonywane w implementacji profilera [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profiler jest w stanie odebrać powiadomienie z środowiska uruchomieniowego, gdy zdarzenie ma miejsce lub właśnie wystąpiło w trakcie wykonywania procesu.  
  
> [!NOTE]
> Profiler rejestruje pojedynczy obiekt COM. Jeśli profiler jest przeznaczony dla .NET Framework w wersji 1,0 lub 1,1, ten obiekt COM musi zaimplementować tylko metody `ICorProfilerCallback`. Jeśli jest to element docelowy .NET Framework wersja 2,0 lub nowsza, obiekt COM musi również zaimplementować metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
