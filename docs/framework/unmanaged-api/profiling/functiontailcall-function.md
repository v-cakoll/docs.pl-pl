---
title: FunctionTailcall — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
ms.openlocfilehash: 42ea497bdcab71518bec08514b827d76f0317d57
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500601"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="1400a-102">FunctionTailcall — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1400a-102">FunctionTailcall Function</span></span>
<span data-ttu-id="1400a-103">Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji.</span><span class="sxs-lookup"><span data-stu-id="1400a-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1400a-104">`FunctionTailcall`Funkcja jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="1400a-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="1400a-105">Będzie ona nadal działała, ale nastąpi spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="1400a-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="1400a-106">Zamiast tego użyj funkcji [FunctionTailcall2](functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="1400a-106">Use the [FunctionTailcall2](functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1400a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1400a-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1400a-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1400a-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="1400a-109">\[in) identyfikator aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="1400a-109">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="1400a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1400a-110">Remarks</span></span>  
 <span data-ttu-id="1400a-111">Funkcja Target wywołania tail będzie używać bieżącej ramki stosu i zwróci się bezpośrednio do obiektu wywołującego funkcji, która wykonał wywołanie tail.</span><span class="sxs-lookup"><span data-stu-id="1400a-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="1400a-112">Oznacza to, że wywołanie zwrotne [FunctionLeave —](functionleave-function.md) nie zostanie wygenerowane dla funkcji, która jest elementem docelowym wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="1400a-112">This means that a [FunctionLeave](functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="1400a-113">`FunctionTailcall`Funkcja jest wywołaniem zwrotnym, należy ją zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="1400a-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="1400a-114">Implementacja musi używać `__declspec` `naked` atrybutu klasy magazynu ().</span><span class="sxs-lookup"><span data-stu-id="1400a-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="1400a-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="1400a-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="1400a-116">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="1400a-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="1400a-117">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="1400a-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="1400a-118">Implementacja `FunctionTailcall` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1400a-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="1400a-119">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1400a-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="1400a-120">W przypadku próby wyrzucania elementów bezużytecznych środowisko uruchomieniowe zostanie zablokowane do momentu `FunctionTailcall` powracania.</span><span class="sxs-lookup"><span data-stu-id="1400a-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="1400a-121">Ponadto `FunctionTailcall` Funkcja nie może wywołać kodu zarządzanego lub w jakikolwiek sposób może spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="1400a-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1400a-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1400a-122">Requirements</span></span>  
 <span data-ttu-id="1400a-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1400a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1400a-124">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="1400a-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1400a-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1400a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1400a-126">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="1400a-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1400a-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1400a-127">See also</span></span>

- [<span data-ttu-id="1400a-128">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="1400a-128">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="1400a-129">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1400a-129">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="1400a-130">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="1400a-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="1400a-131">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="1400a-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
