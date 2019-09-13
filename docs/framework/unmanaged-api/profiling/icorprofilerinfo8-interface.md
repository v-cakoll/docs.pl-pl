---
title: ICorProfilerInfo8, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2baa33a7a3527392d8095b5d0ec7ad6af8a71a8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928936"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8, interfejs

Podklasa elementu [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) , która dostarcza metody do badania informacji o metodach dynamicznych.

## <a name="methods"></a>Metody  

| Metoda|Opis|  
| ------------|-----------------|  
|[IsFunctionDynamic, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| Określa, czy funkcja nie ma skojarzonych metadanych.|
|[GetFunctionFromIP3, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| Mapuje wskaźnik zarządzanej instrukcji kodu na FunctionID. Ta metoda działa w przypadku metod dynamicznych i niedynamicznych. |
|[GetDynamicFunctionInfo, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Pobiera informacje o metodach dynamicznych. |

## <a name="requirements"></a>Wymagania  
**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówki** CorProf. idl, CorProf. h  
**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
