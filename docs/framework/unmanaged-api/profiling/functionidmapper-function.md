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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0320c831648c15dfec42c1b693be2f13e6888ae9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475167"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="3fc96-102">FunctionIDMapper — Funkcja</span><span class="sxs-lookup"><span data-stu-id="3fc96-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="3fc96-103">Powiadamia program profilujący, że identyfikator danej funkcji może być ponownie mapowany do alternatywnego Identyfikatora do użycia w [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołań zwrotnych tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3fc96-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="3fc96-104">`FunctionIDMapper` Umożliwia także profilującemu wskazanie, czy chce odbierać wywołania zwrotne do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3fc96-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc96-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fc96-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fc96-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fc96-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="3fc96-107">[in] Identyfikator funkcji ma być ponownie mapowany.</span><span class="sxs-lookup"><span data-stu-id="3fc96-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="3fc96-108">[out] Wskaźnik do wartości, która ustawia program profilujący `true` jeśli chce otrzymać `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` wywołań zwrotnych; w przeciwnym wypadku ustawia tę wartość na `false`.</span><span class="sxs-lookup"><span data-stu-id="3fc96-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fc96-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3fc96-109">Return Value</span></span>  
 <span data-ttu-id="3fc96-110">Program profilujący zwraca wartość, której używa silnik wykonawczy jako identyfikatora alternatywnej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3fc96-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="3fc96-111">Zwracana wartość nie może mieć wartości null Jeśli nie `false` jest zwracany w `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="3fc96-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="3fc96-112">W przeciwnym wypadku zwracana wartość null powoduje wygenerowanie produkuje nieoczekiwanych rezultatów, w tym ewentualnie powstrzymanie procesu.</span><span class="sxs-lookup"><span data-stu-id="3fc96-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fc96-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3fc96-113">Remarks</span></span>  
 <span data-ttu-id="3fc96-114">`FunctionIDMapper` Funkcja jest wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="3fc96-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="3fc96-115">Jest stosowana przez profiler, aby ponownie zamapować nazwę funkcji, aby inny identyfikator, który jest bardziej użyteczna w przypadku programu profilującego.</span><span class="sxs-lookup"><span data-stu-id="3fc96-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="3fc96-116">`FunctionIDMapper` Zwraca alternatywny identyfikator służący do daną funkcję.</span><span class="sxs-lookup"><span data-stu-id="3fc96-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="3fc96-117">Następnie aparat wykonywania honoruje żądania programu profilującego, przekazując to alternatywny identyfikator, oprócz identyfikator funkcji tradycyjnego, wróć do programu profilującego w `clientData` parametru `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` punkty zaczepienia do identyfikowania Funkcja, dla którego punkt zaczepienia jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3fc96-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="3fc96-118">Możesz użyć [icorprofilerinfo::setfunctionidmapper —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metodę, aby określić implementację `FunctionIDMapper` funkcji.</span><span class="sxs-lookup"><span data-stu-id="3fc96-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="3fc96-119">Możesz wywołać `ICorProfilerInfo::SetFunctionIDMapper` metody tylko raz, a firma Microsoft zaleca, aby zrobić to w [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3fc96-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="3fc96-120">Domyślnie, zakłada się, że program profilujący, ustawia flagę COR_PRF_MONITOR_ENTERLEAVE przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), i która określa punkty zaczepienia za pośrednictwem [icorprofilerinfo::setenterleavefunctionhooks —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [icorprofilerinfo2::setenterleavefunctionhooks2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien zostać wyświetlony `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` wywołania zwrotne dla każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3fc96-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="3fc96-121">Jednak może wdrożyć profilery `FunctionIDMapper` zapobiegających selektywnego odbierania te wywołania zwrotne dla niektórych funkcji, ustawiając `pbHookFunction` do `false`.</span><span class="sxs-lookup"><span data-stu-id="3fc96-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="3fc96-122">Profilery powinien być odporny na błędy przypadków, gdy wiele wątków profilowana aplikacja wywołania dotyczą tej samej metody/funkcji jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="3fc96-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="3fc96-123">W takich przypadkach program profilujący może pojawić się wiele `FunctionIDMapper` wywołania zwrotne dla tego samego `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="3fc96-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="3fc96-124">Program profilujący powinien być niektórych zwracać tej samej wartości z to wywołanie zwrotne, gdy jest wywoływana wiele razy z takimi samymi `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="3fc96-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fc96-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3fc96-125">Requirements</span></span>  
 <span data-ttu-id="3fc96-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fc96-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fc96-127">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3fc96-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3fc96-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fc96-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fc96-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fc96-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc96-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fc96-130">See also</span></span>
- [<span data-ttu-id="3fc96-131">SetFunctionIDMapper, metoda</span><span class="sxs-lookup"><span data-stu-id="3fc96-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="3fc96-132">FunctionIDMapper2, funkcja</span><span class="sxs-lookup"><span data-stu-id="3fc96-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [<span data-ttu-id="3fc96-133">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="3fc96-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="3fc96-134">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="3fc96-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="3fc96-135">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="3fc96-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="3fc96-136">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="3fc96-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
