---
title: ICorProfilerCallback::ModuleLoadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9eb5b4ec4b3bb99de4755a5b64398e989df379b7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478833"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>ICorProfilerCallback::ModuleLoadFinished — Metoda
Powiadamia program profilujący, że moduł zakończeniu ładowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, który zakończy ładowanie.  
  
 `hrStatus`  
 [in] Wartość HRESULT, która wskazuje, czy moduł został załadowany pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Wartość `moduleId` jest nieprawidłowa dla żądania informacje do momentu `ModuleLoadFinished` metoda jest wywoływana.  
  
 Niektóre części podczas ładowania modułu może nadal po `ModuleLoadFinished` wywołania zwrotnego. Błąd HRESULT w `hrStatus` wskazuje błąd. Jednak sukcesów wartość HRESULT w `hrStatus` wskazuje tylko, powiodło się w pierwszej części podczas ładowania modułu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ModuleLoadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
