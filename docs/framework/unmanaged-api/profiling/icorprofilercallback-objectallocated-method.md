---
title: ICorProfilerCallback::ObjectAllocated — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c07b37e58141f7aff747bd3772be265ae0da42ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222019"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated — Metoda
Powiadamia program profilujący, która została przydzielona pamięci w stercie dla obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 [in] Identyfikator obiektu, dla którego pamięć została alokowana.  
  
 `classId`  
 [in] Identyfikator klasy, którego wystąpienie jest obiekt.  
  
## <a name="remarks"></a>Uwagi  
 `ObjectedAllocated` Metoda nie jest wywoływana dla alokacji stosu lub niezarządzanej pamięci. `classId` Parametru może odwoływać się do klasy w kodzie zarządzanym, który nie został jeszcze załadowany. Program profilujący otrzyma wywołanie zwrotne obciążenia klasy dla klasy natychmiast po `ObjectAllocated` wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassLoadStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
