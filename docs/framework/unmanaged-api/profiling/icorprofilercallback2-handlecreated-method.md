---
title: ICorProfilerCallback2::HandleCreated — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47654d7ad1803e57f5db846ea0370d1f736deaa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452276"
---
# <a name="icorprofilercallback2handlecreated-method"></a>ICorProfilerCallback2::HandleCreated — Metoda
Powiadamia profilera kodu utworzono uchwyt kolekcji pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `handleId`  
 [in] Identyfikator obsługę wyrzucanie elementów bezużytecznych.  
  
 `initialObjectId`  
 [in] Identyfikator obiektu, dla którego utworzono uchwyt kolekcji pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
