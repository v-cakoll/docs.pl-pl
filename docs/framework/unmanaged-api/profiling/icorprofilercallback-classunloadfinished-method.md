---
title: ICorProfilerCallback::ClassUnloadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 14eb90c707618796d6d62ed2ec5710ceba31ba6c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500380"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a>ICorProfilerCallback::ClassUnloadFinished — Metoda
Powiadamia profiler o zakończeniu zwalniania klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Parametry

- `classId`

  \[w] identyfikuje klasę, która została zwolniona.

- `hrStatus`

  \[w] wynik HRESULT wskazujący, czy klasa została zwolniona pomyślnie.
  
## <a name="remarks"></a>Uwagi  
 Niektóre części zwalniania klasy mogą być kontynuowane po `ClassUnloadFinished` wywołaniu wywołania zwrotnego. Błąd HRESULT w elemencie `hrStatus` wskazuje na błąd. Jednak wynik HRESULT w programie `hrStatus` wskazuje tylko, że pierwsza część zwalniania klasy zakończyła się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ClassUnloadStarted, metoda](icorprofilercallback-classunloadstarted-method.md)
