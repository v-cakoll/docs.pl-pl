---
title: Wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3694e08555df3ad91fbfcc35b6eb385bd24ce3c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>Wynik CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT została wprowadzona w programie .NET Framework w wersji 2.0. [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Zwraca HRESULT to w przypadku dwóch scenariuszy:  
  
-   Podczas profilera przechwyceniu wymuszone przez wątek należy zarejestrować kontekstu w dowolnej chwili, dzięki czemu wątek próbuje uzyskać dostęp struktur, które znajdują się w stanie niespójnym.  
  
-   Kiedy profiler próbuje wywoływanie metody informacyjne, które wyzwala wyrzucanie elementów bezużytecznych z metody wywołania zwrotnego, która jest zabronione wyrzucanie elementów bezużytecznych.  
  
 W poniższych sekcjach omówiono tych dwóch scenariuszy.  
  
## <a name="hijacking-profilers"></a>Przejęcie kontroli profilowania  
 (Ten scenariusz jest głównie wystąpił problem z przejmującą profilowania, mimo że istnieją przypadki, w którym profilowania z systemem innym niż przejęcie kontroli można zobaczyć tego HRESULT).  
  
 W tym scenariuszu profilera przechwyceniu wymuszanie resetuje kontekstu rejestru wątku w dowolnej chwili, aby wątku można wprowadzić kod profilera lub wprowadź ponownie środowisko uruchomieniowe języka wspólnego (CLR) za pośrednictwem [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) metody.  
  
 Wiele identyfikatorów, że interfejsu API profilowania udostępnia punkt do struktury danych w środowisku CLR. Wiele `ICorProfilerInfo` wywołań tylko odczytać informacji z tych struktur danych i przesłać je. Środowiska CLR może jednak zmienić rzeczy w tych konstrukcji, jak działa, i może używać blokad w tym celu. Załóżmy, że środowisko CLR zostało już zawierający (lub próby uzyskania) blokady w czasie profilera przejęty wątku. Jeśli wątek ponownie wprowadza CLR, próbuje wykonać więcej blokad lub sprawdzić struktur, które były właśnie trwa modyfikowanie tych struktur może być w niespójnym stanie. W takich sytuacjach może łatwo wystąpić zakleszczenie i naruszenia zasad dostępu.  
  
 Ogólnie rzecz biorąc, gdy profilera z systemem innym niż przechwyceniu wykonuje kodu wewnątrz [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) — metoda i wywołuje `ICorProfilerInfo` metody z prawidłowych parametrów, należy nie zakleszczenie lub odebrać naruszenia zasad dostępu. Na przykład kod profilera działają w obrębie [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) metody może poprosić o informacje o klasie wywołując [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) Metoda. Kod może pojawić się w wyniku HRESULT CORPROF_E_DATAINCOMPLETE, aby wskazać, że informacje są niedostępne; jednak go nie zostanie zakleszczenie ani odbierać naruszenia zasad dostępu. Ta klasa wywołuje `ICorProfilerInfo` są nazywane synchroniczne, ponieważ są one `ICorProfilerCallback` metody.  
  
 Jednak zarządzanego wątku, który jest wykonywany kod, który nie jest w `ICorProfilerCallback` metody jest uznawany za wykonywać wywołania asynchronicznego. W programie .NET Framework w wersji 1 jest trudne do ustalenia, co może się zdarzyć w wywołanie asynchroniczne. Wywołanie może zakleszczenie, awarii lub podać nieprawidłową odpowiedź. .NET Framework w wersji 2.0 wprowadzono proste testy pozwala uniknąć tego problemu. W .NET Framework 2.0, można wywołać niebezpieczne `ICorProfilerInfo` funkcji asynchronicznie, jego wykonanie nie powiodło się CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Ogólnie rzecz biorąc wywołania asynchroniczne nie są bezpieczne. Jednak następujące metody są bezpieczne i specjalnie obsługuje asynchroniczne wywołania:  
  
-   [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
-   [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
-   [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
-   [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
-   [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
-   [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
-   [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
-   [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
-   [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
-   [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
-   [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
-   [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
-   [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
-   [IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
-   [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
-   [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Aby uzyskać dodatkowe informacje, zobacz wpis [Dlaczego mamy CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](http://go.microsoft.com/fwlink/?LinkId=169156) w blogu API profilowania środowiska CLR.  
  
## <a name="triggering-garbage-collections"></a>Wyzwolenie wyrzucanie elementów bezużytecznych  
 Ten scenariusz obejmuje profilera, na którym działa wewnątrz metody wywołania zwrotnego (na przykład jeden z `ICorProfilerCallback` metody) który zabrania wyrzucanie elementów bezużytecznych. Jeśli profilera próba wywołania metody informacyjny (na przykład metoda na `ICorProfilerInfo` interfejsu) które mogą wyzwalać wyrzucania elementów bezużytecznych, informacyjny metoda kończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 W poniższej tabeli przedstawiono metody wywołania zwrotnego, które zabraniać wyrzucania i informacyjną metody, które mogą wyzwalać wyrzucanie elementów bezużytecznych. Jeśli profilera wewnątrz jednej z metod wywołania zwrotnego wymienionych i jedną z wymienionych metod informacyjny, informacyjny metoda kończy się niepowodzeniem z CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Metody wywołania zwrotnego, które zabraniać wyrzucanie elementów bezużytecznych|Metody informacyjny, wyzwalających wyrzucanie elementów bezużytecznych|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
