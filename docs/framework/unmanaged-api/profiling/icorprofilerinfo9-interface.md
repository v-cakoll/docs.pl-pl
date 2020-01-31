---
title: ICorProfilerInfo9, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 371e85ce8f5d7b420a30ac842ec658949e47d30e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861648"
---
# <a name="icorprofilerinfo9-interface"></a>ICorProfilerInfo9, interfejs

Podklasa elementu [ICorProfilerInfo8](icorprofilerinfo8-interface.md) , która dostarcza metody do wykonywania zapytań o informacje o funkcjach z wieloma natywnymi wersjami kodu.  

## <a name="methods"></a>Metody  

| Metoda|Opis|  
| ------------|-----------------|  
|[GetNativeCodeStartAddresses, Metoda](icorprofilerinfo9-getnativecodestartaddresses-method.md)| Mając functionId i rejitId, wylicza natywny adres początkowy kodu dla wszystkich wersji trybie JIT tego kodu, który już istnieje. |
|[GetILToNativeMapping3, Metoda](icorprofilerinfo9-getiltonativemapping3-method.md)| Przy podanym adresie początkowym kodu natywnego program zwraca informacje mapowania natywnego do IL dla tej trybie JIT wersji kodu. |
|[GetCodeInfo4, Metoda](icorprofilerinfo9-getcodeinfo4-method.md)| Przy podanym adresie początkowym kodu natywnego program zwraca bloki pamięci wirtualnej, która przechowuje ten kod. |

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**Nagłówek:** CorProf. idl, CorProf. h  
**Wersje .NET:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
