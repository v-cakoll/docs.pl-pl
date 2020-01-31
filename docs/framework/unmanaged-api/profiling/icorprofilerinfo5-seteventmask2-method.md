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
ms.openlocfilehash: 10e84b729c8af607165009a8591a69dbc1afcb1e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868385"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>Metoda ICorProfilerInfo5::SetEventMask2
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Ustawia wartość określającą typy zdarzeń, dla których profiler chce otrzymywać powiadomienia o zdarzeniach z aparatu plików wykonywalnych języka wspólnego (CLR). Zapewnia większą funkcjonalność niż Metoda [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwEventsLow`  
 podczas Wartość 4-bajtowa, która określa kategorie zdarzeń. Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia. Bity są opisane w [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) Wyliczenie.  
  
 `dwEventsHigh`  
 podczas Wartość 4-bajtowa, która określa kategorie zdarzeń.  Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia. Bity są opisane w [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) Wyliczenie.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `SetEventMask2` służy do ustawiania wywołań zwrotnych, do których jest subskrybowany Profiler. Zazwyczaj należy wywołać metodę [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) , aby określić, które bity są ustawione, wykonywać wartości logiczne lub `pdwEventsLow` i `pdwEventsHigh`, a także wszelkie nowe bity, które chcesz ustawić, a następnie wywołać metodę `SetEventMask2`.  
  
 Ta metoda jest zalecaną alternatywą dla metody [SetEventMask](icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo5, interfejs](icorprofilerinfo5-interface.md)
- [GetEventMask2, metoda](icorprofilerinfo5-geteventmask2-method.md)
