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
ms.openlocfilehash: 90071121411b706052e1cbb4cb647536dae2835a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864872"
---
# <a name="icorprofilercallback6-interface"></a>Interfejs ICorProfilerCallback6
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Podklasa elementu [ICorProfilerCallback5](icorprofilercallback5-interface.md) , która zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o ładowaniu zestawu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAssemblyReferences, metoda](icorprofilercallback6-getassemblyreferences-method.md)|Powiadamia program profilujący, że zestaw jest w bardzo wczesnym etapie ładowania, gdy środowisko uruchomieniowe języka wspólnego wykonuje przegląd zamknięcia odwołania do zestawu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
