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
ms.openlocfilehash: 7dede4e5af702f1b86b430450db4a669c326c062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131064"
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
 określoną Tablica wartości COR_IL_MAP, które dostarczają informacji o mapowaniach z Instrumentacji IL do języka IL, do metodyki, którą można wykonać przy użyciu narzędzia.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli profiler ustawi mapowanie przez wywołanie metody [ICorProfilerInfo:: SetILInstrumentedCodeMap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , debuger może wywołać tę metodę, aby pobrać mapowanie i używać mapowania wewnętrznie podczas obliczania przesunięć Il dla śladów stosu i zmiennej okresy istnienia.  
  
 Jeśli `cMap` ma wartość 0, a `pcMap` ma**wartość**różną od null, `pcMap` jest ustawiona na liczbę dostępnych wartości COR_IL_MAP. Jeśli `cMap` jest różna od zera, reprezentuje pojemność magazynu `map` tablicy. Gdy metoda zwraca, `map` zawiera maksymalnie `cMap` elementów, a `pcMap` jest ustawiona na liczbę COR_IL_MAP wartości rzeczywiście zapisywana w tablicy `map`.  
  
 Jeśli obiekt IL nie został Instrumentacją lub mapowanie nie zostało dostarczone przez profiler, Metoda ta zwraca `S_OK` i ustawia `pcMap` na 0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo:: SetILInstrumentedCodeMap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
