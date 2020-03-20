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
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177062"
---
# <a name="functionenter2-function"></a><span data-ttu-id="4ae7e-102">FunctionEnter2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4ae7e-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="4ae7e-103">Powiadamia profiler, że formant jest przekazywany do funkcji i zawiera informacje o ramce stosu i argumenty funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="4ae7e-104">Ta funkcja zastępuje [functionenter](functionenter-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae7e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ae7e-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ae7e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ae7e-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="4ae7e-107">\[w] Identyfikator funkcji, do której formant jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="4ae7e-108">\[w] Semmapowany identyfikator funkcji, który profiler wcześniej określony za pomocą [functionidmapper](functionidmapper-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="4ae7e-109">\[w] `COR_PRF_FRAME_INFO` Wartość, która wskazuje informacje o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="4ae7e-110">Profiler należy traktować to jako nieprzezroczysty dojście, które mogą być przekazywane z powrotem do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="4ae7e-111">\[w] Wskaźnik do [struktury COR_PRF_FUNCTION_ARGUMENT_INFO,](cor-prf-function-argument-info-structure.md) który określa lokalizacje w pamięci argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="4ae7e-112">Aby uzyskać dostęp do `COR_PRF_ENABLE_FUNCTION_ARGS` informacji o argudze, należy ustawić flagę.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="4ae7e-113">Profiler można użyć [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) metody, aby ustawić flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ae7e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ae7e-114">Remarks</span></span>  
 <span data-ttu-id="4ae7e-115">Wartości `func` i `argumentInfo` parametry nie są prawidłowe po zwraca `FunctionEnter2` funkcję, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="4ae7e-116">Funkcja `FunctionEnter2` jest wywołaniem zwrotnym; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="4ae7e-117">Implementacja musi `__declspec`używać`naked`atrybutu () klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="4ae7e-118">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="4ae7e-119">Przy wprowadzaniu należy zapisać wszystkie używane rejestry, w tym rejestry w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="4ae7e-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="4ae7e-120">Po wyjściu należy przywrócić stosu przez popping off wszystkie parametry, które zostały wypchnięte przez jego wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="4ae7e-121">Implementacja `FunctionEnter2` nie należy blokować, ponieważ opóźni wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="4ae7e-122">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznym dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="4ae7e-123">Jeśli zostanie podjęta próba wyrzucania elementów `FunctionEnter2` bezużytecznych, środowisko uruchomieniowe zostanie zablokowane, dopóki nie zwróci.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="4ae7e-124">Ponadto `FunctionEnter2` funkcja nie może wywoływać kodu zarządzanego lub w jakikolwiek sposób powodować alokacji pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="4ae7e-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ae7e-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ae7e-125">Requirements</span></span>  
 <span data-ttu-id="4ae7e-126">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ae7e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ae7e-127">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="4ae7e-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4ae7e-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ae7e-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ae7e-129">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ae7e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae7e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ae7e-130">See also</span></span>

- [<span data-ttu-id="4ae7e-131">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4ae7e-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="4ae7e-132">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="4ae7e-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="4ae7e-133">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="4ae7e-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="4ae7e-134">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="4ae7e-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
