---
title: Metoda ICorDebugILCode2::GetInstrumentedILMap
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode2.GetInstrumentedILMap
api_location: mscordbi.dll
api_type: COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0499813bc2192d419dc21d9dbb84aff17894544f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>Metoda ICorDebugILCode2::GetInstrumentedILMap
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zwraca mapę z Instrumentacji profilera języku pośrednim (IL) przesunięcia do oryginalnego przesunięcia metody IL dla tego wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 cMap  
 [in] Pojemność `map` tablicy. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 pcMap  
 [out] Liczba wartości COR_IL_MAP zapisywane do tablicy mapy.  
  
 map  
 [out] Tablica wartości COR_IL_MAP, które udostępniają informacje dotyczące mapowania z Instrumentacji profilera IL do IL oryginalnej metody.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli profilera ustawia mapowanie przez wywołanie metody [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody debuger tę metodę można wywołać można pobrać mapowania i mapowanie wewnętrznie do obliczania IL przesunięciami stosu Śledzenie i okresy zmiennej.  
  
 Jeśli `cMap` 0 i `pcMap` ma wartość inną niż**null**, `pcMap` wynosi liczba dostępnych wartości COR_IL_MAP. Jeśli `cMap` jest różna od zera, reprezentuje pojemność `map` tablicy. Gdy metoda zwróci wartość, `map` może zawierać maksymalnie `cMap` elementów, i `pcMap` jest równa wartości COR_IL_MAP faktycznie zapisane `map` tablicy.  
  
 Jeśli nie zostały zinstrumentowane IL lub mapowanie nie zostało dostarczone przez profiler, ta metoda zwraca `S_OK` i ustawia `pcMap` na 0.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)  
 [ICorDebugILCode2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
