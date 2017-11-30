---
title: "ICorProfilerInfo4::InitializeCurrentThread — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc19ae86c266c74097bd649aa96f532528df3d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="15d1c-102">ICorProfilerInfo4::InitializeCurrentThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="15d1c-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="15d1c-103">Inicjuje bieżący wątek klienta z wyprzedzeniem kolejnych profilera, który wywołania interfejsu API w tym samym wątku, aby uniknąć tego zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="15d1c-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15d1c-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="15d1c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15d1c-105">Remarks</span></span>  
 <span data-ttu-id="15d1c-106">Firma Microsoft zaleca, aby wywołać `InitializeCurrentThread` w którymkolwiek wątku, który będzie dzwonić profiler interfejsu API, gdy są zawieszone wątków.</span><span class="sxs-lookup"><span data-stu-id="15d1c-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="15d1c-107">Ta metoda jest zwykle używana przez profilowania próbkowania, które utworzyć własne wątku do wywołania [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) przedstawiono metodę w celu stosu podczas docelowy wątek jest zawieszony.</span><span class="sxs-lookup"><span data-stu-id="15d1c-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="15d1c-108">Wywołując `InitializeCurrentThread` po po profilera najpierw tworzy wątku próbkowania, profilery można zapewnić, inicjowanie tego wątku opóźnieniem, które wykonywania innych podczas pierwszego wywołania do środowiska CLR `DoStackSnapshot` może teraz wystąpić bezpiecznie kiedy są nie ma innych wątków zawieszone.</span><span class="sxs-lookup"><span data-stu-id="15d1c-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15d1c-109">`InitializeCurrentThread`nie inicjowania z wyprzedzeniem, aby zakończyć zadania wykonuj blokad, które mogą zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="15d1c-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="15d1c-110">Wywołanie `InitializeCurrentThread` tylko wtedy, gdy nie ma żadnych zawieszonych wątków.</span><span class="sxs-lookup"><span data-stu-id="15d1c-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15d1c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15d1c-111">Requirements</span></span>  
 <span data-ttu-id="15d1c-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15d1c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d1c-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15d1c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15d1c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15d1c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15d1c-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15d1c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d1c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15d1c-116">See Also</span></span>  
 [<span data-ttu-id="15d1c-117">ICorProfilerInfo4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="15d1c-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="15d1c-118">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="15d1c-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="15d1c-119">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="15d1c-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
