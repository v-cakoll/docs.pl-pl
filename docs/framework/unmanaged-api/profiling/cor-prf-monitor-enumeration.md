---
title: "COR_PRF_MONITOR — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6dc135681d11a496dbc27553d46a5d101b6d7b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfmonitor-enumeration"></a>COR_PRF_MONITOR — Wyliczenie
Zawiera wartości, które są używane do określania zachowania, funkcji lub zdarzeń do których chce subskrypcji profilera.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 Na poniższej liście sekcje `COR_PRF_MONITOR` elementy członkowskie wyliczenia według kategorii. Dostępne są następujące kategorie:  
  
-   [Nie ustawiono flagi](#None)  
  
-   [Flagi wywołania zwrotnego](#Callback)  
  
-   [Włączanie funkcji flagi](#Feature)  
  
-   [Flagi konfiguracji](#Config)  
  
-   [Flagi złożone](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a>Nie ustawiono flagi  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Ustawiono żadnych flag.|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a>Flagi wywołania zwrotnego  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Włącza wszystkie zdarzenia wywołania zwrotnego.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Formanty `AppDomainCreation*` i `AppDomainShutdown*` wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Formanty `AssemblyLoad*` i `AssemblyUnload*` wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Formanty `JITCachedFunctionSearch*` wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.<br /><br /> Zachowanie ta flaga jest zmienione w programie .NET Framework w wersji 2.0.|  
|`COR_PRF_MONITOR_CCW`|Formanty `COMClassicVTable*` wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Formanty `ClassLoad*` i `ClassUnload*` wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Formanty `ExceptionCLRCatcher*` wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Formanty [UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) i [ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) — interfejs|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Formanty `FunctionEnter*`, `FunctionLeave*`, i `FunctionTailCall*` [statyczne funkcje globalne profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md).|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Formanty [ExceptionThrown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md) wywołania zwrotnego i `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, i `ExceptionCatcher*` wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Formanty [FunctionUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md) wywołania zwrotnego w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_GC`|Formanty [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md), [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md), [ SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md), [ RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md), [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md), i [FinalizeableObjectQueued ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) wywołania zwrotne w `ICorProfilerCallback*` interfejsów.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Formanty `JITCompilation*`, [JITFunctionPitched](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md), i [JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Formanty `ModuleLoad*`, `ModuleUnload*`, i [ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Formanty [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) wywołania zwrotnego w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_REMOTING`|Formanty `Remoting*` wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Formanty czy `Remoting*` wywołania zwrotne będzie monitorować zdarzenia asynchroniczne.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Określa, czy plik cookie jest przekazywany do `Remoting*` wywołań zwrotnych.|  
|`COR_PRF_MONITOR_SUSPENDS`|Formanty `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md), i [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md) wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_THREADS`|Formanty [ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md), [ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md), i [ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md) wywołania zwrotne w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfejsów.|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a>Włączanie funkcji flagi  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Umożliwia pobieranie dokładnie `ClassID` dla ogólnych funkcji przez wywołanie metody [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody z `COR_PRF_FRAME_INFO` wartość zwrócona przez [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) wywołania zwrotnego.|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Za pomocą śledzenia argument umożliwia [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) wywołania zwrotnego lub [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) wywołania zwrotnego i [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) metody.|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Umożliwia śledzenie zwracanych wartości przy użyciu [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) wywołania zwrotnego lub [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) wywołania zwrotnego i [GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) metody.|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Przestarzałe.<br /><br /> W procesie debugowanie nie jest obsługiwane. Ta flaga nie ma znaczenia.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Przestarzałe.<br /><br /> Umożliwia profilera można uzyskać mapy IL do natywnego przy użyciu [GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md). Począwszy od programu .NET Framework 2.0, środowisko uruchomieniowe zawsze śledzi mapy IL do natywnego; w związku z tym ta flaga jest uznawany za zawsze należy ustawić wartość.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informuje środowiska uruchomieniowego, że profiler może być obiekt alokacji powiadomienia. Ta flaga należy ustawić podczas inicjowania. Umożliwia profiler do późniejszego użycia `COR_PRF_MONITOR_OBJECT_ALLOCATED` flagę w celu odbierania [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) wywołań zwrotnych.|  
|`COR_PRF_ENABLE_REJIT`|Włącza wywołań [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) i [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metody. Profilera musi ustawić tę flagę podczas uruchamiania.  Jeśli profilera określa tej flagi, musi również określać `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Włącza wywołań [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a>Flagi konfiguracji  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Zapobiega ładowania wszystkich obrazów natywnych (w tym ulepszone profilera obrazy).  Jeśli ta flaga i `COR_PRF_USE_PROFILE_IMAGES` flagi są określone oba, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używany.|  
|`COR_PRF_DISABLE_INLINING`|Wyłącza wszystkie ze śródwierszowaniem.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Wyłącza wszystkie optymalizacje kodu.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Wyłącza sprawdzanie przezroczystość zabezpieczeń, które są zazwyczaj wykonywane podczas just in time (JIT) kompilacji i klasa ładowania dla zestawów pełnego zaufania. Ułatwia czynność do wykonania niektórych instrumentacji.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Powoduje, że wyszukiwanie obrazu macierzystego do wyszukania rozszerzone profilera obrazów. Jeśli dla danego zestawu zostanie znaleziony żadnego obrazu enhanced profilera, środowisko uruchomieniowe języka wspólnego powraca do JIT dla tego zestawu. Jeśli ta flaga i `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flagi są określone oba, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używany.|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a>Flagi złożone  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_ALL`|Reprezentuje wszystkie `COR_PRF_MONITOR` Flaga wartości.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które można ustawić po profiler jest dołączony do uruchomionej aplikacji. Sekcja składni wskazuje indywidualne flagi, które znajdują się w tym maski.|  
|`COR_PRF_MONITOR_ALL`|Włącza wszystkie zdarzenia wywołania zwrotnego.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które można ustawić tylko podczas inicjowania. Aby zmienić dowolne z tych flag, po powrocie inicjowania w trakcie `HRESULT` wartość, która wskazuje błąd.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które wymagają rozszerzone profilu obrazów.|  
  
## <a name="remarks"></a>Uwagi  
 A `COR_PRF_MONITOR` wartość jest używana z [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metod, aby zdefiniować powiadomienia o zdarzeniach, które wprowadza środowisko uruchomieniowe języka wspólnego profiler.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [GetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
 [SetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)
