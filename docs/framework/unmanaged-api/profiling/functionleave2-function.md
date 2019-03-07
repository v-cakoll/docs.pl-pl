---
title: FunctionLeave2 — Funkcja
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9985b5a5547097c0474eb3a5797388d1444083e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471592"
---
# <a name="functionleave2-function"></a><span data-ttu-id="fb0d8-102">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="fb0d8-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="fb0d8-103">Powiadamia program profilujący, że funkcji ma zwrócić do elementu wywołującego i zawiera informacje dotyczące stosu ramki i funkcja wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb0d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb0d8-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb0d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb0d8-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="fb0d8-106">[in] Identyfikator funkcji, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="fb0d8-107">[in] Identyfikator funkcji ponownie zmapowany, który program profilujący wcześniej określona za pomocą [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="fb0d8-108">[in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="fb0d8-109">Program profilujący powinien traktować to jako nieprzezroczysty uchwyt, który może być przekazywany do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="fb0d8-110">[in] Wskaźnik do [cor_prf_function_argument_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) strukturę, która określa lokalizację w pamięci wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="fb0d8-111">Aby uzyskać dostęp do informacji o wartości zwracanej, `COR_PRF_ENABLE_FUNCTION_RETVAL` musi zostać ustawiona flaga.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="fb0d8-112">Można użyć programu profilującego [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić flagi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb0d8-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb0d8-113">Remarks</span></span>  
 <span data-ttu-id="fb0d8-114">Wartości `func` i `retvalRange` parametry nie są prawidłowe po `FunctionLeave2` funkcja zwraca wartości mogą ulec zmianie lub zostać zniszczone.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="fb0d8-115">`FunctionLeave2` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="fb0d8-116">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="fb0d8-117">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-117">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="fb0d8-118">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="fb0d8-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="fb0d8-119">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="fb0d8-120">Implementacja `FunctionLeave2` nie powinny blokować, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="fb0d8-121">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="fb0d8-122">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionLeave2` zwraca.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="fb0d8-123">Ponadto `FunctionLeave2` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="fb0d8-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb0d8-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb0d8-124">Requirements</span></span>  
 <span data-ttu-id="fb0d8-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb0d8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb0d8-126">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="fb0d8-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="fb0d8-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb0d8-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb0d8-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb0d8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb0d8-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb0d8-129">See also</span></span>
- [<span data-ttu-id="fb0d8-130">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="fb0d8-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="fb0d8-131">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="fb0d8-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="fb0d8-132">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="fb0d8-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="fb0d8-133">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="fb0d8-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
