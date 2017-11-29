---
title: "FunctionLeave3 — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave3
helpviewer_keywords: FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11aa67a03cfb88910704c0f1d2f586f8dbed7d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave3-function"></a><span data-ttu-id="31a4e-102">FunctionLeave3 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="31a4e-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="31a4e-103">Powiadamia profilera, że formant zostały zwrócone z funkcji.</span><span class="sxs-lookup"><span data-stu-id="31a4e-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31a4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31a4e-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31a4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31a4e-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="31a4e-106">[in] Identyfikator funkcji zwróceniem sterowania.</span><span class="sxs-lookup"><span data-stu-id="31a4e-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31a4e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31a4e-107">Remarks</span></span>  
 <span data-ttu-id="31a4e-108">`FunctionLeave3` Funkcja wywołania zwrotnego powiadamia profilera funkcje są wywoływane, ale nie obsługuje inspekcji zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="31a4e-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="31a4e-109">Użyj [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) zarejestrować implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="31a4e-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="31a4e-110">`FunctionLeave3` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="31a4e-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="31a4e-111">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="31a4e-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="31a4e-112">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="31a4e-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="31a4e-113">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="31a4e-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="31a4e-114">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="31a4e-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="31a4e-115">Implementacja `FunctionLeave3` nie zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="31a4e-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="31a4e-116">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="31a4e-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="31a4e-117">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionLeave3` zwraca.</span><span class="sxs-lookup"><span data-stu-id="31a4e-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="31a4e-118">`FunctionLeave3` Funkcji nie musi wywołania wewnątrz kodu zarządzanego lub spowodować przydział pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="31a4e-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31a4e-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31a4e-119">Requirements</span></span>  
 <span data-ttu-id="31a4e-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31a4e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31a4e-121">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="31a4e-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="31a4e-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31a4e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31a4e-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31a4e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31a4e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31a4e-124">See Also</span></span>  
 [<span data-ttu-id="31a4e-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="31a4e-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="31a4e-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="31a4e-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="31a4e-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="31a4e-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="31a4e-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="31a4e-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="31a4e-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="31a4e-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="31a4e-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="31a4e-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="31a4e-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="31a4e-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="31a4e-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="31a4e-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="31a4e-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="31a4e-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="31a4e-134">Statyczne funkcje globalne profilowania</span><span class="sxs-lookup"><span data-stu-id="31a4e-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
