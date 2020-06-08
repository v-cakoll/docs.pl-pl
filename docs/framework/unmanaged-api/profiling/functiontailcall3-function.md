---
title: FunctionTailcall3 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
ms.openlocfilehash: 55955cd47bd32fb4294b0b8e852dd692702bd74f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500549"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="2e1cd-102">FunctionTailcall3 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2e1cd-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="2e1cd-103">Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e1cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e1cd-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e1cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e1cd-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="2e1cd-106">\[in) identyfikator aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e1cd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e1cd-107">Remarks</span></span>  
 <span data-ttu-id="2e1cd-108">`FunctionTailcall3`Funkcja wywołania zwrotnego powiadamia profiler w miarę wywoływania funkcji.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="2e1cd-109">Użyj [metody ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 —](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) , aby zarejestrować implementację tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="2e1cd-110">`FunctionTailcall3`Funkcja jest wywołaniem zwrotnym, należy ją zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="2e1cd-111">Implementacja musi używać `__declspec(naked)` atrybutu klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="2e1cd-112">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="2e1cd-113">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="2e1cd-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="2e1cd-114">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="2e1cd-115">Implementacja `FunctionTailcall3` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="2e1cd-116">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="2e1cd-117">W przypadku próby wyrzucania elementów bezużytecznych środowisko uruchomieniowe zostanie zablokowane do momentu `FunctionTailcall3` powracania.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="2e1cd-118">`FunctionTailcall3`Funkcja nie może wywołać kodu zarządzanego lub spowodować alokacji pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="2e1cd-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e1cd-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e1cd-119">Requirements</span></span>  
 <span data-ttu-id="2e1cd-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e1cd-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e1cd-121">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="2e1cd-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2e1cd-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2e1cd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e1cd-123">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e1cd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e1cd-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e1cd-124">See also</span></span>

- [<span data-ttu-id="2e1cd-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="2e1cd-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="2e1cd-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="2e1cd-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="2e1cd-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="2e1cd-127">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="2e1cd-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="2e1cd-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="2e1cd-129">FunctionTailcall3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2e1cd-129">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="2e1cd-130">Setenterleavefunctionhooks3 —</span><span class="sxs-lookup"><span data-stu-id="2e1cd-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="2e1cd-131">Setenterleavefunctionhooks3withinfo —</span><span class="sxs-lookup"><span data-stu-id="2e1cd-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="2e1cd-132">SetFunctionIDMapper —</span><span class="sxs-lookup"><span data-stu-id="2e1cd-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="2e1cd-133">Setfunctionidmapper2 —</span><span class="sxs-lookup"><span data-stu-id="2e1cd-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="2e1cd-134">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="2e1cd-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
