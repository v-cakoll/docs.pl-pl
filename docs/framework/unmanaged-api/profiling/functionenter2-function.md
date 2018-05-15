---
title: FunctionEnter2 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d79249a2540adbd7f1b7e9bf36c899ba94d71e2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="functionenter2-function"></a><span data-ttu-id="f306f-102">FunctionEnter2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f306f-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="f306f-103">Powiadamia profilera, czy formant jest przekazywany do funkcji i zawiera informacje o stosie argumenty ramki i funkcji.</span><span class="sxs-lookup"><span data-stu-id="f306f-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="f306f-104">Ta funkcja zastępuje [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="f306f-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f306f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f306f-105">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f306f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f306f-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="f306f-107">[in] Identyfikator funkcji, do którego jest przekazywany formantu.</span><span class="sxs-lookup"><span data-stu-id="f306f-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="f306f-108">[in] Identyfikator ponownie zmapowany funkcji, który profilera wcześniej określony za pomocą [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="f306f-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="f306f-109">[in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="f306f-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="f306f-110">Profiler należy potraktować jako nieprzezroczystego uchwyt, które mogą być przekazywane z powrotem do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f306f-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="f306f-111">[in] Wskaźnik do [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktury, która określa lokalizacje w pamięci argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="f306f-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="f306f-112">Aby uzyskać dostęp do informacji argument `COR_PRF_ENABLE_FUNCTION_ARGS` musi zostać ustawiona flaga.</span><span class="sxs-lookup"><span data-stu-id="f306f-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="f306f-113">Można użyć profilera [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody można ustawić flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f306f-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f306f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f306f-114">Remarks</span></span>  
 <span data-ttu-id="f306f-115">Wartości `func` i `argumentInfo` parametry nie są prawidłowe po `FunctionEnter2` funkcja zwraca, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.</span><span class="sxs-lookup"><span data-stu-id="f306f-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="f306f-116">`FunctionEnter2` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="f306f-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="f306f-117">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="f306f-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="f306f-118">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f306f-118">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="f306f-119">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="f306f-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="f306f-120">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f306f-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f306f-121">Implementacja `FunctionEnter2` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f306f-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="f306f-122">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="f306f-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f306f-123">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionEnter2` zwraca.</span><span class="sxs-lookup"><span data-stu-id="f306f-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="f306f-124">Ponadto `FunctionEnter2` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="f306f-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f306f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f306f-125">Requirements</span></span>  
 <span data-ttu-id="f306f-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f306f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f306f-127">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f306f-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f306f-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f306f-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f306f-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f306f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f306f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f306f-130">See Also</span></span>  
 [<span data-ttu-id="f306f-131">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="f306f-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="f306f-132">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="f306f-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="f306f-133">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="f306f-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="f306f-134">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="f306f-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
