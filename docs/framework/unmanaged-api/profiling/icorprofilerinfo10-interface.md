---
title: ICorProfilerInfo10, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2bc716110c14972e5b2c32bceb3123b16e87c61
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449846"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="86f58-102">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="86f58-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="86f58-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span><span class="sxs-lookup"><span data-stu-id="86f58-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="86f58-104">Metody</span><span class="sxs-lookup"><span data-stu-id="86f58-104">Methods</span></span>  

| <span data-ttu-id="86f58-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="86f58-105">Method</span></span>|<span data-ttu-id="86f58-106">Opis</span><span class="sxs-lookup"><span data-stu-id="86f58-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="86f58-107">EnumerateObjectReferences Method</span><span class="sxs-lookup"><span data-stu-id="86f58-107">EnumerateObjectReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="86f58-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span><span class="sxs-lookup"><span data-stu-id="86f58-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="86f58-109">IsFrozenObject Method</span><span class="sxs-lookup"><span data-stu-id="86f58-109">IsFrozenObject Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="86f58-110">Given an ObjectID, determines whether the object is in a read-only segment.</span><span class="sxs-lookup"><span data-stu-id="86f58-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="86f58-111">GetLOHObjectSizeThreshold Method</span><span class="sxs-lookup"><span data-stu-id="86f58-111">GetLOHObjectSizeThreshold Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="86f58-112">Gets the value of the configured LOH threshold.</span><span class="sxs-lookup"><span data-stu-id="86f58-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="86f58-113">RequestReJITWithInliners Method</span><span class="sxs-lookup"><span data-stu-id="86f58-113">RequestReJITWithInliners Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="86f58-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span><span class="sxs-lookup"><span data-stu-id="86f58-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="86f58-115">SuspendRuntime Method</span><span class="sxs-lookup"><span data-stu-id="86f58-115">SuspendRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="86f58-116">Suspends the runtime without performing a GC.</span><span class="sxs-lookup"><span data-stu-id="86f58-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="86f58-117">ResumeRuntime Method</span><span class="sxs-lookup"><span data-stu-id="86f58-117">ResumeRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="86f58-118">Resumes the runtime without performing a GC.</span><span class="sxs-lookup"><span data-stu-id="86f58-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="86f58-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86f58-119">Requirements</span></span>  
<span data-ttu-id="86f58-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="86f58-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="86f58-121">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86f58-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="86f58-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f58-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="86f58-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86f58-123">See also</span></span>

- [<span data-ttu-id="86f58-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="86f58-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
