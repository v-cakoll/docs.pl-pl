---
title: "FunctionIDMapper — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionIDMapper
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionIDMapper
helpviewer_keywords: FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 629bcd5085169fcb136884c53434c29d385642cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="functionidmapper-function"></a><span data-ttu-id="b2c0a-102">FunctionIDMapper — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b2c0a-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="b2c0a-103">Powiadamia profilera, że danym identyfikatorem funkcji mogą być mapowane ponownie do alternatywny identyfikator ma być używany w [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołań zwrotnych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="b2c0a-104">`FunctionIDMapper`Umożliwia również profilera wskazać, czy chce odbierać wywołań zwrotnych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c0a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2c0a-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2c0a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2c0a-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="b2c0a-107">[in] Identyfikator funkcji można zamapować go ponownie.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="b2c0a-108">[out] Wskaźnik do wartości, która ustawia profilera `true` jeśli chce otrzymywać `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` wywołania zwrotne; w przeciwnym razie ustawia tę wartość na `false`.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2c0a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b2c0a-109">Return Value</span></span>  
 <span data-ttu-id="b2c0a-110">Profiler zwraca wartość używaną przez aparat wykonywania jako identyfikator alternatywny funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="b2c0a-111">Wartość zwrotna nie może mieć wartości null chyba że `false` jest zwracany w `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="b2c0a-112">W przeciwnym razie zwrócenie wartości null da nieoczekiwane wyniki, w tym prawdopodobnie zatrzymywanie procesu.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2c0a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2c0a-113">Remarks</span></span>  
 <span data-ttu-id="b2c0a-114">`FunctionIDMapper` Funkcja jest wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="b2c0a-115">Jest stosowana przez profiler ponownie zmapować Identyfikatora funkcji do innego identyfikatora, który jest bardziej użyteczna w przypadku profilera.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="b2c0a-116">`FunctionIDMapper` Zwraca alternatywny identyfikator służący do daną funkcję.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="b2c0a-117">Aparat wykonywania następnie honoruje żądania profiler od przekazania to alternatywny identyfikator jako uzupełnienie Identyfikatora tradycyjnych funkcja profilera w `clientData` parametr `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` punkty zaczepienia, aby zidentyfikować Funkcja, dla którego jest wywoływana haka.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="b2c0a-118">Można użyć [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metodę, aby określić wykonania `FunctionIDMapper` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="b2c0a-119">Możesz wywołać `ICorProfilerInfo::SetFunctionIDMapper` metody tylko raz i firma Microsoft zaleca, należy więc w [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="b2c0a-120">Domyślnie zakłada się, że profiler który ustawia flagę COR_PRF_MONITOR_ENTERLEAVE przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), i który ustawia punkty zaczepienia za pośrednictwem [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien zostać wyświetlony `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` wywołań zwrotnych dla każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="b2c0a-121">Jednak może wdrożyć profilery `FunctionIDMapper` Aby selektywnie uniknąć otrzymywania tych wywołań zwrotnych dla niektórych funkcji, ustawiając `pbHookFunction` do `false`.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="b2c0a-122">Profilery powinien być odporny na błędy przypadków, gdzie wiele wątków profilowana aplikacja wywoływania tej samej metody/funkcja jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="b2c0a-123">W takich przypadkach profiler może pojawić się wiele `FunctionIDMapper` wywołań zwrotnych dla tego samego `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="b2c0a-124">Profiler upewnij się zwrócić takie same wartości z tego wywołania zwrotnego przy wywołaniu wiele razy z tym samym `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="b2c0a-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c0a-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2c0a-125">Requirements</span></span>  
 <span data-ttu-id="b2c0a-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c0a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c0a-127">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b2c0a-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b2c0a-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2c0a-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2c0a-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c0a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c0a-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2c0a-130">See Also</span></span>  
 [<span data-ttu-id="b2c0a-131">SetFunctionIDMapper — metoda</span><span class="sxs-lookup"><span data-stu-id="b2c0a-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="b2c0a-132">Functionidmapper2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="b2c0a-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [<span data-ttu-id="b2c0a-133">Functionenter2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="b2c0a-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="b2c0a-134">Functionleave2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="b2c0a-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="b2c0a-135">Functiontailcall2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="b2c0a-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="b2c0a-136">Statyczne funkcje globalne profilowania</span><span class="sxs-lookup"><span data-stu-id="b2c0a-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
