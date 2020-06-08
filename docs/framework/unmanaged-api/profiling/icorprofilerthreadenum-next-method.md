---
title: ICorProfilerThreadEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
ms.openlocfilehash: 37d1acfa70a1a2b2c18fb34fb5d6024f3b61e2ab
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494348"
---
# <a name="icorprofilerthreadenumnext-method"></a>ICorProfilerThreadEnum::Next — Metoda
Pobiera określoną liczbę sąsiadujących wątków z kolejnej kolekcji wątków, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba wątków do pobrania.  
  
 `ids`  
 określoną Tablica `ThreadID` wartości, z których każdy reprezentuje pobrany wątek.  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby wątków faktycznie zwracanych w `ids` tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`celt`elementy zostały zwrócone.|  
|S_FALSE|`celt`Zwrócono mniej niż elementy, co oznacza, że Wyliczenie zostało zakończone.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerThreadEnum, interfejs](icorprofilerthreadenum-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
