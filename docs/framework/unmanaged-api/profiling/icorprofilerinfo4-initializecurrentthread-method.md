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
ms.openlocfilehash: b9bb5a2629e435d76691d48feef6689191b66373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957890"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="68f1e-102">ICorProfilerInfo4::InitializeCurrentThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="68f1e-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="68f1e-103">Inicjuje bieżący wątek przed kolejnymi wywołaniami interfejsu API profilera w tym samym wątku, aby można było uniknąć zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="68f1e-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f1e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68f1e-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="68f1e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68f1e-105">Remarks</span></span>  
 <span data-ttu-id="68f1e-106">Zalecamy wywołanie `InitializeCurrentThread` w dowolnym wątku, który wywoła interfejs API profilera, gdy są zawieszone wątki.</span><span class="sxs-lookup"><span data-stu-id="68f1e-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="68f1e-107">Ta metoda jest zwykle używana przez pliki do próbkowania, które tworzą własny wątek wywołujący [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodę, aby wykonać przeszukiwanie stosu, gdy wątek docelowy jest zawieszony.</span><span class="sxs-lookup"><span data-stu-id="68f1e-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="68f1e-108">Wywołując `InitializeCurrentThread` jednokrotnie, gdy profiler najpierw tworzy wątek próbkowania, mogą one zapewnić, że Inicjowanie z opóźnieniem dla wątku, które w przeciwnym razie będzie działać podczas pierwszego `DoStackSnapshot` wywołania, może teraz być bezpiecznie wykonywane, gdy nie są używane żadne inne wątki wieszon.</span><span class="sxs-lookup"><span data-stu-id="68f1e-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68f1e-109">`InitializeCurrentThread`Czy Inicjalizacja zakończyła się z wyprzedzeniem, aby zakończyć zadania, które zostały zablokowane i mogą być zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="68f1e-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="68f1e-110">Wywołaj `InitializeCurrentThread` tylko wtedy, gdy nie ma żadnych zawieszonych wątków.</span><span class="sxs-lookup"><span data-stu-id="68f1e-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f1e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68f1e-111">Requirements</span></span>  
 <span data-ttu-id="68f1e-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f1e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f1e-113">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="68f1e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68f1e-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68f1e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68f1e-115">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f1e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f1e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68f1e-116">See also</span></span>

- [<span data-ttu-id="68f1e-117">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="68f1e-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="68f1e-118">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="68f1e-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="68f1e-119">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="68f1e-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
