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
ms.openlocfilehash: f613842c12b50b8a58aac1b71bf2f3c53aaf961f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231100"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="94dad-102">ICorProfilerCallback2::GarbageCollectionFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="94dad-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="94dad-103">Powiadamia program profilujący, że wyrzucanie elementów bezużytecznych zostało ukończone, a wszystkie wywołania wyrzucania elementów bezużytecznych zostały wydane dla niego.</span><span class="sxs-lookup"><span data-stu-id="94dad-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94dad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94dad-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="94dad-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94dad-105">Remarks</span></span>  
 <span data-ttu-id="94dad-106">Bezpiecznie programu Profiler do inspekcji obiektów w lokalizacjach końcowego podczas `GarbageCollectionFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="94dad-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94dad-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94dad-107">Requirements</span></span>  
 <span data-ttu-id="94dad-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94dad-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94dad-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="94dad-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="94dad-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94dad-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94dad-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94dad-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94dad-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94dad-112">See also</span></span>

- [<span data-ttu-id="94dad-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="94dad-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="94dad-114">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="94dad-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
