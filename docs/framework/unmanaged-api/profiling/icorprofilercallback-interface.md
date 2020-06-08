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
ms.openlocfilehash: 6a53b9b1b061c2ca07a469abc78c07ed9e710069
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500094"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback — Interfejs
Dostarcza metody, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do powiadamiania profilera kodu o wystąpieniu zdarzeń subskrybowanych przez profiler.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AppDomainCreationFinished, metoda](icorprofilercallback-appdomaincreationfinished-method.md)|Powiadamia profiler o utworzeniu domeny aplikacji.|  
|[AppDomainCreationStarted, metoda](icorprofilercallback-appdomaincreationstarted-method.md)|Powiadamia profiler o tworzeniu domeny aplikacji.|  
|[AppDomainShutdownFinished, metoda](icorprofilercallback-appdomainshutdownfinished-method.md)|Powiadamia profiler o tym, że domena aplikacji została zwolniona z procesu.|  
|[AppDomainShutdownStarted, metoda](icorprofilercallback-appdomainshutdownstarted-method.md)|Powiadamia profiler o tym, że domena aplikacji jest zwalniana z procesu.|  
|[AssemblyLoadFinished, metoda](icorprofilercallback-assemblyloadfinished-method.md)|Powiadamia profiler o zakończeniu ładowania zestawu.|  
|[AssemblyLoadStarted, metoda](icorprofilercallback-assemblyloadstarted-method.md)|Powiadamia program profilujący, że zestaw jest ładowany.|  
|[AssemblyUnloadFinished, metoda](icorprofilercallback-assemblyunloadfinished-method.md)|Powiadamia program profilujący, że zestaw został zwolniony.|  
|[AssemblyUnloadStarted, metoda](icorprofilercallback-assemblyunloadstarted-method.md)|Powiadamia program profilujący, że zestaw jest zwolniony.|  
|[ClassLoadFinished, metoda](icorprofilercallback-classloadfinished-method.md)|Powiadamia profiler o zakończeniu ładowania klasy.|  
|[ClassLoadStarted, metoda](icorprofilercallback-classloadstarted-method.md)|Powiadamia program profilujący, że Klasa jest ładowana.|  
|[ClassUnloadFinished, metoda](icorprofilercallback-classunloadfinished-method.md)|Powiadamia profiler o zakończeniu zwalniania klasy.|  
|[ClassUnloadStarted, metoda](icorprofilercallback-classunloadstarted-method.md)|Powiadamia profiler o tym, że Klasa jest zwalniana.|  
|[COMClassicVTableCreated, metoda](icorprofilercallback-comclassicvtablecreated-method.md)|Powiadamia program profilujący, że utworzono otokę (OTOKa) środowiska uruchomieniowego dla określonego identyfikatora IID i klasy.|  
|[COMClassicVTableDestroyed, metoda](icorprofilercallback-comclassicvtabledestroyed-method.md)|Powiadamia profiler o zniszczeniu OTOKi.|  
|[ExceptionCatcherEnter, metoda](icorprofilercallback-exceptioncatcherenter-method.md)|Powiadamia profiler, że sterowanie jest przesyłane do odpowiedniego `catch` bloku.|  
|[ExceptionCatcherLeave, metoda](icorprofilercallback-exceptioncatcherleave-method.md)|Powiadamia profiler, że sterowanie jest przesyłane z odpowiedniego `catch` bloku.|  
|[ExceptionCLRCatcherExecute, metoda](icorprofilercallback-exceptionclrcatcherexecute-method.md)|Przestarzałe w .NET Framework wersja 2,0.|  
|[ExceptionCLRCatcherFound, metoda](icorprofilercallback-exceptionclrcatcherfound-method.md)|Przestarzałe w .NET Framework 2,0.|  
|[ExceptionOSHandlerEnter, metoda](icorprofilercallback-exceptionoshandlerenter-method.md)|Nie zaimplementowano. Profiler wymagający niezarządzanych informacji o wyjątku musi uzyskać te informacje w inny sposób.|  
|[ExceptionOSHandlerLeave, metoda](icorprofilercallback-exceptionoshandlerleave-method.md)|Nie zaimplementowano. Profiler wymagający niezarządzanych informacji o wyjątku musi uzyskać te informacje w inny sposób.|  
|[ExceptionSearchCatcherFound, metoda](icorprofilercallback-exceptionsearchcatcherfound-method.md)|Powiadamia profiler, że faza wyszukiwania obsługi wyjątków znalazła procedurę obsługi dla zgłoszonego wyjątku.|  
|[ExceptionSearchFilterEnter, metoda](icorprofilercallback-exceptionsearchfilterenter-method.md)|Powiadamia profiler o wykonywaniu filtru użytkownika.|  
|[ExceptionSearchFilterLeave, metoda](icorprofilercallback-exceptionsearchfilterleave-method.md)|Powiadamia profiler o zakończeniu wykonywania przez filtr użytkownika.|  
|[ExceptionSearchFunctionEnter, metoda](icorprofilercallback-exceptionsearchfunctionenter-method.md)|Powiadamia profiler, że faza wyszukiwania obsługi wyjątków wprowadziła funkcję.|  
|[ExceptionSearchFunctionLeave, metoda](icorprofilercallback-exceptionsearchfunctionleave-method.md)|Powiadamia profiler, że faza wyszukiwania obsługi wyjątków zakończyła Wyszukiwanie funkcji.|  
|[ExceptionThrown, metoda](icorprofilercallback-exceptionthrown-method.md)|Powiadamia profiler o zgłoszonym wyjątku.|  
|[ExceptionUnwindFinallyEnter, metoda](icorprofilercallback-exceptionunwindfinallyenter-method.md)|Powiadamia profiler, że faza unwind dla obsługi wyjątków wprowadza `finally` klauzulę znajdującą się w określonej funkcji.|  
|[ExceptionUnwindFinallyLeave, metoda](icorprofilercallback-exceptionunwindfinallyleave-method.md)|Powiadamia profiler, że faza unwind dla obsługi wyjątków opuściła `finally` klauzulę.|  
|[ExceptionUnwindFunctionEnter, metoda](icorprofilercallback-exceptionunwindfunctionenter-method.md)|Powiadamia profiler, że faza unwind w obsłudze wyjątków wprowadziła funkcję.|  
|[ExceptionUnwindFunctionLeave, metoda](icorprofilercallback-exceptionunwindfunctionleave-method.md)|Powiadamia profiler, że faza unwind dla obsługi wyjątków zakończyła odwinięcie funkcji.|  
|[FunctionUnloadStarted, metoda](icorprofilercallback-functionunloadstarted-method.md)|Powiadamia profiler o rozpoczęciu pracy przez środowisko uruchomieniowe w celu zwolnienia funkcji.|  
|[Initialize — Metoda](icorprofilercallback-initialize-method.md)|Wywołuje się, by zainicjować profiler za każdym razem, gdy zostanie uruchomiona nowa aplikacja środowiska CLR.|  
|[JITCachedFunctionSearchFinished, metoda](icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Powiadamia profiler o zakończeniu wyszukiwania dla funkcji, która została skompilowana wcześniej przy użyciu programu NGen. exe.|  
|[JITCachedFunctionSearchStarted, metoda](icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Powiadamia profiler o rozpoczęciu wyszukiwania dla funkcji, która została skompilowana wcześniej przy użyciu programu NGen. exe.|  
|[JITCompilationFinished, metoda](icorprofilercallback-jitcompilationfinished-method.md)|Powiadamia profiler, że kompilator JIT zakończył Kompilowanie funkcji.|  
|[JITCompilationStarted, metoda](icorprofilercallback-jitcompilationstarted-method.md)|Powiadamia program profilujący, że kompilator just in Time (JIT) rozpoczął Kompilowanie funkcji.|  
|[JITFunctionPitched, metoda](icorprofilercallback-jitfunctionpitched-method.md)|Powiadamia profiler, że funkcja, która została skompilowana JIT, została usunięta z pamięci.|  
|[JITInlining, metoda](icorprofilercallback-jitinlining-method.md)|Powiadamia program profilujący, że kompilator JIT ma wstawić funkcję w wierszu z inną funkcją.|  
|[ManagedToUnmanagedTransition, metoda](icorprofilercallback-managedtounmanagedtransition-method.md)|Powiadamia profiler o wystąpieniu przejścia z kodu zarządzanego do kodu niezarządzanego.|  
|[ModuleAttachedToAssembly, metoda](icorprofilercallback-moduleattachedtoassembly-method.md)|Powiadamia program profilujący, że moduł jest dołączony do jego zestawu nadrzędnego.|  
|[ModuleLoadFinished, metoda](icorprofilercallback-moduleloadfinished-method.md)|Powiadamia profiler o zakończeniu ładowania modułu.|  
|[ModuleLoadStarted, metoda](icorprofilercallback-moduleloadstarted-method.md)|Powiadamia program profilujący, że moduł jest ładowany.|  
|[ModuleUnloadFinished, metoda](icorprofilercallback-moduleunloadfinished-method.md)|Powiadamia program profilujący o zakończeniu ładowania modułu.|  
|[ModuleUnloadStarted, metoda](icorprofilercallback-moduleunloadstarted-method.md)|Powiadamia program profilujący, że moduł jest zwolniony.|  
|[MovedReferences, metoda](icorprofilercallback-movedreferences-method.md)|Powiadamia profiler o odwołaniach do obiektów, które zostały przeniesione podczas wyrzucania elementów bezużytecznych.|  
|[ObjectAllocated, metoda](icorprofilercallback-objectallocated-method.md)|Powiadamia program profilujący, że pamięć w stercie została przypisana dla obiektu.|  
|[ObjectReferences, metoda](icorprofilercallback-objectreferences-method.md)|Powiadamia profiler o obiektach w pamięci, do których odwołuje się określony obiekt.|  
|[ObjectsAllocatedByClass, metoda](icorprofilercallback-objectsallocatedbyclass-method.md)|Powiadamia profiler o liczbie wystąpień każdej określonej klasy, które zostały utworzone od czasu poprzedniej wyrzucania elementów bezużytecznych.|  
|[RemotingClientInvocationFinished, metoda](icorprofilercallback-remotingclientinvocationfinished-method.md)|Powiadamia program profilujący, że wywołanie komunikacji zdalnej zostało uruchomione w celu ukończenia na kliencie.|  
|[RemotingClientInvocationStarted, metoda](icorprofilercallback-remotingclientinvocationstarted-method.md)|Powiadamia program profilujący o rozpoczęciu wywołania usług zdalnych.|  
|[RemotingClientReceivingReply, metoda](icorprofilercallback-remotingclientreceivingreply-method.md)|Powiadamia program profilujący, że została ukończona część połączenia zdalnego po stronie serwera, a klient otrzymuje i informacje o przetwarzaniu odpowiedzi.|  
|[RemotingClientSendingMessage, metoda](icorprofilercallback-remotingclientsendingmessage-method.md)|Powiadamia program profilujący, że klient wysyła żądanie do serwera.|  
|[RemotingServerInvocationReturned, metoda](icorprofilercallback-remotingserverinvocationreturned-method.md)|Powiadamia program profilujący, że proces zakończył wywoływanie metody w odpowiedzi na żądanie wywołania metody zdalnej.|  
|[RemotingServerInvocationStarted, metoda](icorprofilercallback-remotingserverinvocationstarted-method.md)|Powiadamia program profilujący, że proces wywołuje metodę w odpowiedzi na żądanie wywołania metody zdalnej.|  
|[RemotingServerReceivingMessage, metoda](icorprofilercallback-remotingserverreceivingmessage-method.md)|Powiadamia program profilujący, że proces otrzymuje zdalne wywołanie metody lub żądanie aktywacji.|  
|[RemotingServerSendingReply, metoda](icorprofilercallback-remotingserversendingreply-method.md)|Powiadamia program profilujący, że proces zakończył przetwarzanie żądania wywołania metody zdalnej i ma na celu przesłanie odpowiedzi za pośrednictwem kanału.|  
|[RootReferences, metoda](icorprofilercallback-rootreferences-method.md)|Powiadamia profiler o informacji o odwołaniach głównych po wyrzucaniu elementów bezużytecznych.|  
|[RuntimeResumeFinished, metoda](icorprofilercallback-runtimeresumefinished-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe wznowił wszystkie wątki środowiska uruchomieniowego i wróciło do normalnego działania.|  
|[RuntimeResumeStarted, metoda](icorprofilercallback-runtimeresumestarted-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe wznawia wszystkie wątki czasu wykonywania.|  
|[RuntimeSuspendAborted, metoda](icorprofilercallback-runtimesuspendaborted-method.md)|Powiadamia profiler, że środowisko uruchomieniowe przerywał zawieszanie czasu wykonywania.|  
|[RuntimeSuspendFinished, metoda](icorprofilercallback-runtimesuspendfinished-method.md)|Powiadamia program profilujący, że środowisko uruchomieniowe zakończyło zawieszenie wszystkich wątków czasu wykonywania.|  
|[RuntimeSuspendStarted, metoda](icorprofilercallback-runtimesuspendstarted-method.md)|Powiadamia profiler, że środowisko uruchomieniowe ma zawiesić wszystkie wątki czasu wykonywania.|  
|[RuntimeThreadResumed, metoda](icorprofilercallback-runtimethreadresumed-method.md)|Powiadamia program profilujący, że określony wątek został wznowiony po jego wstrzymaniu.|  
|[RuntimeThreadSuspended, metoda](icorprofilercallback-runtimethreadsuspended-method.md)|Powiadamia program profilujący, że określony wątek został lub wkrótce zostanie zawieszony.|  
|[Shutdown, metoda](icorprofilercallback-shutdown-method.md)|Powiadamia program profilujący, że aplikacja jest zamykana.|  
|[ThreadAssignedToOSThread, metoda](icorprofilercallback-threadassignedtoosthread-method.md)|Powiadamia program profilujący o implementacji wątku zarządzanego przy użyciu określonego wątku systemu operacyjnego (OS).|  
|[ThreadCreated, metoda](icorprofilercallback-threadcreated-method.md)|Powiadamia program profilujący o utworzeniu wątku.|  
|[ThreadDestroyed, metoda](icorprofilercallback-threaddestroyed-method.md)|Powiadamia profiler o zniszczeniu wątku.|  
|[UnmanagedToManagedTransition, metoda](icorprofilercallback-unmanagedtomanagedtransition-method.md)|Powiadamia profiler o wystąpieniu przejścia z niezarządzanego kodu do kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metodę w `ICorProfilerCallback` interfejsie (lub [ICorProfilerCallback2](icorprofilercallback2-interface.md)) w celu powiadomienia profilera o wystąpieniu zdarzenia subskrybowanego przez profiler. Jest to podstawowy interfejs wywołania zwrotnego, za pomocą którego środowisko CLR komunikuje się z profilerem kodu.  
  
 Profiler kodu musi implementować metody `ICorProfilerCallback` interfejsu. W przypadku .NET Framework w wersji 2,0 lub nowszej profiler musi również zaimplementować `ICorProfilerCallback2` metody. Każda implementacja metody musi zwracać wynik HRESULT, który ma wartość S_OK w przypadku powodzenia lub E_FAIL w przypadku niepowodzenia. Obecnie środowisko CLR ignoruje wartość HRESULT zwracaną przez poszczególne wywołania zwrotne, z wyjątkiem [ICorProfilerCallback:: ObjectReferences —](icorprofilercallback-objectreferences-method.md).  
  
 W rejestrze systemu Microsoft Windows Profiler kodu musi zarejestrować swój obiekt Component Object Model (COM), który implementuje `ICorProfilerCallback` `ICorProfilerCallback2` interfejsy i. Profiler kodu subskrybuje zdarzenia, dla których chce otrzymywać powiadomienie przez wywołanie [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md). Zwykle jest to wykonywane w implementacji profilera [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md). Profiler jest w stanie odebrać powiadomienie z środowiska uruchomieniowego, gdy zdarzenie ma miejsce lub właśnie wystąpiło w trakcie wykonywania procesu.  
  
> [!NOTE]
> Profiler rejestruje pojedynczy obiekt COM. Jeśli profiler jest przeznaczony dla .NET Framework w wersji 1,0 lub 1,1, ten obiekt COM musi zaimplementować tylko metody `ICorProfilerCallback` . Jeśli jest to element docelowy .NET Framework wersja 2,0 lub nowsza, obiekt COM musi również zaimplementować metody `ICorProfilerCallback2` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerCallback2 — Interfejs](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interfejs](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
