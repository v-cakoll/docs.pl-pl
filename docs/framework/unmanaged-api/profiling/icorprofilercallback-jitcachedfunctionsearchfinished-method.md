---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: 6efc9d407bb95f75a79252b2dfad85b396d2164a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500081"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="b7341-102">ICorProfilerCallback::JITCachedFunctionSearchFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7341-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="b7341-103">Powiadamia profiler o zakończeniu wyszukiwania dla funkcji, która została skompilowana wcześniej przy użyciu natywnego generatora obrazu (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="b7341-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7341-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7341-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7341-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7341-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="b7341-106">\[in] identyfikator funkcji, dla której wykonano wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="b7341-106">\[in] The ID of the function for which the search was performed.</span></span>

- `result`

  <span data-ttu-id="b7341-107">\[in) wartość wyliczenia [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) , która wskazuje wynik wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="b7341-107">\[in] A value of the [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7341-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7341-108">Remarks</span></span>  
 <span data-ttu-id="b7341-109">W .NET Framework w wersji 2,0 [ICorProfilerCallback:: JITCachedFunctionSearchStarted —](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) i `JITCachedFunctionSearchFinished` wywołania zwrotne nie zostaną wykonane dla wszystkich funkcji w zwykłych obrazach Ngen.</span><span class="sxs-lookup"><span data-stu-id="b7341-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="b7341-110">Tylko obrazy NGen zoptymalizowane pod kątem profilera generują wywołania zwrotne dla wszystkich funkcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="b7341-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="b7341-111">Jednak ze względu na dodatkowe obciążenie, profiler powinien zażądać obrazów NGen zoptymalizowanych pod kątem profilera tylko wtedy, gdy zamierza użyć tych wywołań zwrotnych w celu wymuszenia skompilowania funkcji just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="b7341-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="b7341-112">W przeciwnym razie Profiler powinien używać strategii z opóźnieniem do zbierania informacji o funkcji.</span><span class="sxs-lookup"><span data-stu-id="b7341-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7341-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7341-113">Requirements</span></span>  
 <span data-ttu-id="b7341-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7341-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7341-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b7341-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b7341-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b7341-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7341-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7341-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7341-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7341-118">See also</span></span>

- [<span data-ttu-id="b7341-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b7341-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
