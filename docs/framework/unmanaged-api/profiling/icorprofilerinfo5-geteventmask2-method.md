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
ms.openlocfilehash: 758e5b71443b127c80c820eb8531056530e81b13
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495700"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>Metoda ICorProfilerInfo5::GetEventMask2
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia z aparatu plików wykonywalnych języka wspólnego (CLR).  Zapewnia funkcje niedostarczone przez metodę [ICorProfilerInfo:: GetEventMask —](icorprofilerinfo-geteventmask-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwEventsLow`  
 określoną Wskaźnik do 4-bajtowej wartości, która określa kategorie zdarzeń. Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia. Bity są opisane w [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) Wyliczenie.  
  
 `pdwEventsHigh`  
 określoną Wskaźnik do 4-bajtowej wartości, która określa kategorie zdarzeń.  Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia. Bity są opisane w [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) Wyliczenie.  
  
## <a name="remarks"></a>Uwagi  
 `GetEventMask2`Metoda jest używana do określenia, które wywołania zwrotne zasubskrybował Profiler. Zazwyczaj należy wykonać wartości logiczne lub `pdwEventsLow` i i `pdwEventsHigh` wszystkie nowe bity, które mają zostać ustawione, a następnie wywołać metodę [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .  
  
 Ta metoda jest zalecaną alternatywą dla metody [GetEventMask —](icorprofilerinfo-geteventmask-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo5, interfejs](icorprofilerinfo5-interface.md)
- [SetEventMask2, metoda](icorprofilerinfo5-seteventmask2-method.md)
