---
title: ICorProfilerCallback::JITInlining — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 844ac2a8aad4ce2cc6f70de2d5a53c7c0b6f4f6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="de4c8-102">ICorProfilerCallback::JITInlining — Metoda</span><span class="sxs-lookup"><span data-stu-id="de4c8-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="de4c8-103">Powiadamia profilera kompilatora just-in-time (JIT) o zbliżającym się Wstawianie funkcji z inną funkcję.</span><span class="sxs-lookup"><span data-stu-id="de4c8-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de4c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de4c8-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de4c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de4c8-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="de4c8-106">[in] Identyfikator funkcji, do którego `calleeId` zostanie wstawiona funkcja.</span><span class="sxs-lookup"><span data-stu-id="de4c8-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="de4c8-107">[in] Identyfikator funkcji do wstawienia.</span><span class="sxs-lookup"><span data-stu-id="de4c8-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="de4c8-108">[out] `true` do wstawiania występuje; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="de4c8-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de4c8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de4c8-109">Remarks</span></span>  
 <span data-ttu-id="de4c8-110">Można ustawić profilera `pfShouldInline` do `false` zapobiegające `calleeId` funkcji wstawiane do `callerId` funkcji.</span><span class="sxs-lookup"><span data-stu-id="de4c8-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="de4c8-111">Ponadto profilera globalnie można wyłączyć wbudowanego wstawiania za pomocą wartości COR_PRF_DISABLE_INLINING [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="de4c8-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="de4c8-112">Dodaje funkcje wbudowane nie wywołuj zdarzenia o.</span><span class="sxs-lookup"><span data-stu-id="de4c8-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="de4c8-113">W związku z tym należy ustawić profilera `pfShouldInline` do `false` w celu uzyskania dokładnych Wykres wywołań.</span><span class="sxs-lookup"><span data-stu-id="de4c8-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="de4c8-114">Ustawienie `pfShouldInline` do `false` będzie miało wpływ na wydajność, ponieważ wstawiania wbudowanego zwykle zwiększa szybkość i zmniejsza liczbę odrębne zdarzenia kompilacji JIT wstawionego metody.</span><span class="sxs-lookup"><span data-stu-id="de4c8-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de4c8-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de4c8-115">Requirements</span></span>  
 <span data-ttu-id="de4c8-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de4c8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de4c8-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="de4c8-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de4c8-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de4c8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de4c8-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de4c8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de4c8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de4c8-120">See Also</span></span>  
 [<span data-ttu-id="de4c8-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="de4c8-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
