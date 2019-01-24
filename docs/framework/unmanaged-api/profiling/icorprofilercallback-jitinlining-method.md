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
ms.openlocfilehash: 53a8f9aefa4460493113c035aa05e971b05d5167
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500174"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="31fb0-102">ICorProfilerCallback::JITInlining — Metoda</span><span class="sxs-lookup"><span data-stu-id="31fb0-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="31fb0-103">Powiadamia program profilujący, że kompilator just-in-time (JIT) zostanie Wstawianie funkcji z innej funkcji.</span><span class="sxs-lookup"><span data-stu-id="31fb0-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31fb0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31fb0-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31fb0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31fb0-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="31fb0-106">[in] Identyfikator funkcji, do którego `calleeId` zostanie wstawiona funkcja.</span><span class="sxs-lookup"><span data-stu-id="31fb0-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="31fb0-107">[in] Identyfikator funkcji ma zostać wstawiony.</span><span class="sxs-lookup"><span data-stu-id="31fb0-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="31fb0-108">[out] `true` do wstawiania występuje; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="31fb0-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31fb0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31fb0-109">Remarks</span></span>  
 <span data-ttu-id="31fb0-110">Program profilujący może ustawić `pfShouldInline` do `false` zapobiegające `calleeId` funkcji z jest wstawiany do `callerId` funkcji.</span><span class="sxs-lookup"><span data-stu-id="31fb0-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="31fb0-111">Ponadto program profilujący globalnie wyłączyć wstawiania wbudowane za pomocą wartość COR_PRF_DISABLE_INLINING [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="31fb0-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="31fb0-112">Wbudowane funkcje wstawione nieznakowe inicjują zdarzenia o.</span><span class="sxs-lookup"><span data-stu-id="31fb0-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="31fb0-113">W związku z tym, należy ustawić program profilujący `pfShouldInline` do `false` aby wygenerować dokładne Wykres wywołań.</span><span class="sxs-lookup"><span data-stu-id="31fb0-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="31fb0-114">Ustawienie `pfShouldInline` do `false` będzie mieć wpływ na wydajność, ponieważ wstawiania wbudowane zwykle zwiększa szybkość i zmniejsza liczbę oddzielnych zdarzenia kompilacji JIT dla wstawionych metody.</span><span class="sxs-lookup"><span data-stu-id="31fb0-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31fb0-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31fb0-115">Requirements</span></span>  
 <span data-ttu-id="31fb0-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31fb0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31fb0-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31fb0-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31fb0-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31fb0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31fb0-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31fb0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fb0-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31fb0-120">See also</span></span>
- [<span data-ttu-id="31fb0-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="31fb0-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
