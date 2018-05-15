---
title: FunctionLeave3 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14f4f16a73c50de2d23804f77bca180f4e9827b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="functionleave3-function"></a><span data-ttu-id="5db20-102">FunctionLeave3 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5db20-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="5db20-103">Powiadamia profilera, że formant zostały zwrócone z funkcji.</span><span class="sxs-lookup"><span data-stu-id="5db20-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5db20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5db20-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5db20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5db20-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="5db20-106">[in] Identyfikator funkcji zwróceniem sterowania.</span><span class="sxs-lookup"><span data-stu-id="5db20-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5db20-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5db20-107">Remarks</span></span>  
 <span data-ttu-id="5db20-108">`FunctionLeave3` Funkcja wywołania zwrotnego powiadamia profilera funkcje są wywoływane, ale nie obsługuje inspekcji zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="5db20-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="5db20-109">Użyj [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) zarejestrować implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="5db20-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="5db20-110">`FunctionLeave3` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="5db20-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="5db20-111">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="5db20-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="5db20-112">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="5db20-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="5db20-113">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="5db20-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="5db20-114">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5db20-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="5db20-115">Implementacja `FunctionLeave3` nie zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5db20-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="5db20-116">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="5db20-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="5db20-117">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionLeave3` zwraca.</span><span class="sxs-lookup"><span data-stu-id="5db20-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="5db20-118">`FunctionLeave3` Funkcji nie musi wywołania wewnątrz kodu zarządzanego lub spowodować przydział pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="5db20-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5db20-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5db20-119">Requirements</span></span>  
 <span data-ttu-id="5db20-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5db20-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5db20-121">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5db20-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5db20-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5db20-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5db20-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5db20-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db20-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5db20-124">See Also</span></span>  
 [<span data-ttu-id="5db20-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="5db20-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="5db20-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="5db20-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="5db20-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5db20-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="5db20-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5db20-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="5db20-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5db20-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="5db20-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="5db20-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="5db20-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5db20-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="5db20-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="5db20-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="5db20-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="5db20-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="5db20-134">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="5db20-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
