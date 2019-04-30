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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4197b018ea85402762a8591b40f3503c02af3974
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673140"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>Metoda ICorDebugILCode2::GetInstrumentedILMap
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zwraca mapę z Instrumentacji profilera języka pośredniego (IL) przesunięcia do oryginalnego przesunięcia IL metody dla tego wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 CMap  
 [in] Pojemność magazynu `map` tablicy. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 pcMap  
 [out] Liczba wartości cor_il_map — zapisywane do tablicy mapy.  
  
 map  
 [out] Tablica wartości cor_il_map —, które zawierają informacje dotyczące mapowania z Instrumentacji profilera IL do IL oryginalną metodę.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli profiler ustawia mapowanie przez wywołanie metody [icorprofilerinfo::setilinstrumentedcodemap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody, debuger tę metodę można wywołać można pobrać mapowania i mapowanie wewnętrznie do obliczania IL rekompensaty w przypadku stosu ślady i okresy istnienia zmiennych.  
  
 Jeśli `cMap` wynosi 0 i `pcMap` ma wartość inną niż**null**, `pcMap` wynosi liczba dostępnych wartości cor_il_map —. Jeśli `cMap` jest różna od zera, reprezentuje pojemność magazynu `map` tablicy. Po powrocie z metody `map` może zawierać maksymalnie `cMap` elementów, a `pcMap` jest równa wartości cor_il_map — rzeczywiście zapisanych na `map` tablicy.  
  
 Jeśli nie zostały zinstrumentowane IL lub mapowanie nie podano przez program profilujący, Metoda ta zwraca `S_OK` i ustawia `pcMap` na 0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
