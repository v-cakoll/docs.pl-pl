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
ms.openlocfilehash: 656f2498c7dd9ba165ab6759d8ca3b26e0d7c93f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207048"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="f4121-102">FunctionTailcall — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f4121-102">FunctionTailcall Function</span></span>
<span data-ttu-id="f4121-103">Powiadamia program profilujący, że aktualnie wykonywanej funkcji zostanie wykonywać wywołania tail do innej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4121-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4121-104">`FunctionTailcall` Funkcja jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="f4121-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f4121-105">Nadal będzie działać, ale spowoduje naliczenie opłaty za spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="f4121-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="f4121-106">Użyj [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zamiast tego funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4121-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4121-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4121-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4121-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4121-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="f4121-109">[in] Identyfikator aktualnie wykonywanej funkcji jest przeprowadzasz ogon wywołania.</span><span class="sxs-lookup"><span data-stu-id="f4121-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4121-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4121-110">Remarks</span></span>  
 <span data-ttu-id="f4121-111">Funkcja docelowy wywołania tail użyje bieżącej ramki stosu i zwróci bezpośrednio do obiektu wywołującego zgłaszający tail wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4121-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="f4121-112">Oznacza to, że [functionleave —](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) wywołanie zwrotne nie zostanie wystawiony dla funkcji, która jest elementem docelowym wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="f4121-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="f4121-113">`FunctionTailcall` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="f4121-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="f4121-114">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="f4121-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="f4121-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4121-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="f4121-116">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="f4121-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="f4121-117">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f4121-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f4121-118">Implementacja `FunctionTailcall` nie powinny blokować, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f4121-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="f4121-119">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="f4121-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f4121-120">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionTailcall` zwraca.</span><span class="sxs-lookup"><span data-stu-id="f4121-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="f4121-121">Ponadto `FunctionTailcall` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="f4121-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4121-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4121-122">Requirements</span></span>  
 <span data-ttu-id="f4121-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4121-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4121-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f4121-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f4121-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4121-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4121-126">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="f4121-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4121-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4121-127">See also</span></span>

- [<span data-ttu-id="f4121-128">FunctionEnter2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f4121-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="f4121-129">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f4121-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="f4121-130">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="f4121-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="f4121-131">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="f4121-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
