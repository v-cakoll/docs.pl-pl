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
ms.openlocfilehash: 2e814eaba04fd6781d10bbcb67ade9acdefa161d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114746"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>Metoda ICorProfilerInfo5::GetEventMask2
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia z aparatu plików wykonywalnych języka wspólnego (CLR).  Zapewnia funkcje niedostarczone przez metodę [ICorProfilerInfo:: GetEventMask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwEventsLow`  
 określoną Wskaźnik do 4-bajtowej wartości, która określa kategorie zdarzeń. Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia. Bity są opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Wyliczenie.  
  
 `pdwEventsHigh`  
 określoną Wskaźnik do 4-bajtowej wartości, która określa kategorie zdarzeń.  Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia. Bity są opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) Wyliczenie.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetEventMask2` służy do określania, które wywołania zwrotne zasubskrybował Profiler. Zazwyczaj należy wykonać wartość logiczną lub `pdwEventsLow` i `pdwEventsHigh`, a także wszystkie nowe bity, które mają zostać ustawione, a następnie wywołać metodę [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
 Ta metoda jest zalecaną alternatywą dla metody [GetEventMask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo5, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [SetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
