---
title: ICorProfilerInfo10, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175073"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10, interfejs

Podklasa [ICorProfilerInfo9,](icorprofilerinfo9-interface.md) która udostępnia metody modyfikowania funkcji IL, kwerendy informacji ze środowiska wykonawczego i zawiesić i wznowić środowisko uruchomieniowe.

## <a name="methods"></a>Metody  

| Metoda|Opis|  
| ------------|-----------------|  
|[EnumerateObjectReferences, metoda](icorprofilerinfo10-enumerateobjectreferences-method.md)|Biorąc pod uwagę ObjectID, wywołania zwrotnego i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje). |
|[IsFrozenObject, metoda](icorprofilerinfo10-isfrozenobject-method.md)|Biorąc pod uwagę ObjectID, określa, czy obiekt znajduje się w segmencie tylko do odczytu. |
|[GetLOHObjectSizeThreshold, metoda](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Pobiera wartość skonfigurowanego progu LOH. |
|[RequestReJITWithInliners, metoda](icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs metody wymagane, jak również wszelkie inlinera metod wymaganych metod.  |
|[SuspendRuntime, metoda](icorprofilerinfo10-suspendruntime-method.md)| Zawiesza środowisko wykonawcze bez wykonywania GC. |
|[ResumeRuntime, metoda](icorprofilerinfo10-resumeruntime-method.md)| Wznawia środowisko wykonawcze bez wykonywania GC. |

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [.NET Core obsługiwane systemy operacyjne](../../../core/install/dependencies.md?pivots=os-windows).  
**Nagłówek:** CorProf.idl, CorProf.h  
**Wersje .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Zobacz też

- [Interfejsy profilowania](profiling-interfaces.md)
