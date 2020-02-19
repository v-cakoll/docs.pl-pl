---
title: ICorProfilerInfo9, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 431a546fb4a3b92b379e273553f0caf540ba1473
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449740"
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
**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?pivots=os-windows).  
**Nagłówek:** CorProf. idl, CorProf. h  
**Wersje .NET:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Zobacz też

- [Interfejsy profilowania](profiling-interfaces.md)
