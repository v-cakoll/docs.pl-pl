---
title: ICorProfilerCallback7 Interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81477010b22edee71098edfc1b8557db08b6038f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178636"
---
# <a name="icorprofilercallback7-interface"></a>ICorProfilerCallback7 Interface
[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]  
  
 Podklasa klasy [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) który zapewnia metodę wywołania zwrotnego, która środowiska uruchomieniowego języka wspólnego używa powiadomić profiler, że strumień symbol skojarzone z modułem w pamięci jest aktualizowana.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ModuleInMemorySymbolsUpdated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|Powiadamia program profilujący, że strumień symbol skojarzone z modułem w pamięci jest aktualizowana.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
