---
title: FunctionTailcall3 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82d718c6f6aee36f3a916eb7f9b9a1e0b3b46cb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="22506-102">FunctionTailcall3 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="22506-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="22506-103">Powiadamia profilera aktualnie wykonywane funkcja o zbliżającym się wykonywać wywołania tail na inną funkcję.</span><span class="sxs-lookup"><span data-stu-id="22506-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22506-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22506-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22506-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22506-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="22506-106">[in] Identyfikator aktualnie wykonywane funkcji, która wprowadzi tail wywołania.</span><span class="sxs-lookup"><span data-stu-id="22506-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22506-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22506-107">Remarks</span></span>  
 <span data-ttu-id="22506-108">`FunctionTailcall3` Funkcja wywołania zwrotnego powiadamia profilera, ponieważ funkcje są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="22506-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="22506-109">Użyj [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) zarejestrować implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="22506-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="22506-110">`FunctionTailcall3` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="22506-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="22506-111">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="22506-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="22506-112">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="22506-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="22506-113">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="22506-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="22506-114">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="22506-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="22506-115">Implementacja `FunctionTailcall3` nie zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="22506-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="22506-116">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="22506-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="22506-117">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionTailcall3` zwraca.</span><span class="sxs-lookup"><span data-stu-id="22506-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="22506-118">`FunctionTailcall3` Funkcji nie musi wywołania wewnątrz kodu zarządzanego lub spowodować przydział pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="22506-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22506-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22506-119">Requirements</span></span>  
 <span data-ttu-id="22506-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22506-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22506-121">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="22506-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="22506-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22506-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22506-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22506-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22506-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22506-124">See Also</span></span>  
 [<span data-ttu-id="22506-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="22506-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="22506-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="22506-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="22506-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="22506-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="22506-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="22506-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="22506-129">FunctionTailcall3WithInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="22506-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="22506-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="22506-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="22506-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="22506-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="22506-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="22506-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="22506-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="22506-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="22506-134">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="22506-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
