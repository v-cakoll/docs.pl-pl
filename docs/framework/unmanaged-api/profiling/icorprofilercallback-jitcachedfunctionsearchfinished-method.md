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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89c7b0fe0f3ade3f57aa50b100bc9b4ecc904a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452000"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="7c04f-102">ICorProfilerCallback::JITCachedFunctionSearchFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c04f-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="7c04f-103">Powiadamia profilera zakończenie wyszukiwania dla funkcji skompilowanego wcześniej przy użyciu Generator obrazu natywnego (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="7c04f-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c04f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c04f-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c04f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c04f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7c04f-106">[in] Identyfikator funkcji, dla którego wykonano wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="7c04f-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="7c04f-107">[in] Wartość [cor_prf_jit_cache —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) wyliczenia wskazująca wynik wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="7c04f-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c04f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c04f-108">Remarks</span></span>  
 <span data-ttu-id="7c04f-109">W programie .NET Framework w wersji 2.0 [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) i `JITCachedFunctionSearchFinished` wywołania zwrotne nie zostaną wprowadzone dla wszystkich funkcji w regularnych obrazów NGen.</span><span class="sxs-lookup"><span data-stu-id="7c04f-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="7c04f-110">Tylko obrazów NGen zoptymalizowane pod kątem profiler wygeneruje wywołań zwrotnych dla wszystkich funkcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="7c04f-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="7c04f-111">Jednak ze względu na dodatkowe obciążenie profiler powinien zażądać zoptymalizowanych pod kątem profilera obrazów NGen tylko, jeśli zamierza użyć tych wywołań zwrotnych, aby wymusić funkcję, która ma być skompilowany just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="7c04f-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="7c04f-112">W przeciwnym razie do zbierania informacji o funkcji strategii opóźnieniem należy używać profilera.</span><span class="sxs-lookup"><span data-stu-id="7c04f-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c04f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c04f-113">Requirements</span></span>  
 <span data-ttu-id="7c04f-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c04f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c04f-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c04f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c04f-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c04f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c04f-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c04f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c04f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c04f-118">See Also</span></span>  
 [<span data-ttu-id="7c04f-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c04f-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
