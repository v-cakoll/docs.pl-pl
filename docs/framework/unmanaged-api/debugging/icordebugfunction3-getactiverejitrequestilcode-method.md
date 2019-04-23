---
title: Metoda ICorDebugFunction3::GetActiveReJitRequestILCode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6268019f2e65c7c9209e00c0b6065e91103980c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115885"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="f0955-102">Metoda ICorDebugFunction3::GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="f0955-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="f0955-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="f0955-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f0955-104">Pobiera wskaźnik interfejsu do [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) zawierający IL z aktywne żądanie ReJIT.</span><span class="sxs-lookup"><span data-stu-id="f0955-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0955-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0955-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0955-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0955-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="f0955-107">Wskaźnik do IL od aktywne żądanie ReJIT.</span><span class="sxs-lookup"><span data-stu-id="f0955-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0955-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0955-108">Remarks</span></span>  
 <span data-ttu-id="f0955-109">Jeśli metoda reprezentowany przez ten `ICorDebugFunction3` obiekt ma aktywne żądanie ReJIT `ppReJitedILCode` zwraca wskaźnik do jego IL.</span><span class="sxs-lookup"><span data-stu-id="f0955-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="f0955-110">Jeśli nie istnieje żadne aktywne żądanie, który jest przypadkiem typowe `ppReJitedILCode` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="f0955-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="f0955-111">Żądanie ReJIT staje się aktywny po wykonywanie powraca z [icorprofilercallback4::getrejitparameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="f0955-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="f0955-112">Nie może jeszcze być kompilowany dokładnie na czas i wątki nadal mogą być wykonywane w pierwotnej wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="f0955-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="f0955-113">Żądanie ReJIT staje się nieaktywny podczas wywoływania programu profilującego [icorprofilerinfo4::requestrevert —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f0955-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="f0955-114">Nawet po zakończeniu przywróconych IL to wątek może nadal wykonywane w kodzie ponownie skompilowana JIT (ReJIT).</span><span class="sxs-lookup"><span data-stu-id="f0955-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0955-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0955-115">Requirements</span></span>  
 <span data-ttu-id="f0955-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0955-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0955-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0955-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0955-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0955-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0955-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0955-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0955-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0955-120">See also</span></span>

- [<span data-ttu-id="f0955-121">ICorDebugFunction3, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0955-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [<span data-ttu-id="f0955-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0955-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f0955-123">ReJIT: Przewodniku z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="f0955-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
