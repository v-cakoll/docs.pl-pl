---
title: ICorProfilerInfo10, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 06cce79fbb2b2eb143e77e3c6fda194e47d4f4f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928802"
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
