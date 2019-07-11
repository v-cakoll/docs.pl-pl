---
title: ICorProfilerInfo4::InitializeCurrentThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abcbfaf803e930baaaf798986a585a7da5f9134d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780799"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="ac27e-102">ICorProfilerInfo4::InitializeCurrentThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac27e-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="ac27e-103">Inicjuje bieżący wątek ewentualnej profilującym kolejnych wywołań interfejsu API w tym samym wątku, dzięki czemu można uniknąć tego zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="ac27e-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac27e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac27e-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ac27e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac27e-105">Remarks</span></span>  
 <span data-ttu-id="ac27e-106">Firma Microsoft zaleca wywołanie `InitializeCurrentThread` dotyczące dowolnego wątku, który będzie wybierany program profilujący interfejsu API, gdy istnieją wstrzymane wątki.</span><span class="sxs-lookup"><span data-stu-id="ac27e-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="ac27e-107">Ta metoda jest zwykle używana przez profilowania próbkowania, tworzonych z własnych wątków do wywoływania [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) przedstawia metodę w celu stosu, gdy wątek docelowy jest wstrzymane.</span><span class="sxs-lookup"><span data-stu-id="ac27e-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="ac27e-108">Przez wywołanie metody `InitializeCurrentThread` po kiedy profiler najpierw tworzy wątek próbkowania, profilery zagwarantować, że inicjowanie wątku z opóźnieniem, w przeciwnym razie wykona środowiska CLR Podczas pierwszego wywołania `DoStackSnapshot` teraz możliwe bezpiecznie kiedy są nie ma innych wątków zawieszone.</span><span class="sxs-lookup"><span data-stu-id="ac27e-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac27e-109">`InitializeCurrentThread` wykonuje inicjowanie z wyprzedzeniem, aby zakończyć zadania, które były blokad i może zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="ac27e-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="ac27e-110">Wywołaj `InitializeCurrentThread` tylko wtedy, gdy nie istnieją wątki zawieszone.</span><span class="sxs-lookup"><span data-stu-id="ac27e-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac27e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac27e-111">Requirements</span></span>  
 <span data-ttu-id="ac27e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac27e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac27e-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac27e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac27e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac27e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac27e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac27e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac27e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac27e-116">See also</span></span>

- [<span data-ttu-id="ac27e-117">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac27e-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="ac27e-118">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="ac27e-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ac27e-119">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="ac27e-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
