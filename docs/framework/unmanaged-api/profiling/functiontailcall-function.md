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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11cf96f5957d41e0647c309a7b0bb08fc9b31c91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="functiontailcall-function"></a><span data-ttu-id="81cf3-102">FunctionTailcall — Funkcja</span><span class="sxs-lookup"><span data-stu-id="81cf3-102">FunctionTailcall Function</span></span>
<span data-ttu-id="81cf3-103">Powiadamia profilera aktualnie wykonywane funkcja o zbliżającym się wykonywać wywołania tail na inną funkcję.</span><span class="sxs-lookup"><span data-stu-id="81cf3-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81cf3-104">`FunctionTailcall` Funkcja jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="81cf3-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="81cf3-105">Nadal będzie działać, ale będzie pociągnąć za sobą zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="81cf3-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="81cf3-106">Użyj [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zamiast tego działania.</span><span class="sxs-lookup"><span data-stu-id="81cf3-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81cf3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="81cf3-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81cf3-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="81cf3-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="81cf3-109">[in] Identyfikator aktualnie wykonywane funkcji, która wprowadzi tail wywołania.</span><span class="sxs-lookup"><span data-stu-id="81cf3-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81cf3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81cf3-110">Remarks</span></span>  
 <span data-ttu-id="81cf3-111">Funkcja docelowy wywołania tail użyje bieżącej ramki stosu i zwróci bezpośrednio do obiektu wywołującego zgłaszającego tail wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="81cf3-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="81cf3-112">Oznacza to, że [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) wywołania zwrotnego nie zostanie wystawiony dla funkcji, która jest elementem docelowym wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="81cf3-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="81cf3-113">`FunctionTailcall` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="81cf3-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="81cf3-114">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="81cf3-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="81cf3-115">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="81cf3-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="81cf3-116">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="81cf3-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="81cf3-117">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="81cf3-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="81cf3-118">Implementacja `FunctionTailcall` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="81cf3-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="81cf3-119">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="81cf3-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="81cf3-120">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionTailcall` zwraca.</span><span class="sxs-lookup"><span data-stu-id="81cf3-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="81cf3-121">Ponadto `FunctionTailcall` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="81cf3-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81cf3-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81cf3-122">Requirements</span></span>  
 <span data-ttu-id="81cf3-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81cf3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81cf3-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="81cf3-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="81cf3-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81cf3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81cf3-126">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="81cf3-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81cf3-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81cf3-127">See Also</span></span>  
 [<span data-ttu-id="81cf3-128">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="81cf3-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="81cf3-129">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="81cf3-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="81cf3-130">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="81cf3-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="81cf3-131">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="81cf3-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
