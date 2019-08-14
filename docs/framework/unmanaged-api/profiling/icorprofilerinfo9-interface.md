---
title: ICorProfilerInfo9, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 0ba4f2b4a515143d50bc812f04ea75d821b69471
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973688"
---
# <a name="icorprofilerinfo9-interface"></a>ICorProfilerInfo9, interfejs

Podklasa elementu [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) , która dostarcza metody do wykonywania zapytań o informacje o funkcjach z wieloma natywnymi wersjami kodu.  

## <a name="methods"></a>Metody  

| Metoda|Opis|  
| ------------|-----------------|  
|[GetNativeCodeStartAddresses, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| Mając functionId i rejitId, wylicza natywny adres początkowy kodu dla wszystkich wersji trybie JIT tego kodu, który już istnieje. |
|[GetILToNativeMapping3, Metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| Przy podanym adresie początkowym kodu natywnego program zwraca informacje mapowania natywnego do IL dla tej trybie JIT wersji kodu. |
|[GetCodeInfo4, Metoda](icorprofilerinfo9-getcodeinfo4-method.md)| Przy podanym adresie początkowym kodu natywnego program zwraca bloki pamięci wirtualnej, która przechowuje ten kod. |

## <a name="requirements"></a>Wymagania  
**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
**Nagłówki** CorProf. idl, CorProf. h  
**Wersje .NET:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  
## <a name="see-also"></a>Zobacz także
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
