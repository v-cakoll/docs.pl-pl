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
ms.openlocfilehash: 736e76a57e6dbce76267ad0fdd242897b4bfdbd2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746890"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="13c04-102">ICorProfilerCallback2::GarbageCollectionFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="13c04-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="13c04-103">Powiadamia program profilujący, że wyrzucanie elementów bezużytecznych zostało ukończone, a wszystkie wywołania wyrzucania elementów bezużytecznych zostały wydane dla niego.</span><span class="sxs-lookup"><span data-stu-id="13c04-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c04-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13c04-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="13c04-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13c04-105">Remarks</span></span>  
 <span data-ttu-id="13c04-106">Bezpiecznie programu Profiler do inspekcji obiektów w lokalizacjach końcowego podczas `GarbageCollectionFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="13c04-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c04-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13c04-107">Requirements</span></span>  
 <span data-ttu-id="13c04-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c04-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c04-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13c04-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13c04-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13c04-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13c04-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c04-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c04-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13c04-112">See also</span></span>

- [<span data-ttu-id="13c04-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="13c04-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="13c04-114">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="13c04-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
