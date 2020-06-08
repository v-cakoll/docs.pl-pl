---
title: COR_PRF_MONITOR — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 1ff167121a5bb752c70edd2c5901133503326bea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500809"
---
# <a name="cor_prf_monitor-enumeration"></a>COR_PRF_MONITOR — Wyliczenie
Zawiera wartości, które są używane do określania zachowania, możliwości lub zdarzeń, do których profiler chce subskrybować.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 W poniższych sekcjach wymieniono `COR_PRF_MONITOR` elementy członkowskie wyliczenia według kategorii. Kategorie są następujące:  
  
- [Nie ustawiono flag](#None)  
  
- [Flagi wywołania zwrotnego](#Callback)  
  
- [Flagi włączające funkcję](#Feature)  
  
- [Flagi konfiguracji](#Config)  
  
- [Flagi złożone](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a>Nie ustawiono flag  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Nie ustawiono żadnych flag.|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a>Flagi wywołania zwrotnego  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Włącza wszystkie zdarzenia wywołania zwrotnego.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Kontroluje `AppDomainCreation*` `AppDomainShutdown*` wywołania zwrotne i w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Kontroluje `AssemblyLoad*` `AssemblyUnload*` wywołania zwrotne i w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Steruje `JITCachedFunctionSearch*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .<br /><br /> Zachowanie tej flagi zostanie zmienione w .NET Framework w wersji 2,0.|  
|`COR_PRF_MONITOR_CCW`|Steruje `COMClassicVTable*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Kontroluje `ClassLoad*` `ClassUnload*` wywołania zwrotne i w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Steruje `ExceptionCLRCatcher*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Kontroluje wywołania zwrotne [UnmanagedToManagedTransition —](icorprofilercallback-unmanagedtomanagedtransition-method.md) i [ManagedToUnmanagedTransition —](icorprofilercallback-managedtounmanagedtransition-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Steruje `FunctionEnter*` `FunctionLeave*` `FunctionTailCall*` [globalnymi funkcjami statycznymi](profiling-global-static-functions.md), i profilowania.|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Steruje [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) wywołaniem zwrotnym ExceptionThrown — `ExceptionSearch*` oraz `ExceptionOSHandler*` `ExceptionUnwind*` `ExceptionCatcher*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Steruje wywołaniem zwrotnym [FunctionUnloadStarted —](icorprofilercallback-functionunloadstarted-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_GC`|Kontroluje [GarbageCollectionStarted —](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences —](icorprofilercallback-movedreferences-method.md), [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences —](icorprofilercallback2-survivingreferences-method.md), SurvivingReferences2 — [,](icorprofilercallback4-survivingreferences2-method.md) [ObjectReferences —](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass —](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences —](icorprofilercallback-rootreferences-method.md), [RootReferences2 —](icorprofilercallback2-rootreferences2-method.md), [HandleCreated —](icorprofilercallback2-handlecreated-method.md)i HandleDestroyed — [wywołania](icorprofilercallback2-handledestroyed-method.md)zwrotne [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) w `ICorProfilerCallback*` interfejsach. Gdy `COR_PRF_MONITOR_GC` jest przydzielono, współbieżne wyrzucanie elementów bezużytecznych jest wyłączone.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Kontroluje `JITCompilation*` wywołania zwrotne, [JITFunctionPitched —](icorprofilercallback-jitfunctionpitched-method.md)i [JITInlining —](icorprofilercallback-jitinlining-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Kontroluje `ModuleLoad*` `ModuleUnload*` wywołania zwrotne, i [ModuleAttachedToAssembly —](icorprofilercallback-moduleattachedtoassembly-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Steruje wywołaniem zwrotnym [ObjectAllocated —](icorprofilercallback-objectallocated-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_REMOTING`|Steruje `Remoting*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Określa, czy `Remoting*` wywołania zwrotne będą monitorować zdarzenia asynchroniczne.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Określa, czy plik cookie jest przesyłany do `Remoting*` wywołania zwrotnego.|  
|`COR_PRF_MONITOR_SUSPENDS`|Kontroluje `RuntimeSuspend*` `RuntimeResume*` wywołania zwrotne,, [RuntimeThreadSuspended —](icorprofilercallback-runtimethreadsuspended-method.md)i [RuntimeThreadResumed —](icorprofilercallback-runtimethreadresumed-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_THREADS`|Kontroluje wywołania zwrotne [ThreadCreated —](icorprofilercallback-threadcreated-method.md), [ThreadDestroyed —](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread —](icorprofilercallback-threadassignedtoosthread-method.md)i [ThreadNameChanged —](icorprofilercallback2-threadnamechanged-method.md) w interfejsach [ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback2](icorprofilercallback2-interface.md) .|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a>Flagi włączające funkcję  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Włącza pobieranie dokładne `ClassID` dla funkcji ogólnej przez wywołanie metody [GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) z `COR_PRF_FRAME_INFO` wartością zwracaną przez wywołanie zwrotne [FunctionEnter2](functionenter2-function.md) .|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Włącza śledzenie argumentów przy użyciu wywołania zwrotnego [FunctionEnter2](functionenter2-function.md) lub wywołania zwrotnego [FunctionEnter3WithInfo](functionenter3withinfo-function.md) i metody [GetFunctionEnter3Info —](icorprofilerinfo3-getfunctionenter3info-method.md) .|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Włącza śledzenie wartości zwracanych przy użyciu wywołania zwrotnego [FunctionLeave2](functionleave2-function.md) lub metody wywołania zwrotnego [FunctionLeave3WithInfo](functionleave3withinfo-function.md) i [GetFunctionLeave3Info —](icorprofilerinfo3-getfunctionleave3info-method.md) .|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Przestarzałe.<br /><br /> Debugowanie procesu nie jest obsługiwane. Ta flaga nie ma żadnego wpływu.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Przestarzałe.<br /><br /> Umożliwia programowi Profiler uzyskanie map IL-to-native przy użyciu [GetILToNativeMapping —](icorprofilerinfo-getiltonativemapping-method.md). Począwszy od .NET Framework 2,0, środowisko uruchomieniowe zawsze śledzi mapowania IL-to-natywne; w związku z tym Flaga ta jest zawsze uznawana za ustawioną.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informuje środowisko uruchomieniowe, że profiler może chcieć otrzymywać powiadomienia dotyczące alokacji obiektów. Ta flaga musi być ustawiona podczas inicjowania. Umożliwia profilerowi użycie `COR_PRF_MONITOR_OBJECT_ALLOCATED` flagi, aby otrzymać wywołania zwrotne [ObjectAllocated —](icorprofilercallback-objectallocated-method.md) .|  
|`COR_PRF_ENABLE_REJIT`|Włącza wywołania metod [RequestReJIT —](icorprofilerinfo4-requestrejit-method.md) i [RequestRevert —](icorprofilerinfo4-requestrevert-method.md) . Profiler musi ustawić tę flagę podczas uruchamiania.  Jeśli profiler określa tę flagę, musi także określić `COR_PRF_DISABLE_ALL_NGEN_IMAGES` .|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Włącza wywołania metody [DoStackSnapshot —](icorprofilerinfo2-dostacksnapshot-method.md) .|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a>Flagi konfiguracji  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Zapobiega ładowaniu wszystkich obrazów natywnych (w tym obrazów ulepszonych profilera).  Jeśli ta flaga i `COR_PRF_USE_PROFILE_IMAGES` Flaga są określone, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używana.|  
|`COR_PRF_DISABLE_INLINING`|Wyłącza wszystkie znaki wykreślania.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Wyłącza wszystkie optymalizacje kodu.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Wyłącza kontrole przezroczystości zabezpieczeń, które zwykle są wykonywane podczas kompilacji w czasie just-in-Time (JIT) i załadowanie klasy dla zestawów o pełnym zaufaniu. Może to ułatwić wykonywanie niektórych Instrumentacji.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Powoduje, że wyszukiwanie obrazów natywnych jest wyszukiwane w obrazach z ulepszonym profilerem. Jeśli dla danego zestawu nie zostanie znaleziony obraz z ulepszonym profilerem, środowisko uruchomieniowe języka wspólnego powróci do trybu JIT dla tego zestawu. Jeśli ta flaga i `COR_PRF_DISABLE_ALL_NGEN_IMAGES` Flaga są określone, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używana.|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a>Flagi złożone  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_ALL`|Reprezentuje wszystkie `COR_PRF_MONITOR` wartości flag.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które można ustawić po dołączeniu profilera do uruchomionej aplikacji. Sekcja składnia wskazuje poszczególne flagi, które znajdują się w tej masce bitowej.|  
|`COR_PRF_MONITOR_ALL`|Włącza wszystkie zdarzenia wywołania zwrotnego.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które można ustawić tylko podczas inicjowania. Próba zmiany którejkolwiek z tych flag po inicjalizacji zwróci `HRESULT` wartość wskazującą niepowodzenie.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które wymagają obrazów z rozszerzonym profilem.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_PRF_MONITOR`Wartość jest używana z metodami [ICorProfilerInfo:: GetEventMask —](icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) do definiowania powiadomień o zdarzeniach, które środowisko uruchomieniowe języka wspólnego zapewnia Profiler.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
- [GetEventMask, metoda](icorprofilerinfo-geteventmask-method.md)
- [SetEventMask, metoda](icorprofilerinfo-seteventmask-method.md)
