---
title: Wyliczenie COR_PRF_HIGH_MONITOR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df931796b32b6bea49e8b69da02d39e6a4803e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corprfhighmonitor-enumeration"></a>Wyliczenie COR_PRF_HIGH_MONITOR
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Udostępnia flagi oprócz występujące w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia, które można określić profilera [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody podczas jego ładowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES     = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED     = 0x00000002,     
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE       = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH      = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE           = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Ustawiono żadnych flag.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Formanty [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego do dodawania odwołania do zestawów podczas przeszukiwania zamknięcia odwołanie do zestawu CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Formanty [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) wywołania zwrotnego aktualizacji w strumieniu symbol skojarzone z modułu w pamięci.|  
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Reprezentuje wszystkie `COR_PRF_HIGH_MONITOR` flagi, które wymagają rozszerzone profilu obrazów. Odpowiadający mu `COR_PRF_REQUIRE_PROFILE_IMAGE` oflagowane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Reprezentuje wszystkie `COR_PRF_HIGH_MONITOR` flagi, które można ustawić po profiler jest dołączony do uruchomionej aplikacji.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Reprezentuje wszystkie `COR_PRF_HIGH_MONITOR` flagi, które można ustawić tylko podczas inicjowania. Aby zmienić dowolne z tych flag, gdzie indziej powoduje w trakcie `HRESULT` wartość, która wskazuje błąd.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_PRF_HIGH_MONITOR` Flagi są używane z `pdwEventsHigh` parametr [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) i [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.  
  
 Począwszy od [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], wartość `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` zmienione od 0 do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [COR_PRF_MONITOR — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [Interfejs ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
