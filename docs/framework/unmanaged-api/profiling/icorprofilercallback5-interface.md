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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072652"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="17750-102">ICorProfilerCallback5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="17750-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="17750-103">Uzupełnia informacje pomagające zidentyfikować pełne zamknięcie obiekty na żywo, gdy jest używana z oboma program profilujący [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) lub [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)metoda wraz z [icorprofilercallback::objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) i [conditionalweaktableelementreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="17750-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="17750-104">`ICorProfilerCallback5` muszą być zaimplementowane przez profiler pamięci zarządzanej do subskrybowania powiadomień uchwytów związanych z zależnych.</span><span class="sxs-lookup"><span data-stu-id="17750-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17750-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17750-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17750-106">Metody</span><span class="sxs-lookup"><span data-stu-id="17750-106">Methods</span></span>  
  
|<span data-ttu-id="17750-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="17750-107">Method</span></span>|<span data-ttu-id="17750-108">Opis</span><span class="sxs-lookup"><span data-stu-id="17750-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17750-109">ConditionalWeakTableElementReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="17750-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="17750-110">Identyfikuje przechodnie zamknięcia obiektów, odwołuje się katalogami, za pomocą odwołania do obu pól bezpośrednim członkiem i za pomocą `ConditionalWeakTable` zależności.</span><span class="sxs-lookup"><span data-stu-id="17750-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17750-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17750-111">Requirements</span></span>  
 <span data-ttu-id="17750-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17750-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17750-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17750-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17750-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17750-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17750-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17750-115">See also</span></span>

- [<span data-ttu-id="17750-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="17750-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="17750-117">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="17750-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
