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
ms.openlocfilehash: c6fdb7040620bb7a5b6aea6e0dc41e08d6f346d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210361"
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
 podczas Pojemność magazynu `map` macierzy. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 pcMap  
 określoną Liczba wartości COR_IL_MAP zapisywana w tablicy map.  
  
 map  
 określoną Tablica wartości COR_IL_MAP, które dostarczają informacji o mapowaniach z Instrumentacji Il do języka IL, w przypadku metody języka, która została oryginalną metodą.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli profiler ustawi mapowanie, wywołując metodę [ICorProfilerInfo:: SetILInstrumentedCodeMap —](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , debuger może wywołać tę metodę, aby pobrać mapowanie i używać mapowania wewnętrznie podczas obliczania przesunięć Il dla śladów stosu i zmiennych okresów istnienia.  
  
 Jeśli wartość `cMap` jest równa 0 i `pcMap` ma**wartość**różną od null, `pcMap` jest ustawiona na liczbę dostępnych wartości COR_IL_MAP. Jeśli `cMap` jest różna od zera, reprezentuje pojemność magazynu `map` tablicy. Gdy metoda zwraca, `map` zawiera maksimum `cMap` elementów i `pcMap` jest ustawiona na liczbę COR_IL_MAP wartości rzeczywiście zapisywana w `map` tablicy.  
  
 Jeśli obiekt IL nie został Instrumentacją lub mapowanie nie zostało dostarczone przez profiler, Metoda ta zwraca `S_OK` i ustawia `pcMap` wartość 0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorProfilerInfo:: SetILInstrumentedCodeMap —](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [Interfejs ICorDebugILCode2](icordebugilcode2-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
