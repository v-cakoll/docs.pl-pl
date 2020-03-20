---
title: ICorProfilerInfo10, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175073"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="46ee3-102">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="46ee3-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="46ee3-103">Podklasa [ICorProfilerInfo9,](icorprofilerinfo9-interface.md) która udostępnia metody modyfikowania funkcji IL, kwerendy informacji ze środowiska wykonawczego i zawiesić i wznowić środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="46ee3-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="46ee3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="46ee3-104">Methods</span></span>  

| <span data-ttu-id="46ee3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="46ee3-105">Method</span></span>|<span data-ttu-id="46ee3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="46ee3-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="46ee3-107">EnumerateObjectReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="46ee3-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="46ee3-108">Biorąc pod uwagę ObjectID, wywołania zwrotnego i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="46ee3-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="46ee3-109">IsFrozenObject, metoda</span><span class="sxs-lookup"><span data-stu-id="46ee3-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="46ee3-110">Biorąc pod uwagę ObjectID, określa, czy obiekt znajduje się w segmencie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="46ee3-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="46ee3-111">GetLOHObjectSizeThreshold, metoda</span><span class="sxs-lookup"><span data-stu-id="46ee3-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="46ee3-112">Pobiera wartość skonfigurowanego progu LOH.</span><span class="sxs-lookup"><span data-stu-id="46ee3-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="46ee3-113">RequestReJITWithInliners, metoda</span><span class="sxs-lookup"><span data-stu-id="46ee3-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="46ee3-114">ReJITs metody wymagane, jak również wszelkie inlinera metod wymaganych metod.</span><span class="sxs-lookup"><span data-stu-id="46ee3-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="46ee3-115">SuspendRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="46ee3-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="46ee3-116">Zawiesza środowisko wykonawcze bez wykonywania GC.</span><span class="sxs-lookup"><span data-stu-id="46ee3-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="46ee3-117">ResumeRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="46ee3-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="46ee3-118">Wznawia środowisko wykonawcze bez wykonywania GC.</span><span class="sxs-lookup"><span data-stu-id="46ee3-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="46ee3-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46ee3-119">Requirements</span></span>  
<span data-ttu-id="46ee3-120">**Platformy:** Zobacz [.NET Core obsługiwane systemy operacyjne](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="46ee3-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
<span data-ttu-id="46ee3-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46ee3-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="46ee3-122">**Wersje .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46ee3-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="46ee3-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46ee3-123">See also</span></span>

- [<span data-ttu-id="46ee3-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="46ee3-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
