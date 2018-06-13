---
title: FunctionLeave — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2614ad988496a22f0e6234c2f3300e22ef548308
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452445"
---
# <a name="functionleave-function"></a><span data-ttu-id="b6172-102">FunctionLeave — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b6172-102">FunctionLeave Function</span></span>
<span data-ttu-id="b6172-103">Powiadamia profilera funkcji o zbliżającym się zwrócić do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b6172-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6172-104">`FunctionLeave` Funkcja jest przestarzała w .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="b6172-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="b6172-105">Nadal będzie działać, ale będzie pociągnąć za sobą zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="b6172-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="b6172-106">Użyj [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zamiast tego działania.</span><span class="sxs-lookup"><span data-stu-id="b6172-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6172-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6172-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6172-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6172-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="b6172-109">[in] Identyfikator funkcji, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="b6172-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6172-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6172-110">Remarks</span></span>  
 <span data-ttu-id="b6172-111">`FunctionLeave` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="b6172-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="b6172-112">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="b6172-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="b6172-113">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b6172-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="b6172-114">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="b6172-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="b6172-115">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b6172-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b6172-116">Implementacja `FunctionLeave` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b6172-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="b6172-117">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="b6172-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b6172-118">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionLeave` zwraca.</span><span class="sxs-lookup"><span data-stu-id="b6172-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="b6172-119">Ponadto `FunctionLeave` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="b6172-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6172-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6172-120">Requirements</span></span>  
 <span data-ttu-id="b6172-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6172-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6172-122">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b6172-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b6172-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6172-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6172-124">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="b6172-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6172-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6172-125">See Also</span></span>  
 [<span data-ttu-id="b6172-126">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="b6172-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="b6172-127">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="b6172-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="b6172-128">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="b6172-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="b6172-129">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="b6172-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="b6172-130">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="b6172-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
