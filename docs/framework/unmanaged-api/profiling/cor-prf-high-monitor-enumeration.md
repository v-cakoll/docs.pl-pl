---
title: Wyliczenie COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 03fa33e0e2b4175d9f82bc6021731d58805da258
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123994"
---
# <a name="cor_prf_high_monitor-enumeration"></a>Wyliczenie COR_PRF_HIGH_MONITOR
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Oferuje flagi oprócz tych, które znajdują się w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia, które profiler może określić do metody [ICorProfilerInfo5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) podczas ładowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Nie ustawiono żadnych flag.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Kontroluje wywołanie zwrotne [ICorProfilerCallback6:: GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) w celu dodania odwołań do zestawu podczas przeszukiwania odwołań do zestawów CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Kontroluje wywołanie zwrotne [ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) dla aktualizacji strumienia symboli skojarzonego z modułem w pamięci.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Steruje wywołaniem zwrotnym [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) , aby wskazać, kiedy metoda dynamiczna została odtworzona i zwolniona. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|Tylko .NET Core 3,0 i nowsze wersje: wyłącza [kompilację warstwową](../../../core/whats-new/dotnet-core-3-0.md) dla plików profilowanych.|
|`COR_PRF_HIGH_BASIC_GC`|Tylko .NET Core 3,0 i nowsze wersje: zapewnia uproszczoną opcję profilowania GC w porównaniu do [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md). Kontroluje tylko wywołania zwrotne [GarbageCollectionStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)i [GetGenerationBounds —](icorprofilerinfo2-getgenerationbounds-method.md) . W przeciwieństwie do flagi `COR_PRF_MONITOR_GC`, `COR_PRF_HIGH_BASIC_GC` nie wyłącza współbieżnego wyrzucania elementów bezużytecznych.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|Tylko .NET Core 3,0 i nowsze wersje: włącza wywołania zwrotne [MovedReferences —](icorprofilercallback-movedreferences-method.md) i [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) tylko do kompaktowania operacje odzyskiwania pamięci.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|Tylko .NET Core 3,0 i nowsze wersje: podobne do [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), ale zawierają informacje dotyczące alokacji obiektów dla sterty dużych obiektów (LOH).|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Reprezentuje wszystkie flagi `COR_PRF_HIGH_MONITOR`, które wymagają obrazów z rozszerzonym profilem. Odnosi się do flagi `COR_PRF_REQUIRE_PROFILE_IMAGE` w wyliczeniu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Reprezentuje wszystkie flagi `COR_PRF_HIGH_MONITOR`, które można ustawić po dołączeniu profilera do uruchomionej aplikacji.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Reprezentuje wszystkie flagi `COR_PRF_HIGH_MONITOR`, które można ustawić tylko podczas inicjowania. Próba zmiany którejkolwiek z tych flag w innym miejscu powoduje, że wartość `HRESULT`, która wskazuje na błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Flagi `COR_PRF_HIGH_MONITOR` są używane z parametrem `pdwEventsHigh` metod [ICorProfilerInfo5:: GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) i [ICorProfilerInfo5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
Począwszy od .NET Framework 4.6.1 wartość `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` zmieniona z 0 na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). Począwszy od .NET Framework 4.7.2, jego wartość zmieniła się z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` ma być maską bitowej, która reprezentuje wszystkie flagi, które można ustawić tylko podczas inicjowania. Próba zmiany którejkolwiek z tych flag w innym miejscu powoduje niepowodzenie `HRESULT`.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [COR_PRF_MONITOR, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
