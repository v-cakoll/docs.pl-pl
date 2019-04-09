---
title: ICorProfilerCallback5 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 114d97e02b0a6b80c46f971ed74a24dc3c397f1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072652"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="2319f-102">ICorProfilerCallback5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2319f-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="2319f-103">Uzupełnia informacje pomagające zidentyfikować pełne zamknięcie obiekty na żywo, gdy jest używana z oboma program profilujący [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) lub [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)metoda wraz z [icorprofilercallback::objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) i [conditionalweaktableelementreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2319f-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 `ICorProfilerCallback5` <span data-ttu-id="2319f-104">muszą być zaimplementowane przez profiler pamięci zarządzanej do subskrybowania powiadomień uchwytów związanych z zależnych.</span><span class="sxs-lookup"><span data-stu-id="2319f-104">must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2319f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2319f-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2319f-106">Metody</span><span class="sxs-lookup"><span data-stu-id="2319f-106">Methods</span></span>  
  
|<span data-ttu-id="2319f-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="2319f-107">Method</span></span>|<span data-ttu-id="2319f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2319f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2319f-109">ConditionalWeakTableElementReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="2319f-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="2319f-110">Identyfikuje przechodnie zamknięcia obiektów, odwołuje się katalogami, za pomocą odwołania do obu pól bezpośrednim członkiem i za pomocą `ConditionalWeakTable` zależności.</span><span class="sxs-lookup"><span data-stu-id="2319f-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2319f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2319f-111">Requirements</span></span>  
 <span data-ttu-id="2319f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2319f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2319f-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2319f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="2319f-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2319f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2319f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2319f-115">See also</span></span>

- [<span data-ttu-id="2319f-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="2319f-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2319f-117">ICorProfilerCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2319f-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
