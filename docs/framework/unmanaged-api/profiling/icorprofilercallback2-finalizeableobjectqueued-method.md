---
title: ICorProfilerCallback2::FinalizeableObjectQueued — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
ms.openlocfilehash: e2e01c396a67614464e3d4ca50de992388961463
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499829"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a>ICorProfilerCallback2::FinalizeableObjectQueued — Metoda
Powiadamia profiler kodu o tym, że obiekt z finalizatorem został umieszczony w kolejce finalizatora w celu wykonania jego `Finalize` metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a>Parametry  
 `finalizerFlags`  
 podczas Wartość wyliczenia [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) opisująca aspekty finalizatora.  
  
 `objectID`  
 podczas Identyfikator obiektu, który został umieszczony w kolejce.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 — Interfejs](icorprofilercallback2-interface.md)
