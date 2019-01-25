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
ms.openlocfilehash: b84b4b7ba96d39693abe238427983da086e62b1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634847"
---
# <a name="functionleave-function"></a><span data-ttu-id="784dd-102">FunctionLeave — Funkcja</span><span class="sxs-lookup"><span data-stu-id="784dd-102">FunctionLeave Function</span></span>
<span data-ttu-id="784dd-103">Powiadamia program profilujący, że funkcja jest około, aby powrócić do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="784dd-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="784dd-104">`FunctionLeave` Funkcja jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="784dd-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="784dd-105">Nadal będzie działać, ale spowoduje naliczenie opłaty za spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="784dd-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="784dd-106">Użyj [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zamiast tego funkcji.</span><span class="sxs-lookup"><span data-stu-id="784dd-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="784dd-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="784dd-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="784dd-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="784dd-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="784dd-109">[in] Identyfikator funkcji, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="784dd-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="784dd-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="784dd-110">Remarks</span></span>  
 <span data-ttu-id="784dd-111">`FunctionLeave` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="784dd-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="784dd-112">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="784dd-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="784dd-113">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="784dd-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="784dd-114">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="784dd-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="784dd-115">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="784dd-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="784dd-116">Implementacja `FunctionLeave` nie powinny blokować, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="784dd-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="784dd-117">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="784dd-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="784dd-118">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionLeave` zwraca.</span><span class="sxs-lookup"><span data-stu-id="784dd-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="784dd-119">Ponadto `FunctionLeave` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="784dd-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="784dd-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="784dd-120">Requirements</span></span>  
 <span data-ttu-id="784dd-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="784dd-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="784dd-122">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="784dd-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="784dd-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="784dd-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="784dd-124">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="784dd-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="784dd-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="784dd-125">See also</span></span>
- [<span data-ttu-id="784dd-126">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="784dd-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="784dd-127">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="784dd-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="784dd-128">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="784dd-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="784dd-129">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="784dd-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="784dd-130">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="784dd-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
