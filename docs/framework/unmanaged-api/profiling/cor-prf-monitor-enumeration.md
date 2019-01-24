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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a07442d990694099c9402989b41c937360842316
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569878"
---
# <a name="corprfmonitor-enumeration"></a>COR_PRF_MONITOR — Wyliczenie
Zawiera wartości, które są używane do określania zachowania, funkcji lub zdarzeń do których program profilujący chce subskrypcji.  
  
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
 Na poniższej liście sekcje `COR_PRF_MONITOR` elementów członkowskich wyliczenia według kategorii. Dostępne są następujące kategorie:  
  
-   [Nie ustawiono flagi](#None)  
  
-   [Flagi wywołania zwrotnego](#Callback)  
  
-   [Włączanie funkcji flagi](#Feature)  
  
-   [Flagi konfiguracji](#Config)  
  
-   [Flagi złożone](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a>Nie ustawiono flagi  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Flagi nie są ustawione.|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a>Flagi wywołania zwrotnego  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Włącza wszystkie zdarzenia wywołania zwrotnego.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Formanty `AppDomainCreation*` i `AppDomainShutdown*` wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Formanty `AssemblyLoad*` i `AssemblyUnload*` wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Formanty `JITCachedFunctionSearch*` wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.<br /><br /> Zachowanie tej flagi nie zostało zmienione w programie .NET Framework 2.0.|  
|`COR_PRF_MONITOR_CCW`|Formanty `COMClassicVTable*` wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Formanty `ClassLoad*` i `ClassUnload*` wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Formanty `ExceptionCLRCatcher*` wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Formanty [unmanagedtomanagedtransition —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) i [managedtounmanagedtransition —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Formanty `FunctionEnter*`, `FunctionLeave*`, i `FunctionTailCall*` [profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md).|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Formanty [exceptionthrown —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md) wywołania zwrotnego i `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, i `ExceptionCatcher*` wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Formanty [functionunloadstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md) wywołania zwrotnego w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_GC`|Formanty [garbagecollectionstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), [movedreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md), [movedreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md), [ Survivingreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md), [survivingreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md), [objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), [objectsallocatedbyclass —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md), [ Rootreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md), [rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [handlecreated —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md), [handledestroyed —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md), i [finalizeableobjectqueued — ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) wywołaniami zwrotnymi w `ICorProfilerCallback*` interfejsów.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Formanty `JITCompilation*`, [jitfunctionpitched —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md), i [jitinlining —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Formanty `ModuleLoad*`, `ModuleUnload*`, i [moduleattachedtoassembly —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Formanty [objectallocated —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) wywołania zwrotnego w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_REMOTING`|Formanty `Remoting*` wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Formanty czy `Remoting*` wywołania zwrotne będzie monitorować zdarzenia asynchroniczne.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Określa, czy plik cookie jest przekazywany do `Remoting*` wywołań zwrotnych.|  
|`COR_PRF_MONITOR_SUSPENDS`|Formanty `RuntimeSuspend*`, `RuntimeResume*`, [runtimethreadsuspended —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md), i [runtimethreadresumed —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md) wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu.|  
|`COR_PRF_MONITOR_THREADS`|Formanty [threadcreated —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md), [threaddestroyed —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md), [threadassignedtoosthread —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md), i [threadnamechanged —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md) wywołaniami zwrotnymi w [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfejsów.|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a>Włączanie funkcji flagi  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Umożliwia pobieranie dokładnie `ClassID` ogólnych funkcji, wywołując [getfunctioninfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody z `COR_PRF_FRAME_INFO` wartość zwrócona przez obiekt [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) wywołania zwrotnego.|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Za pomocą śledzenia argument umożliwia [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) wywołanie zwrotne lub [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) wywołania zwrotnego i [getfunctionenter3info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) metody.|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Umożliwia śledzenie zwracane wartości przy użyciu [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) wywołanie zwrotne lub [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) wywołania zwrotnego i [getfunctionleave3info —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) metody.|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Przestarzałe.<br /><br /> W procesie debugowania nie jest obsługiwana. Ta flaga nie ma znaczenia.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Przestarzałe.<br /><br /> Umożliwia profiler umożliwiające uzyskanie mapy IL do natywnych przy użyciu [getiltonativemapping —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md). Począwszy od programu .NET Framework 2.0 środowisko uruchomieniowe zawsze śledzi IL do natywnego mapy; w związku z tym ta flaga jest zawsze traktowana jako można ustawić.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informuje środowiska uruchomieniowego, że program profilujący może być obiekt alokacji powiadomienia. Tej flagi należy ustawić podczas inicjowania. Umożliwia ona profiler można następnie użyć `COR_PRF_MONITOR_OBJECT_ALLOCATED` flagi, aby otrzymać [objectallocated —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) wywołań zwrotnych.|  
|`COR_PRF_ENABLE_REJIT`|Umożliwia wywołania [requestrejit —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) i [requestrevert —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metody. Program profilujący, należy ustawić tę flagę przy uruchamianiu.  Jeśli program profilujący określa tej flagi, musi on również określać `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Umożliwia wywołania [dostacksnapshot —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a>Flagi konfiguracji  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Zapobiega wszystkich obrazów natywnych (w tym obrazów wzmocnionych programem profilującym) podczas ładowania.  Jeśli ta flaga i `COR_PRF_USE_PROFILE_IMAGES` flagi są określone oba `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używany.|  
|`COR_PRF_DISABLE_INLINING`|Wyłącza wszystkie wbudowanie.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Wyłącza wszystkie optymalizacje kodu.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Wyłącza sprawdzanie przezroczystości zabezpieczeń, które są zazwyczaj wykonywane podczas just-in-time (JIT) kompilacja i klasa ładowania dla zestawów pełnego zaufania. Ułatwia czynność do wykonania niektórych instrumentacji.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Powoduje, że wyszukiwanie obrazów natywnych wzmocnionych programem profilującym obrazy. Jeśli nie obrazów wzmocnionych programem profilującym został znaleziony dla danego zestawu, środowisko uruchomieniowe języka wspólnego powraca do metody JIT dla tego zestawu. Jeśli ta flaga i `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flagi są określone oba `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używany.|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a>Flagi złożone  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_ALL`|Reprezentuje wszystkie `COR_PRF_MONITOR` Flaga wartości.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które można ustawić po profiler jest dołączony do uruchomionej aplikacji. W sekcji składni wskazuje poszczególne flagi, które znajdują się w tym maski bitów.|  
|`COR_PRF_MONITOR_ALL`|Włącza wszystkie zdarzenia wywołania zwrotnego.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które można ustawić tylko podczas inicjowania. Podjęcie próby zmienić dowolne z tych flag, po powrocie inicjowania `HRESULT` wartość, która wskazuje błąd.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Reprezentuje wszystkie `COR_PRF_MONITOR` flagi, które wymagają obrazów rozszerzone profilu.|  
  
## <a name="remarks"></a>Uwagi  
 A `COR_PRF_MONITOR` wartość jest używana z [icorprofilerinfo::geteventmask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody służące do definiowania powiadomienia o zdarzeniach, które wprowadza środowiska uruchomieniowego języka wspólnego profiler.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [GetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)
- [SetEventMask, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)
