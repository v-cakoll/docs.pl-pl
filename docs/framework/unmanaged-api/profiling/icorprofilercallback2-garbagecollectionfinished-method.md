---
title: ICorProfilerCallback2::GarbageCollectionFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21f7e9fa0e567063c49caa390ace09c43454b092
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451685"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a>ICorProfilerCallback2::GarbageCollectionFinished — Metoda
Powiadamia profilera, że ukończono wyrzucanie elementów bezużytecznych i wszystkie wywołania zwrotne kolekcji pamięci zostały wydane dla niego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a>Uwagi  
 Bezpiecznie dla profiler do zbadania obiektów w ich lokalizacji końcowej podczas `GarbageCollectionFinished` metoda jest wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
