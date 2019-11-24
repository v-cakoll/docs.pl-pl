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
ms.openlocfilehash: ce34d43091cdee0bca88f94711e49072fa4fd08c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430066"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="719d5-102">ICorProfilerCallback5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="719d5-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="719d5-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span><span class="sxs-lookup"><span data-stu-id="719d5-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="719d5-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span><span class="sxs-lookup"><span data-stu-id="719d5-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="719d5-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="719d5-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="719d5-106">Metody</span><span class="sxs-lookup"><span data-stu-id="719d5-106">Methods</span></span>  
  
|<span data-ttu-id="719d5-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="719d5-107">Method</span></span>|<span data-ttu-id="719d5-108">Opis</span><span class="sxs-lookup"><span data-stu-id="719d5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="719d5-109">ConditionalWeakTableElementReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="719d5-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="719d5-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span><span class="sxs-lookup"><span data-stu-id="719d5-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="719d5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="719d5-111">Requirements</span></span>  
 <span data-ttu-id="719d5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="719d5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="719d5-113">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="719d5-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="719d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="719d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="719d5-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="719d5-115">See also</span></span>

- [<span data-ttu-id="719d5-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="719d5-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="719d5-117">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="719d5-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
