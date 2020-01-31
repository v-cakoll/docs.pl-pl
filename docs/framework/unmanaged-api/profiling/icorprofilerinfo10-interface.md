---
title: ICorProfilerInfo10, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: e90a1ffbc037636e4296bbd4f4c3c5082885e9f3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863247"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10, interfejs

Podklasa elementu [ICorProfilerInfo9](icorprofilerinfo9-interface.md) , która udostępnia metody modyfikowania funkcji IL, zapytania o informacje z środowiska uruchomieniowego oraz wstrzymywanie i wznawianie środowiska uruchomieniowego.

## <a name="methods"></a>Metody  

| Metoda|Opis|  
| ------------|-----------------|  
|[EnumerateObjectReferences, Metoda](icorprofilerinfo10-enumerateobjectreferences-method.md)|Podanym identyfikatorem ObjectID, wywołaniem zwrotnym i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje). |
|[Zamrożonobject, Metoda](icorprofilerinfo10-isfrozenobject-method.md)|Przy użyciu identyfikatora ObjectID określa, czy obiekt znajduje się w segmencie tylko do odczytu. |
|[GetLOHObjectSizeThreshold, Metoda](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Pobiera wartość skonfigurowanego progu LOH. |
|[RequestReJITWithInliners, Metoda](icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs wymagane metody, a także wszystkie wbudowane metody.  |
|[SuspendRuntime, Metoda](icorprofilerinfo10-suspendruntime-method.md)| Wstrzymuje środowisko uruchomieniowe bez wykonywania operacji GC. |
|[ResumeRuntime, Metoda](icorprofilerinfo10-resumeruntime-method.md)| Wznawia środowisko uruchomieniowe bez wykonywania operacji GC. |

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**Nagłówek:** CorProf. idl, CorProf. h  
**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
