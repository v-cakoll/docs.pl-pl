---
title: ICorProfilerCallback::AssemblyUnloadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 734ae1d14d02d47c7d3126f1b4cf55dcb4ad151b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866627"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>ICorProfilerCallback::AssemblyUnloadFinished — Metoda
Powiadamia program profilujący, że zestaw został zwolniony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametry

- `assemblyId`

  \[in] określa zestaw, który jest zwalniany.

- `hrStatus`

  \[in] wynik HRESULT wskazujący, czy zestaw został zwolniony pomyślnie.

## <a name="remarks"></a>Uwagi  
 Wartość `assemblyId` nie jest prawidłowa dla żądania informacji po powrocie metody [ICorProfilerCallback:: AssemblyUnloadStarted —](icorprofilercallback-assemblyunloadstarted-method.md) .  
  
 Niektóre części zwalniania zestawu mogą być kontynuowane po wywołaniu wywołania zwrotnego `AssemblyUnloadFinished`. Błąd HRESULT w `hrStatus` wskazuje na błąd. Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część zwalniania zestawu zakończyła się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
