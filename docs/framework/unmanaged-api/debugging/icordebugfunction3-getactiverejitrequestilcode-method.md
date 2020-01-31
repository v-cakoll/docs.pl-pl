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
ms.openlocfilehash: 70a55b833acb7fa946c694a63e1e8b51562938bc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777730"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="be2c1-102">Metoda ICorDebugFunction3::GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="be2c1-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="be2c1-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="be2c1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="be2c1-104">Pobiera wskaźnik interfejsu do [ICorDebugILCode](icordebugilcode-interface.md) zawierającego Il z aktywnego żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="be2c1-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be2c1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="be2c1-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be2c1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="be2c1-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="be2c1-107">Wskaźnik do IL z aktywnego żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="be2c1-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be2c1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be2c1-108">Remarks</span></span>  
 <span data-ttu-id="be2c1-109">Jeśli metoda reprezentowana przez ten obiekt `ICorDebugFunction3` ma aktywne żądanie ReJIT, `ppReJitedILCode` zwraca wskaźnik do jego IL.</span><span class="sxs-lookup"><span data-stu-id="be2c1-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="be2c1-110">Jeśli nie ma aktywnych żądań, które są typowym przypadkiem, `ppReJitedILCode` ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="be2c1-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="be2c1-111">Żądanie ReJIT jest uaktywniane tuż po powrocie wykonania z wywołania metody [ICorProfilerCallback4:: GetReJITParameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="be2c1-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="be2c1-112">Może nie być jeszcze skompilowana w trybie JIT, a wątki nadal mogą być wykonywane w pierwotnej wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="be2c1-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="be2c1-113">Żądanie ReJIT stanie się nieaktywne w trakcie wywołania profilera do metody [ICorProfilerInfo4:: RequestRevert —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="be2c1-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="be2c1-114">Nawet po przywróceniu kodu IL wątek nadal może być wykonywany w kodzie JIT-rekompilowanym (ReJIT).</span><span class="sxs-lookup"><span data-stu-id="be2c1-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be2c1-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be2c1-115">Requirements</span></span>  
 <span data-ttu-id="be2c1-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be2c1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be2c1-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be2c1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be2c1-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="be2c1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be2c1-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be2c1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2c1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be2c1-120">See also</span></span>

- [<span data-ttu-id="be2c1-121">ICorDebugFunction3, interfejs</span><span class="sxs-lookup"><span data-stu-id="be2c1-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="be2c1-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="be2c1-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="be2c1-123">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="be2c1-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
