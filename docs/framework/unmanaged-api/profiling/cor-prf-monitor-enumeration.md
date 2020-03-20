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
ms.openlocfilehash: b6c3dc78b9c503747c7a2d404706eb797790b931
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175203"
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
 W poniższych `COR_PRF_MONITOR` sekcjach listy członków wyliczenia według kategorii. Kategorie to:  
  
- [Nie ustawiono flag](#None)  
  
- [Flagi oddzwaniania zwrotnego](#Callback)  
  
- [Flagi włączające funkcje](#Feature)  
  
- [Flagi konfiguracji](#Config)  
  
- [Flagi kompozytowe](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a>Nie ustawiono flag  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Nie ustawiono żadnych flag.|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a>Flagi oddzwaniania zwrotnego  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Włącza wszystkie zdarzenia wywołania zwrotnego.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Steruje `AppDomainCreation*` `AppDomainShutdown*` i wywołania zwrotne w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Steruje `AssemblyLoad*` `AssemblyUnload*` i wywołania zwrotne w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Steruje `JITCachedFunctionSearch*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)<br /><br /> Zachowanie tej flagi zostanie zmienione w .NET Framework w wersji 2.0.|  
|`COR_PRF_MONITOR_CCW`|Steruje `COMClassicVTable*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Steruje `ClassLoad*` `ClassUnload*` i wywołania zwrotne w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Steruje `ExceptionCLRCatcher*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Steruje wywołaniami zwrotnymi [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) i [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) w interfejsie [ICorProfilerCallback](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Steruje `FunctionEnter*` `FunctionLeave*`programem `FunctionTailCall*`, i [profilowaniem globalnych funkcji statycznych](profiling-global-static-functions.md).|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Steruje [exceptionthrown](icorprofilercallback-exceptionthrown-method.md) wywołania `ExceptionSearch*` `ExceptionOSHandler*`zwrotnego i , `ExceptionUnwind*`, i `ExceptionCatcher*` wywołania zwrotne w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Steruje [wywołaniem zwrotnym FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_GC`|Steruje [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md) `ICorProfilerCallback*` , [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md)i [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) wywołania zwrotne w interfejsach. Po `COR_PRF_MONITOR_GC` przydzieleniu równoczesnych wyrzucania elementów bezużytecznych jest wyłączony.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Steruje `JITCompilation*`wywołaniami zwrotnymi , [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md)i [JITInlining](icorprofilercallback-jitinlining-method.md) w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Steruje `ModuleLoad*` `ModuleUnload*`, , i [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotne w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Steruje [objectallocated](icorprofilercallback-objectallocated-method.md) wywołania zwrotnego w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_REMOTING`|Steruje `Remoting*` wywołaniami zwrotnymi w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Określa, `Remoting*` czy wywołania zwrotne będą monitorować zdarzenia asynchroniczne.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Określa, czy plik cookie `Remoting*` jest przekazywany do wywołań zwrotnych.|  
|`COR_PRF_MONITOR_SUSPENDS`|Steruje `RuntimeSuspend*` `RuntimeResume*`, , [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)i [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) wywołania zwrotne w interfejsie [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_THREADS`|Steruje [wątkiemtworzone](icorprofilercallback-threadcreated-method.md), [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)i [ThreadNameZmienione](icorprofilercallback2-threadnamechanged-method.md) wywołania zwrotne w interfejsach [ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback2.](icorprofilercallback2-interface.md)|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a>Flagi włączające funkcje  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Umożliwia pobieranie `ClassID` dokładnej dla funkcji ogólnej, wywołując [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) `COR_PRF_FRAME_INFO` metoda z wartością zwróconą przez [functionenter2](functionenter2-function.md) wywołania zwrotnego.|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Umożliwia śledzenie argumentów przy użyciu wywołania zwrotnego [FunctionEnter2](functionenter2-function.md) lub wywołania zwrotnego [FunctionEnter3WithInfo](functionenter3withinfo-function.md) i metody [GetFunctionEnter3Info.](icorprofilerinfo3-getfunctionenter3info-method.md)|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Umożliwia śledzenie zwracanych wartości przy użyciu wywołania zwrotnego [FunctionLeave2](functionleave2-function.md) lub [functionleave3WithInfo](functionleave3withinfo-function.md) wywołania zwrotnego i [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) metody.|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Przestarzałe.<br /><br /> Debugowanie w procesie nie jest obsługiwane. Ta flaga nie ma wpływu.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Przestarzałe.<br /><br /> Umożliwia profilerowi uzyskanie map IL-to-native za pomocą [programu GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md). Począwszy od programu .NET Framework 2.0, środowisko wykonawcze zawsze śledzi mapy IL-to-native; w związku z tym ta flaga jest zawsze uważane za ustawione.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informuje środowisko wykonawcze, że profiler może chcieć powiadomień o alokacji obiektów. Ta flaga musi być ustawiona podczas inicjowania. Umożliwia profilera następnie użyć `COR_PRF_MONITOR_OBJECT_ALLOCATED` flagi do odbierania [objectallocated](icorprofilercallback-objectallocated-method.md) wywołania zwrotne.|  
|`COR_PRF_ENABLE_REJIT`|Włącza wywołania [Do RequestReJIT](icorprofilerinfo4-requestrejit-method.md) i [RequestRevert](icorprofilerinfo4-requestrevert-method.md) metody. Profiler musi ustawić tę flagę podczas uruchamiania.  Jeśli profiler określa tę flagę, `COR_PRF_DISABLE_ALL_NGEN_IMAGES`musi również określić .|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Włącza wywołania [do DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metody.|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a>Flagi konfiguracji  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Zapobiega ładowaniu wszystkich obrazów natywnych (w tym obrazów z profilem).  Jeśli ta flaga i flaga `COR_PRF_USE_PROFILE_IMAGES` są określone, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używany.|  
|`COR_PRF_DISABLE_INLINING`|Wyłącza wszystkie inline.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Wyłącza wszystkie optymalizacje kodu.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Wyłącza kontroli przezroczystości zabezpieczeń, które są zwykle wykonywane podczas kompilacji just-in-time (JIT) i ładowania klas dla zestawów pełnego zaufania. Może to ułatwić niektóre instrumentacji do wykonania.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Powoduje, że natywne wyszukiwanie obrazów wyszukuje obrazy z profilem. Jeśli nie profiler rozszerzony obraz zostanie znaleziony dla danego zestawu, środowisko uruchomieniowe języka wspólnego przechodzi z powrotem do JIT dla tego zestawu. Jeśli ta flaga i flaga `COR_PRF_DISABLE_ALL_NGEN_IMAGES` są określone, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jest używany.|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a>Flagi kompozytowe  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_ALL`|Reprezentuje `COR_PRF_MONITOR` wszystkie wartości flagi.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Reprezentuje `COR_PRF_MONITOR` wszystkie flagi, które można ustawić po profiler jest dołączony do uruchomionej aplikacji. Sekcja składnia wskazuje poszczególne flagi, które są obecne w tej masce bitowej.|  
|`COR_PRF_MONITOR_ALL`|Włącza wszystkie zdarzenia wywołania zwrotnego.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Reprezentuje `COR_PRF_MONITOR` wszystkie flagi, które można ustawić tylko podczas inicjowania. Próba zmiany dowolnej z tych flag `HRESULT` po inicjalizacji zwraca wartość, która wskazuje błąd.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Reprezentuje `COR_PRF_MONITOR` wszystkie flagi, które wymagają obrazów o rozszerzonej profili.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość `COR_PRF_MONITOR` jest używana z [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) metody do definiowania powiadomień o zdarzeniach, które środowisko uruchomieniowe języka wspólnego sprawia, że do profilera.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Profilowanie — wyliczenia](profiling-enumerations.md)
- [GetEventMask, metoda](icorprofilerinfo-geteventmask-method.md)
- [SetEventMask, metoda](icorprofilerinfo-seteventmask-method.md)
