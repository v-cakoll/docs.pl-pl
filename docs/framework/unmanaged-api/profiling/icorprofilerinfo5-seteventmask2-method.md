---
title: Metoda ICorProfilerInfo5::SetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 266219894ffefa0d4066c6ca68c7cadf6265e098
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175815"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>Metoda ICorProfilerInfo5::SetEventMask2
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Ustawia wartość, która określa typy zdarzeń, dla których program profilujący chce otrzymywać powiadomienia o zdarzeniach środowisko uruchomieniowe języka wspólnego (CLR). Zapewnia więcej funkcji niż [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwEventsLow`  
 [in] Wartość 4-bajtowych, który określa kategorie zdarzeń. Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia. Bity są opisane w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.  
  
 `dwEventsHigh`  
 [in] Wartość 4-bajtowych, który określa kategorie zdarzeń.  Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia. Bity są opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 `SetEventMask2` Metoda jest używana do ustawiania wywołań zwrotnych, do których subskrybuje profilera. Zazwyczaj należy wywołać [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metodę pozwala ustalić, które bity są ustawione, wykonać logiczne OR z jego `pdwEventsLow` i `pdwEventsHigh` wartości i żadnych nowych elementów, które chcesz ustawić, a następnie wywołaj `SetEventMask2` metody.  
  
 Ta metoda jest zalecaną alternatywą [seteventmask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [GetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
