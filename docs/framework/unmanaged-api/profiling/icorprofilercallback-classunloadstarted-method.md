---
title: ICorProfilerCallback::ClassUnloadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 3b729d3be84571a48cc9a770d7f06b99723c0d1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445067"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a>ICorProfilerCallback::ClassUnloadStarted — Metoda
Powiadamia profiler o tym, że Klasa jest zwalniana.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 podczas Identyfikuje klasę, która jest zwalniana.  
  
## <a name="remarks"></a>Uwagi  
 Wartość `classId` nie jest prawidłowa dla żądania informacji po powrocie metody `ClassUnloadStarted` — jest to Ostatnia szansa dla profilera do uzyskania informacji o tej klasie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassUnloadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
