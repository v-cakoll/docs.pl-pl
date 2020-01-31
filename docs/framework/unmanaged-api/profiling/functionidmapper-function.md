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
ms.openlocfilehash: d5bf6626e2c6ba15fa9a5da08bcf2d9052866750
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866947"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="d1d68-102">FunctionIDMapper — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d1d68-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="d1d68-103">Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)i [FunctionTailcall2](functiontailcall2-function.md) dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1d68-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="d1d68-104">`FunctionIDMapper` również umożliwia profilerowi określenie, czy chce otrzymywać wywołania zwrotne dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1d68-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d68-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1d68-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1d68-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1d68-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="d1d68-107">\[] identyfikator funkcji, która ma zostać ponownie zmapowana.</span><span class="sxs-lookup"><span data-stu-id="d1d68-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="d1d68-108">\[out] wskaźnik do wartości, która jest ustawiana przez profiler `true`, jeśli chce otrzymywać `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` wywołania zwrotne; w przeciwnym razie ustawia tę wartość na `false`.</span><span class="sxs-lookup"><span data-stu-id="d1d68-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d1d68-109">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="d1d68-109">Return Value</span></span>  
 <span data-ttu-id="d1d68-110">Profiler zwraca wartość, którą aparat wykonywania używa jako alternatywnego identyfikatora funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1d68-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="d1d68-111">Zwracana wartość nie może mieć wartości null, chyba że `false` jest zwracana w `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="d1d68-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="d1d68-112">W przeciwnym razie wartość zwracana null będzie generować nieprzewidywalne wyniki, w tym prawdopodobnie zatrzymanie procesu.</span><span class="sxs-lookup"><span data-stu-id="d1d68-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1d68-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1d68-113">Remarks</span></span>  
 <span data-ttu-id="d1d68-114">Funkcja `FunctionIDMapper` jest wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="d1d68-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="d1d68-115">Jest implementowany przez profiler, aby ponownie mapować identyfikator funkcji na inny identyfikator, który jest bardziej przydatny dla profilera.</span><span class="sxs-lookup"><span data-stu-id="d1d68-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="d1d68-116">`FunctionIDMapper` zwraca alternatywny identyfikator, który ma być używany dla danej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1d68-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="d1d68-117">Aparat wykonywania następnie będzie przestrzegać żądania profilera przez przekazanie tego alternatywnego identyfikatora, oprócz tradycyjnego identyfikatora funkcji, z powrotem do profilera w `clientData` parametr `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` punkty zaczepienia, aby zidentyfikować funkcję, dla której jest wywoływany element Hook.</span><span class="sxs-lookup"><span data-stu-id="d1d68-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="d1d68-118">Aby określić implementację funkcji `FunctionIDMapper`, można użyć metody [ICorProfilerInfo:: SetFunctionIDMapper —](icorprofilerinfo-setfunctionidmapper-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d1d68-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="d1d68-119">Metodę `ICorProfilerInfo::SetFunctionIDMapper` można wywołać tylko raz i zalecamy wykonanie tego w [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d1d68-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="d1d68-120">Domyślnie zakłada się, że profiler ustawiający flagę COR_PRF_MONITOR_ENTERLEAVE przy użyciu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)i który ustawia haki za pośrednictwem [ICorProfilerInfo:: SetEnterLeaveFunctionHooks —](icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 —](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien otrzymać `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` wywołania zwrotne dla każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1d68-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="d1d68-121">Jednakże można zaimplementować program do `FunctionIDMapper`, aby selektywnie unikać otrzymywania wywołania zwrotnego dla niektórych funkcji przez ustawienie `pbHookFunction` do `false`.</span><span class="sxs-lookup"><span data-stu-id="d1d68-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="d1d68-122">Profilowani powinni być odporne na uszkodzenia przypadków, w których wiele wątków profilowanej aplikacji jednocześnie wywołuje tę samą metodę/funkcję.</span><span class="sxs-lookup"><span data-stu-id="d1d68-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="d1d68-123">W takich przypadkach profiler może odbierać wiele wywołań zwrotnych `FunctionIDMapper` dla tego samego `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="d1d68-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="d1d68-124">Profiler powinien mieć pewność, że zwracają te same wartości z tego wywołania zwrotnego, gdy jest wywoływana wiele razy z tą samą `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="d1d68-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d68-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1d68-125">Requirements</span></span>  
 <span data-ttu-id="d1d68-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1d68-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d68-127">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="d1d68-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d1d68-128">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d1d68-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1d68-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d68-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d68-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1d68-130">See also</span></span>

- [<span data-ttu-id="d1d68-131">SetFunctionIDMapper, metoda</span><span class="sxs-lookup"><span data-stu-id="d1d68-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d1d68-132">FunctionIDMapper2, funkcja</span><span class="sxs-lookup"><span data-stu-id="d1d68-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="d1d68-133">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="d1d68-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="d1d68-134">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="d1d68-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="d1d68-135">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="d1d68-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="d1d68-136">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="d1d68-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
