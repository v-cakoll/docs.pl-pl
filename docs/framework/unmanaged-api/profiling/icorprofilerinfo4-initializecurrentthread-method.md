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
ms.openlocfilehash: b52a0e7f993629c1005883723c734996d75300a7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868437"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="b6766-102">ICorProfilerInfo4::InitializeCurrentThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6766-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="b6766-103">Inicjuje bieżący wątek przed kolejnymi wywołaniami interfejsu API profilera w tym samym wątku, aby można było uniknąć zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="b6766-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6766-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6766-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b6766-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6766-105">Remarks</span></span>  
 <span data-ttu-id="b6766-106">Zalecamy wywołanie `InitializeCurrentThread` w dowolnym wątku, który wywoła interfejs API profilera, gdy są zawieszone wątki.</span><span class="sxs-lookup"><span data-stu-id="b6766-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="b6766-107">Ta metoda jest zwykle używana przez pliki do próbkowania, które tworzą własny wątek wywołujący [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metodę, aby wykonać przeszukiwanie stosu, gdy wątek docelowy jest zawieszony.</span><span class="sxs-lookup"><span data-stu-id="b6766-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="b6766-108">Wywołując `InitializeCurrentThread` raz, gdy profiler najpierw tworzy wątek próbkowania, mogą one zagwarantować, że inicjalizacja każdego wątku środowiska CLR w przeciwnym razie będzie działać podczas pierwszego wywołania do `DoStackSnapshot` może być bezpiecznie wykonywana, gdy nie zostaną wstrzymane żadne inne wątki.</span><span class="sxs-lookup"><span data-stu-id="b6766-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6766-109">`InitializeCurrentThread` wykonuje inicjalizację, aby zakończyć zadania, które mają blokadę i mogą być zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="b6766-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="b6766-110">Wywołaj `InitializeCurrentThread` tylko wtedy, gdy nie ma żadnych zawieszonych wątków.</span><span class="sxs-lookup"><span data-stu-id="b6766-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6766-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6766-111">Requirements</span></span>  
 <span data-ttu-id="b6766-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6766-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6766-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b6766-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6766-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6766-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6766-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6766-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6766-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6766-116">See also</span></span>

- [<span data-ttu-id="b6766-117">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6766-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b6766-118">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b6766-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b6766-119">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="b6766-119">Profiling</span></span>](index.md)
