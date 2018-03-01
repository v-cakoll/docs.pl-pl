---
title: "ICorProfilerCallback5 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0406b537f6f20d7194a0115020245ade101bd498
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="89553-102">ICorProfilerCallback5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="89553-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="89553-103">Uzupełnia informacje ułatwiające profiler zidentyfikować pełne zamknięcie obiekty na żywo, gdy jest używany z albo [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) lub [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)metody razem z [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) i [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="89553-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="89553-104">`ICorProfilerCallback5`musi być implementowana przez profiler pamięci zarządzanej do subskrybowania powiadomień uchwyty związane z zależnych.</span><span class="sxs-lookup"><span data-stu-id="89553-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89553-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89553-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89553-106">Metody</span><span class="sxs-lookup"><span data-stu-id="89553-106">Methods</span></span>  
  
|<span data-ttu-id="89553-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="89553-107">Method</span></span>|<span data-ttu-id="89553-108">Opis</span><span class="sxs-lookup"><span data-stu-id="89553-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89553-109">ConditionalWeakTableElementReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="89553-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="89553-110">Identyfikuje przechodnie zamknięcia odwołuje się katalogami za pomocą obu odwołania do pól bezpośrednimi elementami członkowskimi i za pomocą obiektów `ConditionalWeakTable` zależności.</span><span class="sxs-lookup"><span data-stu-id="89553-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89553-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89553-111">Requirements</span></span>  
 <span data-ttu-id="89553-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89553-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89553-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89553-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89553-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89553-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89553-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89553-115">See Also</span></span>  
 [<span data-ttu-id="89553-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="89553-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="89553-117">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="89553-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
