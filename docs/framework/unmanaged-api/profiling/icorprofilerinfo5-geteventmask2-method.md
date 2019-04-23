---
title: Metoda ICorProfilerInfo5::GetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8ebddf9a16b2eddbbc58342f68b517064e8d794
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214640"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>Metoda ICorProfilerInfo5::GetEventMask2
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera bieżący kategorie zdarzeń, dla których program profilujący chce otrzymywać powiadomienia z środowisko uruchomieniowe języka wspólnego (CLR).  Oferuje funkcje, które nie został dostarczony przez [icorprofilerinfo::geteventmask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwEventsLow`  
 [out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń. Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia. Bity są opisane w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.  
  
 `pdwEventsHigh`  
 [out] Wskaźnik do wartości 4-bajtowych, który określa kategorie zdarzeń.  Każdy bit kontroluje różne możliwości, działanie lub typ zdarzenia. Bity są opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 `GetEventMask2` Metoda jest używana do określenia wywołania zwrotne, które zostały zasubskrybowane przez profiler. Zwykle wykonać logiczne OR `pdwEventsLow` i `pdwEventsHigh` wartości i żadnych nowych elementów, które chcesz ustawić, a następnie wywołaj [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.  
  
 Ta metoda jest zalecaną alternatywą [geteventmask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [SetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
