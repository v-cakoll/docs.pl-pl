---
title: ICorProfilerInfo2::GetObjectGeneration — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c259bc167d2d4fbadf0d4721e3329975cb0f0caf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454369"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a>ICorProfilerInfo2::GetObjectGeneration — Metoda
Pobiera segment stosu, który zawiera określony obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a>Parametry  
 `objectId`  
 [in] Identyfikator obiektu.  
  
 `range`  
 [out] Wskaźnik do [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury, która opisuje zakresu (Blokuj) pamięci w ramach wybranej generacji jest poddawana wyrzucanie elementów bezużytecznych. Ten zakres zawiera określony obiekt.  
  
## <a name="remarks"></a>Uwagi  
 `GetObjectGeneration` Zwrotne profilera, może zostać wywołana metoda pod warunkiem, że pamięci nie jest w toku. Oznacza to, może być wywoływana z dowolnego wywołania zwrotnego z wyjątkiem tych, które mają miejsce między [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) i [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
