---
title: FunctionTailcall2 — Funkcja
ms.date: 03/30/2017
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
ms.openlocfilehash: cb7e21e0c6aad5ebb328ae5d1a993716f96e8d47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500575"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="0df2a-102">FunctionTailcall2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0df2a-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="0df2a-103">Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji i zawiera informacje na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="0df2a-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0df2a-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0df2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0df2a-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="0df2a-106">\[in) identyfikator aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="0df2a-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="0df2a-107">\[w] identyfikator funkcji ponownie mapowanej, który został wcześniej określony przez program [FunctionIDMapper](functionidmapper-function.md), aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="0df2a-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="0df2a-108">\[in) `COR_PRF_FRAME_INFO` wartość, która wskazuje na informacje o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="0df2a-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="0df2a-109">Profiler powinien być traktowany jako nieprzezroczysty uchwyt, który można przesłać z powrotem do aparatu wykonywania w metodzie [ICorProfilerInfo2:: GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0df2a-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="0df2a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0df2a-110">Remarks</span></span>  
 <span data-ttu-id="0df2a-111">Funkcja Target wywołania tail będzie używać bieżącej ramki stosu i zwróci się bezpośrednio do obiektu wywołującego funkcji, która wykonał wywołanie tail.</span><span class="sxs-lookup"><span data-stu-id="0df2a-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="0df2a-112">Oznacza to, że wywołanie zwrotne [FunctionLeave2](functionleave2-function.md) nie zostanie wygenerowane dla funkcji, która jest elementem docelowym wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="0df2a-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="0df2a-113">Wartość `func` parametru jest nieprawidłowa po `FunctionTailcall2` powrocie funkcji, ponieważ wartość może ulec zmianie lub zostać zniszczona.</span><span class="sxs-lookup"><span data-stu-id="0df2a-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="0df2a-114">`FunctionTailcall2`Funkcja jest wywołaniem zwrotnym, należy ją zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="0df2a-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="0df2a-115">Implementacja musi używać `__declspec` `naked` atrybutu klasy magazynu ().</span><span class="sxs-lookup"><span data-stu-id="0df2a-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="0df2a-116">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0df2a-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="0df2a-117">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="0df2a-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="0df2a-118">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="0df2a-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="0df2a-119">Implementacja `FunctionTailcall2` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0df2a-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="0df2a-120">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0df2a-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="0df2a-121">W przypadku próby wyrzucania elementów bezużytecznych środowisko uruchomieniowe zostanie zablokowane do momentu `FunctionTailcall2` powracania.</span><span class="sxs-lookup"><span data-stu-id="0df2a-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="0df2a-122">Ponadto `FunctionTailcall2` Funkcja nie może wywołać kodu zarządzanego lub w jakikolwiek sposób może spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0df2a-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0df2a-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0df2a-123">Requirements</span></span>  
 <span data-ttu-id="0df2a-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0df2a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0df2a-125">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="0df2a-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0df2a-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0df2a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0df2a-127">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0df2a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df2a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0df2a-128">See also</span></span>

- [<span data-ttu-id="0df2a-129">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="0df2a-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="0df2a-130">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0df2a-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="0df2a-131">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="0df2a-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="0df2a-132">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="0df2a-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
