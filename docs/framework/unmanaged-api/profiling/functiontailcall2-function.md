---
title: "FunctionTailcall2 — Funkcja"
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
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a9d6ccb08bc09bea2ec9e9a49333c92da8cb5695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="af114-102">FunctionTailcall2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="af114-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="af114-103">Powiadamia profilera, że funkcja aktualnie wykonywane ma wykonywać wywołania tail do innej funkcji i zawiera informacje o ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="af114-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af114-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af114-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af114-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af114-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="af114-106">[in] Identyfikator aktualnie wykonywane funkcji, która wprowadzi tail wywołania.</span><span class="sxs-lookup"><span data-stu-id="af114-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="af114-107">[in] Identyfikator ponownie zmapowany funkcji, który profilera wcześniej określona za pomocą [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), aktualnie wykonywane funkcji, która wprowadzi tail wywołania.</span><span class="sxs-lookup"><span data-stu-id="af114-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="af114-108">[in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="af114-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="af114-109">Profiler należy potraktować jako nieprzezroczystego uchwyt, które mogą być przekazywane z powrotem do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="af114-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af114-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af114-110">Remarks</span></span>  
 <span data-ttu-id="af114-111">Funkcja docelowy wywołania tail użyje bieżącej ramki stosu i zwróci bezpośrednio do obiektu wywołującego zgłaszającego tail wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="af114-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="af114-112">Oznacza to, że [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) wywołania zwrotnego nie zostanie wystawiony dla funkcji, która jest elementem docelowym wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="af114-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="af114-113">Wartość `func` parametr jest nieprawidłowy po `FunctionTailcall2` funkcja zwraca, ponieważ wartość mogą ulec zmianie lub zostać zniszczone.</span><span class="sxs-lookup"><span data-stu-id="af114-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="af114-114">`FunctionTailcall2` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="af114-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="af114-115">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="af114-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="af114-116">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="af114-116">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="af114-117">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="af114-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="af114-118">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="af114-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="af114-119">Implementacja `FunctionTailcall2` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="af114-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="af114-120">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="af114-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="af114-121">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionTailcall2` zwraca.</span><span class="sxs-lookup"><span data-stu-id="af114-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="af114-122">Ponadto `FunctionTailcall2` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="af114-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af114-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af114-123">Requirements</span></span>  
 <span data-ttu-id="af114-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af114-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af114-125">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="af114-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="af114-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af114-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af114-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af114-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af114-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af114-128">See Also</span></span>  
 [<span data-ttu-id="af114-129">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="af114-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="af114-130">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="af114-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="af114-131">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="af114-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="af114-132">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="af114-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
