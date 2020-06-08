---
title: ICorProfilerCallback::ClassLoadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 4be2a50664b001e865b5ecdd9aabe8ba727b8c26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500393"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a>ICorProfilerCallback::ClassLoadFinished — Metoda
Powiadamia profiler o zakończeniu ładowania klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Parametry

- `classId`

  \[w] identyfikuje klasę, która została załadowana.

- `hrStatus`

  \[w] wynik HRESULT wskazujący, czy klasa została pomyślnie załadowana.

## <a name="remarks"></a>Uwagi  
 Wartość `classId` nie jest prawidłowa dla żądania informacji, dopóki `ClassLoadFinished` Metoda nie zostanie wywołana.  
  
 Niektóre części ładowania klasy mogą być kontynuowane po `ClassLoadFinished` wywołaniu wywołania zwrotnego. Błąd HRESULT w elemencie `hrStatus` wskazuje na błąd. Jednak powodzenie HRESULT w programie `hrStatus` wskazuje tylko, że pierwsza część ładowania klasy zakończyła się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ClassLoadStarted, metoda](icorprofilercallback-classloadstarted-method.md)
