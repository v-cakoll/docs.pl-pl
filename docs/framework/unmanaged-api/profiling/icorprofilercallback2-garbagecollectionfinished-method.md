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
ms.openlocfilehash: 47f25dbb1f88dbf580b096246016cd46f2d0d89c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499832"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="c1ee7-102">ICorProfilerCallback2::GarbageCollectionFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1ee7-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="c1ee7-103">Powiadamia profiler, że wyrzucanie elementów bezużytecznych zostało ukończone i wydano wszystkie wywołania zwrotne elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c1ee7-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ee7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1ee7-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c1ee7-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1ee7-105">Remarks</span></span>  
 <span data-ttu-id="c1ee7-106">Program profilujący może bezpiecznie zbadać obiekty w ich końcowych lokalizacjach, gdy `GarbageCollectionFinished` wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="c1ee7-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1ee7-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1ee7-107">Requirements</span></span>  
 <span data-ttu-id="c1ee7-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1ee7-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1ee7-109">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c1ee7-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1ee7-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c1ee7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1ee7-111">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1ee7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ee7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1ee7-112">See also</span></span>

- [<span data-ttu-id="c1ee7-113">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c1ee7-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c1ee7-114">ICorProfilerCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c1ee7-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
