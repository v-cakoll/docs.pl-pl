---
title: FunctionIDMapper — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175177"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="ffad2-102">FunctionIDMapper — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ffad2-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="ffad2-103">Powiadamia profiler, że dany identyfikator funkcji może być ponownie mapowany na alternatywny identyfikator, który ma być używany w [functionenter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)i [FunctionTailcall2](functiontailcall2-function.md) wywołania zwrotne dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ffad2-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="ffad2-104">`FunctionIDMapper`również umożliwia profilera, aby wskazać, czy chce odbierać wywołania zwrotne dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ffad2-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffad2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffad2-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffad2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffad2-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="ffad2-107">\[w] Identyfikator funkcji, który ma zostać ponownie zamapowany.</span><span class="sxs-lookup"><span data-stu-id="ffad2-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="ffad2-108">\[out] Wskaźnik do wartości, którą profiler `true` ustawia, jeśli `FunctionEnter2` `FunctionLeave2`chce `FunctionTailcall2` odbierać , i wywołania zwrotne; w przeciwnym razie ustawia `false`tę wartość na .</span><span class="sxs-lookup"><span data-stu-id="ffad2-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ffad2-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ffad2-109">Return Value</span></span>  
 <span data-ttu-id="ffad2-110">Profiler zwraca wartość, która aparat wykonywania używa jako alternatywny identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="ffad2-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="ffad2-111">Zwracana wartość nie `false` może być `pbHookFunction`null, chyba że jest zwracana w .</span><span class="sxs-lookup"><span data-stu-id="ffad2-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="ffad2-112">W przeciwnym razie wartość zwracana null spowoduje nieprzewidywalne wyniki, w tym ewentualnie zatrzymanie procesu.</span><span class="sxs-lookup"><span data-stu-id="ffad2-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffad2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffad2-113">Remarks</span></span>  
 <span data-ttu-id="ffad2-114">Funkcja `FunctionIDMapper` jest wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="ffad2-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="ffad2-115">Jest implementowany przez profiler do ponownego mapowania identyfikatora funkcji do innego identyfikatora, który jest bardziej przydatny dla profilera.</span><span class="sxs-lookup"><span data-stu-id="ffad2-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="ffad2-116">Zwraca `FunctionIDMapper` alternatywny identyfikator, który ma być używany dla danej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ffad2-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="ffad2-117">Aparat wykonywania następnie honoruje żądanie profilera, przekazując ten alternatywny identyfikator, oprócz tradycyjnego identyfikatora funkcji, `clientData` z `FunctionEnter2`powrotem do profilera w parametrze , `FunctionLeave2`i `FunctionTailcall2` haki, aby zidentyfikować funkcję, dla której hak jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="ffad2-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="ffad2-118">Za pomocą metody [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) można określić `FunctionIDMapper` implementację funkcji.</span><span class="sxs-lookup"><span data-stu-id="ffad2-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="ffad2-119">`ICorProfilerInfo::SetFunctionIDMapper` Metodę można wywołać tylko raz i zaleca się to zrobić w [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="ffad2-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="ffad2-120">Domyślnie zakłada się, że profiler, który ustawia flagę COR_PRF_MONITOR_ENTERLEAVE za pomocą [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), i który ustawia haki za pośrednictwem [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien odbierać `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` wywołania zwrotne dla każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ffad2-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="ffad2-121">Jednak profilerzy mogą `FunctionIDMapper` zaimplementować, aby selektywnie unikać `pbHookFunction` odbierania tych wywołań zwrotnych dla niektórych funkcji, ustawiając na `false`.</span><span class="sxs-lookup"><span data-stu-id="ffad2-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="ffad2-122">Profilerzy powinny być tolerancyjne przypadków, w których wiele wątków profilowane aplikacji są wywołanie tej samej metody/funkcji jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="ffad2-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="ffad2-123">W takich przypadkach profiler może `FunctionIDMapper` odbierać wiele `FunctionID`wywołań zwrotnych dla tego samego .</span><span class="sxs-lookup"><span data-stu-id="ffad2-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="ffad2-124">Profiler powinien być pewny, aby zwrócić te same wartości z tego `FunctionID`wywołania zwrotnego, gdy jest wywoływana wiele razy z tym samym .</span><span class="sxs-lookup"><span data-stu-id="ffad2-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffad2-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffad2-125">Requirements</span></span>  
 <span data-ttu-id="ffad2-126">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffad2-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffad2-127">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ffad2-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ffad2-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffad2-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffad2-129">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffad2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffad2-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ffad2-130">See also</span></span>

- [<span data-ttu-id="ffad2-131">SetFunctionIDMapper, metoda</span><span class="sxs-lookup"><span data-stu-id="ffad2-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="ffad2-132">FunctionIDMapper2, funkcja</span><span class="sxs-lookup"><span data-stu-id="ffad2-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="ffad2-133">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="ffad2-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="ffad2-134">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ffad2-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="ffad2-135">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="ffad2-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="ffad2-136">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="ffad2-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
