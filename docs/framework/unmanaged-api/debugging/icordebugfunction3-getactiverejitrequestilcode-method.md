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
ms.openlocfilehash: 9e7f682752cfefae63b574655a4fc5e8964146a0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213182"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="06e89-102">Metoda ICorDebugFunction3::GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="06e89-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="06e89-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="06e89-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="06e89-104">Pobiera wskaźnik interfejsu do [ICorDebugILCode](icordebugilcode-interface.md) zawierającego Il z aktywnego żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="06e89-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e89-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="06e89-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06e89-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="06e89-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="06e89-107">Wskaźnik do IL z aktywnego żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="06e89-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06e89-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06e89-108">Remarks</span></span>  
 <span data-ttu-id="06e89-109">Jeśli metoda reprezentowana przez ten `ICorDebugFunction3` obiekt ma aktywne żądanie ReJIT, `ppReJitedILCode` zwraca wskaźnik do jego Il.</span><span class="sxs-lookup"><span data-stu-id="06e89-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="06e89-110">Jeśli nie ma aktywnych żądań, które są typowym przypadkiem, wówczas `ppReJitedILCode` ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="06e89-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="06e89-111">Żądanie ReJIT jest uaktywniane tuż po powrocie wykonania z wywołania metody [ICorProfilerCallback4:: GetReJITParameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="06e89-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="06e89-112">Może nie być jeszcze skompilowana w trybie JIT, a wątki nadal mogą być wykonywane w pierwotnej wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="06e89-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="06e89-113">Żądanie ReJIT stanie się nieaktywne w trakcie wywołania profilera do metody [ICorProfilerInfo4:: RequestRevert —](../profiling/icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="06e89-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="06e89-114">Nawet po przywróceniu kodu IL wątek nadal może być wykonywany w kodzie JIT-rekompilowanym (ReJIT).</span><span class="sxs-lookup"><span data-stu-id="06e89-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06e89-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06e89-115">Requirements</span></span>  
 <span data-ttu-id="06e89-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06e89-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06e89-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="06e89-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06e89-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06e89-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06e89-119">**.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06e89-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e89-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06e89-120">See also</span></span>

- [<span data-ttu-id="06e89-121">Interfejs ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="06e89-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="06e89-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="06e89-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="06e89-123">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="06e89-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
