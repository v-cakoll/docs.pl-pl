---
title: Wyliczenie COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 5c6e34746368a7658c43fe0e2472000c29292569
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175216"
---
# <a name="cor_prf_high_monitor-enumeration"></a>Wyliczenie COR_PRF_HIGH_MONITOR

[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
Zawiera flagi oprócz tych znalezionych w [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) wyliczenie, które profiler można określić do [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metody podczas ładowania.  
  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Nie ustawiono żadnych flag.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Steruje [wywołaniami zwrotnymi ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) do dodawania odwołań do zestawu podczas przejścia zamknięcia odwołania do odwołania clr.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Steruje [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback dla aktualizacji strumienia symbolu skojarzonego z modułem w pamięci.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Steruje [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) wywołania zwrotnego do wskazania, gdy metoda dynamiczna została pobrana i zwolniona. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET Core 3.0 i nowsze wersje tylko: Wyłącza [kompilacji warstwowej](../../../core/whats-new/dotnet-core-3-0.md) dla profilerów.|
|`COR_PRF_HIGH_BASIC_GC`|.NET Core 3.0 i nowsze wersje tylko: Zapewnia [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)lekką opcję profilowania GC w porównaniu do . Steruje tylko [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)i [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) wywołania zwrotne. W `COR_PRF_MONITOR_GC` przeciwieństwie `COR_PRF_HIGH_BASIC_GC` do flagi, nie wyłącza równoczesnych wyrzucania elementów bezużytecznych.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET Core 3.0 i nowsze wersje tylko: Włącza [MovedReferences](icorprofilercallback-movedreferences-method.md) i [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) wywołania zwrotne tylko do kompaktowania kontrolerów GC.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET Core 3.0 i nowsze wersje tylko: Podobne do [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), ale zawiera informacje na temat alokacji obiektów dla sterty dużych obiektów (LOH) tylko.|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Reprezentuje `COR_PRF_HIGH_MONITOR` wszystkie flagi, które wymagają obrazów o rozszerzonej profili. Odpowiada `COR_PRF_REQUIRE_PROFILE_IMAGE` flagi w wyliczeniu [COR_PRF_MONITOR.](cor-prf-monitor-enumeration.md)|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Reprezentuje `COR_PRF_HIGH_MONITOR` wszystkie flagi, które można ustawić po profiler jest dołączony do uruchomionej aplikacji.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Reprezentuje `COR_PRF_HIGH_MONITOR` wszystkie flagi, które można ustawić tylko podczas inicjowania. Próba zmiany dowolnej z tych flag `HRESULT` w innym miejscu powoduje wartość, która wskazuje na niepowodzenie.|  
  
## <a name="remarks"></a>Uwagi

Flagi `COR_PRF_HIGH_MONITOR` są używane `pdwEventsHigh` z [parametrem ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) i [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metody.  
  
Począwszy od .NET Framework 4.6.1, `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` wartość zmieniona `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` z 0 na (0x00000002). Począwszy od programu .NET Framework 4.7.2, jego wartość zmieniła się z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` na `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.

`COR_PRF_HIGH_MONITOR_IMMUTABLE`ma być maską bitową, która reprezentuje wszystkie flagi, które można ustawić tylko podczas inicjowania. Próba zmiany któregokolwiek z tych flag `HRESULT`w innym miejscu powoduje niepowodzenie .

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
**Nagłówek:** CorProf.idl, CorProf.h  
  
**Biblioteka:** CorGuids.lib  
  
**Wersje programu .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Profilowanie — wyliczenia](profiling-enumerations.md)
- [COR_PRF_MONITOR, wyliczenie](cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5, interfejs](icorprofilerinfo5-interface.md)
