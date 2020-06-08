---
title: ICorProfilerCallback::ModuleLoadStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
ms.openlocfilehash: a04f72fff9a88c8689821131b08b35500c23b3d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503357"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a>ICorProfilerCallback::ModuleLoadStarted — Metoda
Powiadamia program profilujący, że moduł jest ładowany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 podczas Identyfikator modułu, który jest ładowany.  
  
## <a name="remarks"></a>Uwagi  
 Wartość `moduleId` nie jest prawidłowa dla żądania informacji, dopóki nie zostanie wywołana metoda [ICorProfilerCallback:: ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
