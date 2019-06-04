---
title: Wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8eb622b974de350f86a586a0f07b887bffdbd61
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483066"
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>Wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
Wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT została wprowadzona w .NET Framework w wersji 2.0. .NET Framework 4 zwraca ta wartość HRESULT w przypadku dwóch scenariuszy:  
  
- Gdy profiler przejmującego wymuszone resetuje wątku należy zarejestrować kontekstu w dowolnym momencie, tak aby wątek podejmie próbę dostępu do struktur, które znajdują się w stanie niespójnym.  
  
- Gdy profiler próbuje wywołać metodę informacyjną, która wyzwala wyrzucanie elementów bezużytecznych z metody wywołania zwrotnego, która zabrania wyrzucania elementów bezużytecznych.  
  
 W poniższych sekcjach omówiono te dwa scenariusze.  
  
## <a name="hijacking-profilers"></a>Przejęcie kontroli nad Profilery  
 (W tym scenariuszu jest głównie wystąpił problem z przejmującą profilerów, mimo że istnieją przypadki, w którym profilery przejmującego nie widzą ta wartość HRESULT).  
  
 W tym scenariuszu program profilujący przejmującego wymuszone resetuje kontekst rejestru wątku w dowolnym momencie, aby wątku można wprowadzić kod programu profilującego lub wprowadź ponownie środowisko uruchomieniowe języka wspólnego (CLR) za pośrednictwem [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) metody.  
  
 Wiele identyfikatorów, profilowania API zapewnia punkt do struktur danych w środowisku CLR. Wiele `ICorProfilerInfo` wywołania jedynie odczytać informacji z tych struktur danych i przekazywać je ponownie. Jednak CLR mogą ulec zmianie rzeczy w tych struktur, jak działa, a jego może to zrobić za pomocą blokad. Załóżmy, że środowisko CLR został już przytrzymanie (lub próby uzyskania) blokady w czasie program profilujący przejęty wątku. Jeśli wątek ponownie wprowadza środowiska CLR i próbuje wykonać więcej blokady lub sprawdzić struktur, które zostały właśnie jest modyfikowany, te struktury może być w stanie niespójnym. W takich sytuacjach może łatwo wystąpić zakleszczenia i naruszenia zasad dostępu.  
  
 Ogólnie rzecz biorąc, gdy program profilujący nie przejmującego wykonuje kod wewnątrz [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metodę i wywołuje `ICorProfilerInfo` metody przy użyciu prawidłowych parametrów, należy nie zakleszczenie lub odebrać naruszenie zasad dostępu. Na przykład, kod programu profilującego, który działa wewnątrz [icorprofilercallback::classloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) metody mogą zażądać informacji o klasie przez wywołanie metody [icorprofilerinfo2::getclassidinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) Metoda. Kod może zostać wyświetlony HRESULT CORPROF_E_DATAINCOMPLETE, aby wskazać, że informacje są niedostępne; jednak go będzie nie zakleszczenie lub odbieranie naruszenie zasad dostępu. Ta klasa wywołuje `ICorProfilerInfo` są nazywane synchroniczne, ponieważ są one `ICorProfilerCallback` metody.  
  
 Jednak wątków zarządzanych, który jest wykonywany kod, który nie jest w ramach `ICorProfilerCallback` metoda jest uznawana za ustawienie wywołania asynchronicznego. W .NET Framework w wersji 1 było trudne do ustalenia, co może się zdarzyć w przypadku wywołania asynchronicznego. Wywołanie może zakleszczenie, awarii lub nadać nieprawidłową odpowiedź. .NET Framework w wersji 2.0 wprowadzono niektóre proste testy, co pozwala uniknąć tego problemu. W .NET Framework 2.0, jeśli wywołasz niebezpieczne `ICorProfilerInfo` funkcji asynchronicznie, zakończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Ogólnie rzecz biorąc wywołania asynchroniczne nie są bezpieczne. Jednak następujące metody są bezpieczne i przeznaczone do obsługi asynchronicznego wywołania:  
  
- [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
- [Getcurrentthreadid —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
- [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
- [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [Isarrayclass —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Aby uzyskać dodatkowe informacje, zobacz wpis [Dlaczego mamy CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://go.microsoft.com/fwlink/?LinkId=169156) w blogu CLR profilowania API.  
  
## <a name="triggering-garbage-collections"></a>Wyzwalanie wyrzucania elementów bezużytecznych  
 Ten scenariusz obejmuje profiler, który działa wewnątrz metody wywołania zwrotnego (na przykład jeden z `ICorProfilerCallback` metod), zabrania wyrzucania elementów bezużytecznych. Jeśli program profilujący próbuje wywołać metodę informacyjną (na przykład metoda na `ICorProfilerInfo` interfejsu) który mogą wywołać wyrzucanie elementów bezużytecznych, metodę informacyjną kończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 W poniższej tabeli przedstawiono metody wywołania zwrotnego, które może zabronić wyrzucania elementów bezużytecznych i informacyjny metod, co może powodować wyzwalanie wyrzucania elementów bezużytecznych. Jeśli program profilujący wykonuje w jednej z metod wymienionych wywołania zwrotnego, wywołuje jedną z wymienionych metod informacyjny tę metodę informacyjną kończy się niepowodzeniem wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Metody wywołania zwrotnego, które może zabronić wyrzucania elementów bezużytecznych|Metody informacyjny, które mogą powodować wyrzucania elementów bezużytecznych|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [Exceptionunwindfinallyenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [Exceptionunwindfinallyleave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [Movedreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [Objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [Rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
