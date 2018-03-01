---
title: "ICorProfilerCallback::JITInlining — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3990fdf1bcf76592288aac35b47b15f42cf77bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="2df10-102">ICorProfilerCallback::JITInlining — Metoda</span><span class="sxs-lookup"><span data-stu-id="2df10-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="2df10-103">Powiadamia profilera kompilatora just-in-time (JIT) o zbliżającym się Wstawianie funkcji z inną funkcję.</span><span class="sxs-lookup"><span data-stu-id="2df10-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df10-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2df10-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2df10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2df10-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="2df10-106">[in] Identyfikator funkcji, do którego `calleeId` zostanie wstawiona funkcja.</span><span class="sxs-lookup"><span data-stu-id="2df10-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="2df10-107">[in] Identyfikator funkcji do wstawienia.</span><span class="sxs-lookup"><span data-stu-id="2df10-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="2df10-108">[out] `true` do wstawiania występuje; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="2df10-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2df10-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2df10-109">Remarks</span></span>  
 <span data-ttu-id="2df10-110">Można ustawić profilera `pfShouldInline` do `false` zapobiegające `calleeId` funkcji wstawiane do `callerId` funkcji.</span><span class="sxs-lookup"><span data-stu-id="2df10-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="2df10-111">Ponadto profilera globalnie można wyłączyć wbudowanego wstawiania za pomocą wartości COR_PRF_DISABLE_INLINING [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2df10-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="2df10-112">Dodaje funkcje wbudowane nie wywołuj zdarzenia o.</span><span class="sxs-lookup"><span data-stu-id="2df10-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="2df10-113">W związku z tym należy ustawić profilera `pfShouldInline` do `false` w celu uzyskania dokładnych Wykres wywołań.</span><span class="sxs-lookup"><span data-stu-id="2df10-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="2df10-114">Ustawienie `pfShouldInline` do `false` będzie miało wpływ na wydajność, ponieważ wstawiania wbudowanego zwykle zwiększa szybkość i zmniejsza liczbę odrębne zdarzenia kompilacji JIT wstawionego metody.</span><span class="sxs-lookup"><span data-stu-id="2df10-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df10-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2df10-115">Requirements</span></span>  
 <span data-ttu-id="2df10-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2df10-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df10-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2df10-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2df10-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2df10-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2df10-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df10-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df10-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2df10-120">See Also</span></span>  
 [<span data-ttu-id="2df10-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="2df10-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
