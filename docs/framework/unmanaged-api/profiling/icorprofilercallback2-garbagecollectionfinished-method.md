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
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="6d88b-102">ICorProfilerCallback2::GarbageCollectionFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d88b-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="6d88b-103">Powiadamia profilera, że ukończono wyrzucanie elementów bezużytecznych i wszystkie wywołania zwrotne kolekcji pamięci zostały wydane dla niego.</span><span class="sxs-lookup"><span data-stu-id="6d88b-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d88b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d88b-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6d88b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d88b-105">Remarks</span></span>  
 <span data-ttu-id="6d88b-106">Bezpiecznie dla profiler do zbadania obiektów w ich lokalizacji końcowej podczas `GarbageCollectionFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="6d88b-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d88b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d88b-107">Requirements</span></span>  
 <span data-ttu-id="6d88b-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d88b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d88b-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d88b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d88b-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d88b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d88b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d88b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d88b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d88b-112">See Also</span></span>  
 [<span data-ttu-id="6d88b-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d88b-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6d88b-114">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d88b-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
