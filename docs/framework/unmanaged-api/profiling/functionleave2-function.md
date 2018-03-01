---
title: "FunctionLeave2 — Funkcja"
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
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86ffb6cc18de0b0b7b68b418477c1e8cdd6e6cc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="functionleave2-function"></a><span data-ttu-id="2ff2b-102">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2ff2b-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="2ff2b-103">Powiadamia profilera, że funkcja ma zwrócić do obiektu wywołującego i zawiera informacje o stosu ramki i funkcja wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ff2b-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ff2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ff2b-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="2ff2b-106">[in] Identyfikator funkcji, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="2ff2b-107">[in] Identyfikator ponownie zmapowany funkcji, który profilera wcześniej określona za pomocą [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="2ff2b-108">[in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="2ff2b-109">Profiler należy potraktować jako nieprzezroczystego uchwyt, które mogą być przekazywane z powrotem do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="2ff2b-110">[in] Wskaźnik do [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) strukturę, która określa lokalizację pamięci wartości zwracanej przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="2ff2b-111">Aby uzyskać dostęp do informacji wartości zwracanej `COR_PRF_ENABLE_FUNCTION_RETVAL` musi zostać ustawiona flaga.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="2ff2b-112">Można użyć profilera [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody można ustawić flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ff2b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ff2b-113">Remarks</span></span>  
 <span data-ttu-id="2ff2b-114">Wartości `func` i `retvalRange` parametry nie są prawidłowe po `FunctionLeave2` funkcja zwraca, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="2ff2b-115">`FunctionLeave2` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="2ff2b-116">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="2ff2b-117">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-117">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="2ff2b-118">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="2ff2b-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="2ff2b-119">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="2ff2b-120">Implementacja `FunctionLeave2` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="2ff2b-121">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="2ff2b-122">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionLeave2` zwraca.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="2ff2b-123">Ponadto `FunctionLeave2` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="2ff2b-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff2b-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ff2b-124">Requirements</span></span>  
 <span data-ttu-id="2ff2b-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff2b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff2b-126">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="2ff2b-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2ff2b-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ff2b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ff2b-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff2b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff2b-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ff2b-129">See Also</span></span>  
 [<span data-ttu-id="2ff2b-130">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="2ff2b-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="2ff2b-131">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="2ff2b-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="2ff2b-132">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="2ff2b-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="2ff2b-133">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="2ff2b-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
