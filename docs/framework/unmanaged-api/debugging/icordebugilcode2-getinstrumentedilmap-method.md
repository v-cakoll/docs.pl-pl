---
title: Metoda ICorDebugILCode2::GetInstrumentedILMap
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: 728a6c83dc321fa28dc4ff84c4e874d886524b36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788569"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>Metoda ICorDebugILCode2::GetInstrumentedILMap
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zwraca mapę z przesunięcia języka pośredniego (IL) instrumentacji do metody oryginalnej dla tego wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 cMap  
 podczas Pojemność magazynu tablicy `map`. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 pcMap  
 określoną Liczba wartości COR_IL_MAP zapisywana w tablicy map.  
  
 map  
 określoną Tablica wartości COR_IL_MAP, które dostarczają informacji o mapowaniach z Instrumentacji Il do języka IL, w przypadku metody języka, która została oryginalną metodą.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli profiler ustawi mapowanie, wywołując metodę [ICorProfilerInfo:: SetILInstrumentedCodeMap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , debuger może wywołać tę metodę, aby pobrać mapowanie i używać mapowania wewnętrznie podczas obliczania przesunięć Il dla śladów stosu i zmiennych okresów istnienia.  
  
 Jeśli `cMap` ma wartość 0, a `pcMap` ma**wartość**różną od null, `pcMap` jest ustawiona na liczbę dostępnych wartości COR_IL_MAP. Jeśli `cMap` jest różna od zera, reprezentuje pojemność magazynu `map` tablicy. Gdy metoda zwraca, `map` zawiera maksymalnie `cMap` elementów, a `pcMap` jest ustawiona na liczbę wartości COR_IL_MAP rzeczywiście zapisywana w tablicy `map`.  
  
 Jeśli obiekt IL nie został Instrumentacją lub mapowanie nie zostało dostarczone przez profiler, Metoda ta zwraca `S_OK` i ustawia `pcMap` na 0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2, interfejs](icordebugilcode2-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
