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
ms.openlocfilehash: e40687f7f843dc563801bb01b503d2ae94a094fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446013"
---
# <a name="functionleave2-function"></a><span data-ttu-id="330bc-102">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="330bc-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="330bc-103">Powiadamia program profilujący, że funkcja ma zwrócić do obiektu wywołującego i zawiera informacje na temat ramki stosu i wartości zwracanej przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="330bc-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="330bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="330bc-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="330bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="330bc-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="330bc-106">podczas Identyfikator zwracanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="330bc-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="330bc-107">podczas Identyfikator funkcji ponownie mapowanej, który Profiler wcześniej określono za pośrednictwem funkcji [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="330bc-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="330bc-108">podczas Wartość `COR_PRF_FRAME_INFO`, która wskazuje na informacje o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="330bc-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="330bc-109">Profiler powinien być traktowany jako nieprzezroczysty uchwyt, który można przesłać z powrotem do aparatu wykonywania w metodzie [ICorProfilerInfo2:: GetFunctionInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="330bc-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="330bc-110">podczas Wskaźnik do struktury [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) , która określa lokalizację pamięci wartości zwracanej przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="330bc-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="330bc-111">Aby można było uzyskać dostęp do informacji o wartości zwracanej, należy ustawić flagę `COR_PRF_ENABLE_FUNCTION_RETVAL`.</span><span class="sxs-lookup"><span data-stu-id="330bc-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="330bc-112">Profiler może użyć metody [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="330bc-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="330bc-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="330bc-113">Remarks</span></span>  
 <span data-ttu-id="330bc-114">Wartości parametrów `func` i `retvalRange` są nieprawidłowe po powrocie funkcji `FunctionLeave2`, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.</span><span class="sxs-lookup"><span data-stu-id="330bc-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="330bc-115">Funkcja `FunctionLeave2` jest wywołaniem zwrotnym; należy zaimplementować go.</span><span class="sxs-lookup"><span data-stu-id="330bc-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="330bc-116">Implementacja musi używać atrybutu klasy magazynu `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="330bc-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="330bc-117">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="330bc-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="330bc-118">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="330bc-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="330bc-119">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="330bc-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="330bc-120">Implementacja `FunctionLeave2` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="330bc-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="330bc-121">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="330bc-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="330bc-122">Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionLeave2` zwraca.</span><span class="sxs-lookup"><span data-stu-id="330bc-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="330bc-123">Ponadto funkcja `FunctionLeave2` nie może wywoływać w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="330bc-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="330bc-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="330bc-124">Requirements</span></span>  
 <span data-ttu-id="330bc-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="330bc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="330bc-126">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="330bc-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="330bc-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="330bc-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="330bc-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="330bc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330bc-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="330bc-129">See also</span></span>

- [<span data-ttu-id="330bc-130">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="330bc-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="330bc-131">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="330bc-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="330bc-132">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="330bc-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="330bc-133">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="330bc-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
