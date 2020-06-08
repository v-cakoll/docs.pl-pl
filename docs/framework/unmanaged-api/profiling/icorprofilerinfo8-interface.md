---
title: ICorProfilerInfo8, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2cca915eda44d73aea7469e5f752c57309c2300d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495167"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8, interfejs

Podklasa elementu [ICorProfilerInfo7](icorprofilerinfo7-interface.md) , która dostarcza metody do badania informacji o metodach dynamicznych.

## <a name="methods"></a>Metody  

| Metoda|Opis|  
| ------------|-----------------|  
|[IsFunctionDynamic, metoda](icorprofilerinfo8-isfunctiondynamic-method.md)| Określa, czy funkcja nie ma skojarzonych metadanych.|
|[GetFunctionFromIP3, metoda](icorprofilerinfo8-getfunctionfromip3-method.md)| Mapuje wskaźnik zarządzanej instrukcji kodu na FunctionID. Ta metoda działa w przypadku metod dynamicznych i niedynamicznych. |
|[GetDynamicFunctionInfo, metoda](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Pobiera informacje o metodach dynamicznych. |

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** CorProf. idl, CorProf. h  
**.NET Framework wersje:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
