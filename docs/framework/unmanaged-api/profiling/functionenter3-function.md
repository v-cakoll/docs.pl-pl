---
title: "FunctionEnter3 — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter3
helpviewer_keywords: FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08ab1b6adc3d4038a57a187519e96c7a07f1e6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter3-function"></a><span data-ttu-id="5876c-102">FunctionEnter3 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5876c-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="5876c-103">Powiadamia profilera, czy formant jest przekazywany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="5876c-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5876c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5876c-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5876c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5876c-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="5876c-106">[in] Identyfikator funkcji, do którego jest przekazywany formantu.</span><span class="sxs-lookup"><span data-stu-id="5876c-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5876c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5876c-107">Remarks</span></span>  
 <span data-ttu-id="5876c-108">`FunctionEnter3` Funkcja wywołania zwrotnego powiadamia profilera jako funkcje są wywoływane, ale nie nie kontroli argument pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="5876c-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="5876c-109">Użyj [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) zarejestrować implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="5876c-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="5876c-110">`FunctionEnter3` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="5876c-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="5876c-111">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="5876c-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="5876c-112">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="5876c-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="5876c-113">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="5876c-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="5876c-114">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5876c-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5876c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5876c-115">Requirements</span></span>  
 <span data-ttu-id="5876c-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5876c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5876c-117">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5876c-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5876c-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5876c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5876c-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5876c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5876c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5876c-120">See Also</span></span>  
 [<span data-ttu-id="5876c-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="5876c-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="5876c-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="5876c-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="5876c-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5876c-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="5876c-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5876c-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="5876c-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5876c-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="5876c-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="5876c-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="5876c-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5876c-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="5876c-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="5876c-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="5876c-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="5876c-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="5876c-130">Statyczne funkcje globalne profilowania</span><span class="sxs-lookup"><span data-stu-id="5876c-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
