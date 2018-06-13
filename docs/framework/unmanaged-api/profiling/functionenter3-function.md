---
title: FunctionEnter3 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 466b90f814d267fb289b2804beccd58fc442e341
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451883"
---
# <a name="functionenter3-function"></a><span data-ttu-id="41a6b-102">FunctionEnter3 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="41a6b-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="41a6b-103">Powiadamia profilera, czy formant jest przekazywany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="41a6b-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41a6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41a6b-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41a6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41a6b-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="41a6b-106">[in] Identyfikator funkcji, do którego jest przekazywany formantu.</span><span class="sxs-lookup"><span data-stu-id="41a6b-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41a6b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41a6b-107">Remarks</span></span>  
 <span data-ttu-id="41a6b-108">`FunctionEnter3` Funkcja wywołania zwrotnego powiadamia profilera jako funkcje są wywoływane, ale nie nie kontroli argument pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="41a6b-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="41a6b-109">Użyj [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) zarejestrować implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="41a6b-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="41a6b-110">`FunctionEnter3` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="41a6b-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="41a6b-111">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="41a6b-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="41a6b-112">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="41a6b-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="41a6b-113">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="41a6b-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="41a6b-114">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="41a6b-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41a6b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41a6b-115">Requirements</span></span>  
 <span data-ttu-id="41a6b-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41a6b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41a6b-117">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="41a6b-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="41a6b-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41a6b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41a6b-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41a6b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a6b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41a6b-120">See Also</span></span>  
 [<span data-ttu-id="41a6b-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="41a6b-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="41a6b-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="41a6b-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="41a6b-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="41a6b-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="41a6b-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="41a6b-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="41a6b-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="41a6b-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="41a6b-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="41a6b-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="41a6b-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="41a6b-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="41a6b-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="41a6b-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="41a6b-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="41a6b-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="41a6b-130">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="41a6b-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
