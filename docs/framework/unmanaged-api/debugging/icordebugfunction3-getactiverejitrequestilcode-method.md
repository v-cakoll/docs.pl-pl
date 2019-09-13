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
ms.openlocfilehash: 4985a448321eceabf7975a8e5b638043f6c88723
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926854"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="3fc2b-102">Metoda ICorDebugFunction3::GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="3fc2b-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="3fc2b-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="3fc2b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3fc2b-104">Pobiera wskaźnik interfejsu do [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) zawierającego Il z aktywnego żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="3fc2b-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc2b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fc2b-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fc2b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fc2b-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="3fc2b-107">Wskaźnik do IL z aktywnego żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="3fc2b-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fc2b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3fc2b-108">Remarks</span></span>  
 <span data-ttu-id="3fc2b-109">Jeśli metoda reprezentowana przez ten `ICorDebugFunction3` obiekt ma aktywne żądanie ReJIT, `ppReJitedILCode` zwraca wskaźnik do jego Il.</span><span class="sxs-lookup"><span data-stu-id="3fc2b-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="3fc2b-110">Jeśli nie ma aktywnych żądań, które są typowym przypadkiem, wówczas `ppReJitedILCode` ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="3fc2b-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="3fc2b-111">Żądanie ReJIT jest uaktywniane tuż po powrocie wykonania z wywołania metody [ICorProfilerCallback4:: GetReJITParameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3fc2b-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="3fc2b-112">Może nie być jeszcze skompilowana w trybie JIT, a wątki nadal mogą być wykonywane w pierwotnej wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="3fc2b-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="3fc2b-113">Żądanie ReJIT stanie się nieaktywne w trakcie wywołania profilera do metody [ICorProfilerInfo4:: RequestRevert —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3fc2b-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="3fc2b-114">Nawet po przywróceniu kodu IL wątek nadal może być wykonywany w kodzie JIT-rekompilowanym (ReJIT).</span><span class="sxs-lookup"><span data-stu-id="3fc2b-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fc2b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3fc2b-115">Requirements</span></span>  
 <span data-ttu-id="3fc2b-116">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fc2b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fc2b-117">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fc2b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fc2b-118">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fc2b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fc2b-119">**.NET Framework wersje:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fc2b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc2b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fc2b-120">See also</span></span>

- [<span data-ttu-id="3fc2b-121">ICorDebugFunction3, interfejs</span><span class="sxs-lookup"><span data-stu-id="3fc2b-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [<span data-ttu-id="3fc2b-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3fc2b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3fc2b-123">ReJIT: Przewodnik krok po kroku</span><span class="sxs-lookup"><span data-stu-id="3fc2b-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
