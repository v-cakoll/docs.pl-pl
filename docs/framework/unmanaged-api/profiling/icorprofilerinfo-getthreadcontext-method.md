---
title: ICorProfilerInfo::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b8afe10563d61e3ddab93e8d1b57eee4b6765c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766832"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a>ICorProfilerInfo::GetThreadContext — Metoda
Pobiera tożsamość kontekstu aktualnie skojarzone z określonego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadId`  
 [in] Identyfikator wątku.  
  
 `pContextId`  
 [out] Wskaźnik do identyfikator kontekstu, obecnie skojarzonego z określonego wątku. Jeśli wątek ma kontekst nie jest obecnie skojarzony z nim, ta funkcja zwróci CORPROF_E_DATAINCOMPLETE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
