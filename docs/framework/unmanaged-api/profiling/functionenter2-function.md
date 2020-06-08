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
ms.openlocfilehash: 8c88e97f8187ac347f4ff39890c8d87ee80c8f9e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500718"
---
# <a name="functionenter2-function"></a><span data-ttu-id="89c0f-102">FunctionEnter2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="89c0f-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="89c0f-103">Powiadamia profiler, że sterowanie jest przesyłane do funkcji i zawiera informacje na temat ramki stosu i argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="89c0f-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="89c0f-104">Ta funkcja zastępuje funkcję [FunctionEnter —](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="89c0f-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89c0f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="89c0f-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89c0f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="89c0f-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="89c0f-107">\[in) identyfikator funkcji, do której jest przenoszona kontrola.</span><span class="sxs-lookup"><span data-stu-id="89c0f-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="89c0f-108">\[w] ponownie mapowany identyfikator funkcji, który został wcześniej określony przez profiler przy użyciu funkcji [FunctionIDMapper](functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="89c0f-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="89c0f-109">\[in) `COR_PRF_FRAME_INFO` wartość, która wskazuje na informacje o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="89c0f-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="89c0f-110">Profiler powinien być traktowany jako nieprzezroczysty uchwyt, który można przesłać z powrotem do aparatu wykonywania w metodzie [ICorProfilerInfo2:: GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89c0f-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="89c0f-111">\[w] wskaźnik do struktury [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) , która określa lokalizacje w pamięci argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="89c0f-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="89c0f-112">Aby można było uzyskać dostęp do informacji o argumencie, `COR_PRF_ENABLE_FUNCTION_ARGS` należy ustawić flagę.</span><span class="sxs-lookup"><span data-stu-id="89c0f-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="89c0f-113">Profiler może użyć metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="89c0f-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="89c0f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89c0f-114">Remarks</span></span>  
 <span data-ttu-id="89c0f-115">Wartości `func` `argumentInfo` parametrów i są nieprawidłowe po `FunctionEnter2` powrocie funkcji, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.</span><span class="sxs-lookup"><span data-stu-id="89c0f-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="89c0f-116">`FunctionEnter2`Funkcja jest wywołaniem zwrotnym, należy ją zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="89c0f-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="89c0f-117">Implementacja musi używać `__declspec` `naked` atrybutu klasy magazynu ().</span><span class="sxs-lookup"><span data-stu-id="89c0f-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="89c0f-118">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="89c0f-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="89c0f-119">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="89c0f-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="89c0f-120">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="89c0f-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="89c0f-121">Implementacja `FunctionEnter2` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="89c0f-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="89c0f-122">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="89c0f-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="89c0f-123">W przypadku próby wyrzucania elementów bezużytecznych środowisko uruchomieniowe zostanie zablokowane do momentu `FunctionEnter2` powracania.</span><span class="sxs-lookup"><span data-stu-id="89c0f-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="89c0f-124">Ponadto `FunctionEnter2` Funkcja nie może wywołać kodu zarządzanego lub w jakikolwiek sposób może spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="89c0f-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89c0f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89c0f-125">Requirements</span></span>  
 <span data-ttu-id="89c0f-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89c0f-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89c0f-127">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="89c0f-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="89c0f-128">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="89c0f-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89c0f-129">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89c0f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89c0f-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89c0f-130">See also</span></span>

- [<span data-ttu-id="89c0f-131">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="89c0f-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="89c0f-132">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="89c0f-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="89c0f-133">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="89c0f-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="89c0f-134">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="89c0f-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
