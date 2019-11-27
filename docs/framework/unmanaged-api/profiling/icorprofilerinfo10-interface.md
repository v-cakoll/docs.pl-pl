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
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="7a73e-102">ICorProfilerInfo10, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a73e-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="7a73e-103">Podklasa elementu [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) , która udostępnia metody modyfikowania funkcji IL, zapytania o informacje z środowiska uruchomieniowego oraz wstrzymywanie i wznawianie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7a73e-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="7a73e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7a73e-104">Methods</span></span>  

| <span data-ttu-id="7a73e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7a73e-105">Method</span></span>|<span data-ttu-id="7a73e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7a73e-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="7a73e-107">EnumerateObjectReferences, Metoda</span><span class="sxs-lookup"><span data-stu-id="7a73e-107">EnumerateObjectReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="7a73e-108">Podanym identyfikatorem ObjectID, wywołaniem zwrotnym i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="7a73e-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="7a73e-109">Zamrożonobject, Metoda</span><span class="sxs-lookup"><span data-stu-id="7a73e-109">IsFrozenObject Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="7a73e-110">Przy użyciu identyfikatora ObjectID określa, czy obiekt znajduje się w segmencie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="7a73e-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="7a73e-111">GetLOHObjectSizeThreshold, Metoda</span><span class="sxs-lookup"><span data-stu-id="7a73e-111">GetLOHObjectSizeThreshold Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="7a73e-112">Pobiera wartość skonfigurowanego progu LOH.</span><span class="sxs-lookup"><span data-stu-id="7a73e-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="7a73e-113">RequestReJITWithInliners, Metoda</span><span class="sxs-lookup"><span data-stu-id="7a73e-113">RequestReJITWithInliners Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="7a73e-114">ReJITs wymagane metody, a także wszystkie wbudowane metody.</span><span class="sxs-lookup"><span data-stu-id="7a73e-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="7a73e-115">SuspendRuntime, Metoda</span><span class="sxs-lookup"><span data-stu-id="7a73e-115">SuspendRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="7a73e-116">Wstrzymuje środowisko uruchomieniowe bez wykonywania operacji GC.</span><span class="sxs-lookup"><span data-stu-id="7a73e-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="7a73e-117">ResumeRuntime, Metoda</span><span class="sxs-lookup"><span data-stu-id="7a73e-117">ResumeRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="7a73e-118">Wznawia środowisko uruchomieniowe bez wykonywania operacji GC.</span><span class="sxs-lookup"><span data-stu-id="7a73e-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="7a73e-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a73e-119">Requirements</span></span>  
<span data-ttu-id="7a73e-120">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="7a73e-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="7a73e-121">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7a73e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="7a73e-122">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a73e-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="7a73e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a73e-123">See also</span></span>

- [<span data-ttu-id="7a73e-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="7a73e-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
