---
title: Wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: 4d835f749a33d21a13be307e1524671e36496899
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440828"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>Wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT wprowadzono w .NET Framework wersji 2,0. .NET Framework 4 zwraca wynik HRESULT w dwóch scenariuszach:  
  
- Gdy profiler przejęcia zostanie wymuszony resetuje kontekst rejestracji wątku w dowolnym momencie, aby wątek próbował uzyskać dostęp do struktur, które znajdują się w stanie niespójnym.  
  
- Gdy profiler próbuje wywołać metodę informacyjną, która wyzwala wyrzucanie elementów bezużytecznych z metody wywołania zwrotnego, która zabrania wyrzucania elementów bezużytecznych.  
  
 Te dwa scenariusze zostały omówione w poniższych sekcjach.  
  
## <a name="hijacking-profilers"></a>Przejmowanie plików  
 (W tym scenariuszu występuje przede wszystkim problem z przejmowaniem plików, chociaż istnieją przypadki, w których w przypadku nieprzejętych plików można zobaczyć ten wynik HRESULT).  
  
 W tym scenariuszu przez profiler przejęcia, który wymusi resetuje kontekst rejestracji wątku w dowolnym momencie, aby wątek mógł wprowadzić kod profilera lub ponownie wprowadzić środowisko uruchomieniowe języka wspólnego (CLR) za pomocą metody [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) .  
  
 Wiele identyfikatorów, które obsługuje interfejs API profilowania, wskazuje struktury danych w środowisku CLR. Wiele `ICorProfilerInfo` wywołuje tylko informacje z tych struktur danych i przekazuje je ponownie. Jednak środowisko CLR może zmienić elementy w tych strukturach w miarę ich działania i może użyć blokad, aby to zrobić. Załóżmy, że środowisko CLR już utrzymuje (lub próbuje uzyskać) blokadę w czasie, gdy profiler przekazano wątek. Jeśli wątek ponownie przejdzie do środowiska CLR i podejmie próbę wykonania większej liczby blokad lub Przeprowadź inspekcję struktur, które były w trakcie modyfikacji, te struktury mogą być w stanie niespójnym. Zakleszczenia i naruszenia dostępu mogą w takich sytuacjach łatwo wystąpić.  
  
 Ogólnie rzecz biorąc, gdy profiler nieprzeprzejmujący wykonuje kod wewnątrz metody [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i wywołuje metodę `ICorProfilerInfo` z prawidłowymi parametrami, nie powinien zakleszczony ani odebrać naruszenia dostępu. Na przykład kod profilera, który działa w metodzie [ICorProfilerCallback:: ClassLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) , może podawać informacje o klasie przez wywołanie metody [ICorProfilerInfo2:: GetClassIDInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) . Kod może otrzymać CORPROF_E_DATAINCOMPLETE HRESULT, aby wskazać, że informacje są niedostępne; nie spowoduje to jednak zakleszczenia ani uzyskania naruszenia dostępu. Ta klasa wywołań do `ICorProfilerInfo` jest nazywana synchronicznie, ponieważ zostały wykonane z metody `ICorProfilerCallback`.  
  
 Jednak zarządzany wątek, który wykonuje kod, który nie znajduje się w metodzie `ICorProfilerCallback` jest traktowany jako wywołujący wywołanie asynchroniczne. W .NET Framework wersji 1 trudno było określić, co może się zdarzyć w wywołaniu asynchronicznym. Wywołanie może prowadzić do zakleszczenia, awarii lub udzielenia nieprawidłowej odpowiedzi. W .NET Framework w wersji 2,0 wprowadzono kilka prostych testów, które pomagają uniknąć tego problemu. W .NET Framework 2,0, jeśli wywołasz niebezpieczną funkcję `ICorProfilerInfo` asynchronicznie, zakończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Ogólnie rzecz biorąc wywołania asynchroniczne są niebezpieczne. Jednak następujące metody są bezpieczne i w pełni obsługują wywołania asynchroniczne:  
  
- [GetEventMask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
- [Getfunctioninfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
- [Getcodeinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
- [Getclassidinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Aby uzyskać dodatkowe informacje, zobacz wpis [dlaczego CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://go.microsoft.com/fwlink/?LinkId=169156) w blogu interfejsu API profilowania CLR.  
  
## <a name="triggering-garbage-collections"></a>Wyzwalanie wyrzucania elementów bezużytecznych  
 Ten scenariusz obejmuje Profiler, który działa wewnątrz metody wywołania zwrotnego (na przykład jedną z `ICorProfilerCallback` metod), która zabrania wyrzucania elementów bezużytecznych. Jeśli profiler próbuje wywołać metodę informacyjną (na przykład metodę w interfejsie `ICorProfilerInfo`), która może wyzwolić wyrzucanie elementów bezużytecznych, Metoda informacyjna kończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 W poniższej tabeli przedstawiono metody wywołania zwrotnego, które zabraniają wyrzucania elementów bezużytecznych, oraz metody informacyjne, które mogą wyzwalać odzyskiwanie pamięci. Jeśli profiler wykonuje się w jednej z wymienionych metod wywołania zwrotnego i wywołuje jedną z wymienionych metod informacyjnych, ta metoda informacyjna kończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Metody wywołania zwrotnego, które uniemożliwiają odzyskiwanie pamięci|Metody informacyjne wyzwalające odzyskiwanie pamięci|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [Rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
