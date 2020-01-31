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
ms.openlocfilehash: e0ff90f99c1127b5a4626f47514ba7099b5d48af
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866601"
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

  \[in] wynik HRESULT wskazujący, czy klasa została pomyślnie załadowana.

## <a name="remarks"></a>Uwagi  
 Wartość `classId` nie jest prawidłowa dla żądania informacji, dopóki nie zostanie wywołana metoda `ClassLoadFinished`.  
  
 Niektóre części ładowania klasy mogą być kontynuowane po wywołaniu wywołania zwrotnego `ClassLoadFinished`. Błąd HRESULT w `hrStatus` wskazuje na błąd. Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część ładowania klasy zakończyła się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [ClassLoadStarted, metoda](icorprofilercallback-classloadstarted-method.md)
