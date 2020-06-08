---
title: ICorProfilerCallback::AssemblyLoadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500445"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>ICorProfilerCallback::AssemblyLoadFinished — Metoda
Powiadamia profiler o zakończeniu ładowania zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametry

- `assemblyId`

  \[w] identyfikuje zestaw, który został załadowany.

- `hrStatus`

  \[w] wynik HRESULT wskazujący, czy zestaw zakończył pomyślne ładowanie.

## <a name="remarks"></a>Uwagi  
 Wartość `assemblyId` nie jest prawidłowa dla żądania informacji, dopóki `AssemblyLoadFinished` Metoda nie zostanie wywołana.  
  
 Niektóre części ładowania zestawu mogą być kontynuowane po `AssemblyLoadFinished` wywołaniu wywołania zwrotnego. Błąd HRESULT w elemencie `hrStatus` wskazuje na błąd. Jednak powodzenie HRESULT w programie `hrStatus` wskazuje tylko, że pierwsza część ładowania zestawu zakończyła się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
