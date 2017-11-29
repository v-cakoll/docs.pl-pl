---
title: Metoda ICorProfilerInfo5::SetEventMask2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: IcorProfilerInfo5.SetEventMask2
api_location: mscorwks.dll
api_type: COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2cf383ef8100e096b8373b59231d4aef12725c3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>Metoda ICorProfilerInfo5::SetEventMask2
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Ustawia wartość, która określa typy zdarzeń, dla których chce otrzymywać powiadomienia o zdarzeniach środowisko uruchomieniowe języka wspólnego (CLR) profilera. Zapewnia więcej funkcji niż [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwEventsLow`  
 [in] Wartość 4-bajtowych, która określa kategorie zdarzeń. Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia. Bity zostały opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.  
  
 `dwEventsHigh`  
 [in] Wartość 4-bajtowych, która określa kategorie zdarzeń.  Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia. Bity zostały opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 `SetEventMask2` Metoda jest używana do ustawiania wywołań zwrotnych, do których subskrybuje profilera. Zazwyczaj wywołanie [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metodę, aby określić, które są skonfigurowane, wykonaj logicznych lub jego `pdwEventsLow` i `pdwEventsHigh` wartości i wszelkie nowe bity chcesz ustawić, a następnie wywołać `SetEventMask2` — metoda.  
  
 Ta metoda jest zalecanym sposobem [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [Metoda GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
