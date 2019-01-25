---
title: Interfejs ICorProfilerCallback6
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5025f4bb6433d193ecf7dec1d8375104147e9e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562573"
---
# <a name="icorprofilercallback6-interface"></a>Interfejs ICorProfilerCallback6
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Podklasa klasy [icorprofilercallback5 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) który zapewnia metodę wywołania zwrotnego, który środowiska uruchomieniowego języka wspólnego używa powiadomić profiler, który jest ładowany zestaw.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAssemblyReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|Powiadamia program profilujący, że zestaw w bardzo wczesnym ładowania etapie, gdy środowisko uruchomieniowe języka wspólnego wykonuje przeszukiwania zamknięcia odwołanie do zestawu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
