---
title: Metoda ICorProfilerInfo5::GetEventMask2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerInfo5.GetEventMask2
api_location: mscorwks.dll
api_type: COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72adbbdc3495f4171f555d119cb61d5dbc5ef0e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>Metoda ICorProfilerInfo5::GetEventMask2
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera bieżący kategorii zdarzeń, dla których chce otrzymywać powiadomień według środowisko uruchomieniowe języka wspólnego (CLR) profilera.  Zapewnia funkcje nie są udostępniane przez [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwEventsLow`  
 [out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń. Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia. Bity zostały opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.  
  
 `pdwEventsHigh`  
 [out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń.  Każdy bit określa różne możliwości, zachowanie lub typ zdarzenia. Bity zostały opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 `GetEventMask2` Metoda jest używana do określenia wywołania zwrotne, które subskrybuje profilera. Zwykle wykonać logicznych lub `pdwEventsLow` i `pdwEventsHigh` wartości i wszelkie nowe bity chcesz ustawić, a następnie wywołać [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.  
  
 Ta metoda jest zalecanym sposobem [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [SetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
