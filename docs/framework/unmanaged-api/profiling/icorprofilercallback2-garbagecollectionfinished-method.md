---
title: "ICorProfilerCallback2::GarbageCollectionFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.GarbageCollectionFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 287c33a80144b9b04fd7e0797071d40e46a52454
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="88dbd-102">ICorProfilerCallback2::GarbageCollectionFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="88dbd-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="88dbd-103">Powiadamia profilera, że ukończono wyrzucanie elementów bezużytecznych i wszystkie wywołania zwrotne kolekcji pamięci zostały wydane dla niego.</span><span class="sxs-lookup"><span data-stu-id="88dbd-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88dbd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88dbd-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="88dbd-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88dbd-105">Remarks</span></span>  
 <span data-ttu-id="88dbd-106">Bezpiecznie dla profiler do zbadania obiektów w ich lokalizacji końcowej podczas `GarbageCollectionFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="88dbd-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88dbd-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88dbd-107">Requirements</span></span>  
 <span data-ttu-id="88dbd-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88dbd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88dbd-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="88dbd-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="88dbd-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88dbd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88dbd-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88dbd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88dbd-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88dbd-112">See Also</span></span>  
 [<span data-ttu-id="88dbd-113">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="88dbd-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="88dbd-114">ICorProfilerCallback2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="88dbd-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
