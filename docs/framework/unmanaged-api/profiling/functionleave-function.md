---
title: "FunctionLeave — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave
helpviewer_keywords: FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3368a97adf6ffceaa5ac56b7ffe16d6e2802437c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave-function"></a><span data-ttu-id="dffc4-102">FunctionLeave — Funkcja</span><span class="sxs-lookup"><span data-stu-id="dffc4-102">FunctionLeave Function</span></span>
<span data-ttu-id="dffc4-103">Powiadamia profilera funkcji o zbliżającym się zwrócić do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="dffc4-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dffc4-104">`FunctionLeave` Funkcja jest przestarzała w .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="dffc4-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="dffc4-105">Nadal będzie działać, ale będzie pociągnąć za sobą zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="dffc4-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="dffc4-106">Użyj [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zamiast tego działania.</span><span class="sxs-lookup"><span data-stu-id="dffc4-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dffc4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="dffc4-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dffc4-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="dffc4-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="dffc4-109">[in] Identyfikator funkcji, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="dffc4-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dffc4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dffc4-110">Remarks</span></span>  
 <span data-ttu-id="dffc4-111">`FunctionLeave` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="dffc4-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="dffc4-112">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="dffc4-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="dffc4-113">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="dffc4-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="dffc4-114">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="dffc4-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="dffc4-115">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="dffc4-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="dffc4-116">Implementacja `FunctionLeave` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dffc4-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="dffc4-117">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="dffc4-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="dffc4-118">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionLeave` zwraca.</span><span class="sxs-lookup"><span data-stu-id="dffc4-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="dffc4-119">Ponadto `FunctionLeave` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="dffc4-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dffc4-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dffc4-120">Requirements</span></span>  
 <span data-ttu-id="dffc4-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dffc4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dffc4-122">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="dffc4-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="dffc4-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dffc4-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dffc4-124">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="dffc4-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffc4-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dffc4-125">See Also</span></span>  
 [<span data-ttu-id="dffc4-126">Functionenter2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="dffc4-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="dffc4-127">Functionleave2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="dffc4-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="dffc4-128">Functiontailcall2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="dffc4-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="dffc4-129">SetEnterLeaveFunctionHooks2 — metoda</span><span class="sxs-lookup"><span data-stu-id="dffc4-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="dffc4-130">Statyczne funkcje globalne profilowania</span><span class="sxs-lookup"><span data-stu-id="dffc4-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
