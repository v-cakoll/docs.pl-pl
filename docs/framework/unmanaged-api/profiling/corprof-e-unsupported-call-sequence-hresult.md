---
title: Wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: b4ab5c8f7cdca1303cb4fbbc4fa39db3c5977c15
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867012"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>Wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT

CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT wprowadzono w .NET Framework wersji 2,0. .NET Framework 4 zwraca wynik HRESULT w dwóch scenariuszach:  
  
- Gdy profiler przejęcia zostanie wymuszony resetuje kontekst rejestracji wątku w dowolnym momencie, aby wątek próbował uzyskać dostęp do struktur, które znajdują się w stanie niespójnym.  
  
- Gdy profiler próbuje wywołać metodę informacyjną, która wyzwala wyrzucanie elementów bezużytecznych z metody wywołania zwrotnego, która zabrania wyrzucania elementów bezużytecznych.  
  
Te dwa scenariusze zostały omówione w poniższych sekcjach.  
  
## <a name="hijacking-profilers"></a>Przejmowanie plików  

  (W tym scenariuszu występuje przede wszystkim problem z przejmowaniem plików, chociaż istnieją przypadki, w których w przypadku nieprzejętych plików można zobaczyć ten wynik HRESULT).  
  
 W tym scenariuszu, w którym Profiler przejęcia, resetuje kontekst rejestracji wątku w dowolnym momencie, aby wątek mógł wprowadzić kod profilera lub ponownie wprowadzić środowisko uruchomieniowe języka wspólnego (CLR) za pomocą metody [ICorProfilerInfo](icorprofilerinfo-interface.md) .  
  
 Wiele identyfikatorów, które obsługuje interfejs API profilowania, wskazuje struktury danych w środowisku CLR. Wiele `ICorProfilerInfo` wywołuje tylko informacje z tych struktur danych i przekazuje je ponownie. Jednak środowisko CLR może zmienić elementy w tych strukturach w miarę ich działania i może użyć blokad, aby to zrobić. Załóżmy, że środowisko CLR już utrzymuje (lub próbuje uzyskać) blokadę w czasie, gdy profiler przekazano wątek. Jeśli wątek ponownie wprowadzi środowisko CLR i podejmie próbę wykonania większej liczby blokad lub Przeprowadź inspekcję struktur, które były w trakcie modyfikacji, te struktury mogą być w stanie niespójnym. Zakleszczenia i naruszenia dostępu mogą w takich sytuacjach łatwo wystąpić.  
  
 Ogólnie rzecz biorąc, gdy profiler nieprzeprzejmujący wykonuje kod wewnątrz metody [ICorProfilerCallback](icorprofilercallback-interface.md) i wywołuje metodę `ICorProfilerInfo` z prawidłowymi parametrami, nie powinien zakleszczony ani odebrać naruszenia dostępu. Na przykład kod profilera, który działa w metodzie [ICorProfilerCallback:: ClassLoadFinished —](icorprofilercallback-classloadfinished-method.md) , może podawać informacje o klasie przez wywołanie metody [ICorProfilerInfo2:: GetClassIDInfo2 —](icorprofilerinfo2-getclassidinfo2-method.md) . Kod może otrzymać CORPROF_E_DATAINCOMPLETE HRESULT, aby wskazać, że informacje są niedostępne. Nie spowoduje to jednak zakleszczenia ani uzyskania naruszenia dostępu. Te wywołania do `ICorProfilerInfo` są uważane za synchroniczne, ponieważ zostały wykonane z metody `ICorProfilerCallback`.  
  
 Jednak zarządzany wątek, który wykonuje kod, który nie znajduje się w metodzie `ICorProfilerCallback` jest traktowany jako wywołujący wywołanie asynchroniczne. W .NET Framework wersji 1 trudno było określić, co może się zdarzyć w wywołaniu asynchronicznym. Wywołanie może prowadzić do zakleszczenia, awarii lub udzielenia nieprawidłowej odpowiedzi. W .NET Framework w wersji 2,0 wprowadzono kilka prostych testów, które pomagają uniknąć tego problemu. W .NET Framework 2,0, jeśli wywołasz niebezpieczną funkcję `ICorProfilerInfo` asynchronicznie, zakończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Ogólnie rzecz biorąc wywołania asynchroniczne są niebezpieczne. Jednak następujące metody są bezpieczne i w pełni obsługują wywołania asynchroniczne:  
  
- [GetEventMask](icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID —](icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext](icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP —](icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](icorprofilerinfo-getfunctioninfo-method.md)  
  
- [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo —](icorprofilerinfo-getcodeinfo-method.md)  
  
- [Getcodeinfo2 —](icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo —](icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass —](icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot —](icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Aby uzyskać więcej informacji, zobacz wpis [dlaczego CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://docs.microsoft.com/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) w blogu interfejsu API profilowania CLR.  
  
## <a name="triggering-garbage-collections"></a>Wyzwalanie wyrzucania elementów bezużytecznych  
 Ten scenariusz obejmuje Profiler, który działa wewnątrz metody wywołania zwrotnego (na przykład jedną z `ICorProfilerCallback` metod), która zabrania wyrzucania elementów bezużytecznych. Jeśli profiler próbuje wywołać metodę informacyjną (na przykład metodę w interfejsie `ICorProfilerInfo`), która może wyzwolić wyrzucanie elementów bezużytecznych, Metoda informacyjna kończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 W poniższej tabeli przedstawiono metody wywołania zwrotnego, które zabraniają wyrzucania elementów bezużytecznych, oraz metody informacyjne, które mogą wyzwalać odzyskiwanie pamięci. Jeśli profiler wykonuje się w jednej z wymienionych metod wywołania zwrotnego i wywołuje jedną z wymienionych metod informacyjnych, ta metoda informacyjna kończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Metody wywołania zwrotnego, które uniemożliwiają odzyskiwanie pamięci|Metody informacyjne wyzwalające odzyskiwanie pamięci|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread —](icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter —](icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave —](icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter —](icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted —](icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished —](icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended —](icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences —](icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences —](icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass —](icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [Rootreferences2 —](icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated —](icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo —](icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule —](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interfejs](icorprofilercallback3-interface.md)
- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
