---
title: ICorProfilerInfo10, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 496959ecac5b16f1faa138aec90c5194d15cb105
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973751"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10, interfejs

Podklasa elementu [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) , która udostępnia metody modyfikowania funkcji IL, zapytania o informacje z środowiska uruchomieniowego oraz wstrzymywanie i wznawianie środowiska uruchomieniowego.

## <a name="methods"></a>Metody  

| Metoda|Opis|  
| ------------|-----------------|  
|[EnumerateObjectReferences, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|Podanym identyfikatorem ObjectID, wywołaniem zwrotnym i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje). |
|[Zamrożonobject, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|Przy użyciu identyfikatora ObjectID określa, czy obiekt znajduje się w segmencie tylko do odczytu. |
|[GetLOHObjectSizeThreshold, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Pobiera wartość skonfigurowanego progu LOH. |
|[RequestReJITWithInliners, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs wymagane metody, a także wszystkie wbudowane metody.  |
|[SuspendRuntime, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| Wstrzymuje środowisko uruchomieniowe bez wykonywania operacji GC. |
|[ResumeRuntime, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| Wznawia środowisko uruchomieniowe bez wykonywania operacji GC. |

## <a name="requirements"></a>Wymagania  
**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
**Nagłówki** CorProf. idl, CorProf. h  
**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 
## <a name="see-also"></a>Zobacz także
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
