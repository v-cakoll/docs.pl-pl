---
title: FunctionEnter — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6018b5b06a138b38b7b97df280a3e4c4ea0512d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598964"
---
# <a name="functionenter-function"></a><span data-ttu-id="7db8d-102">FunctionEnter — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7db8d-102">FunctionEnter Function</span></span>
<span data-ttu-id="7db8d-103">Powiadamia program profilujący, że formant jest przekazywany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="7db8d-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7db8d-104">`FunctionEnter` Funkcja jest przestarzała w programie .NET Framework w wersji 2.0 i jego użycia spowoduje naliczenie opłaty za spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="7db8d-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="7db8d-105">Użyj [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zamiast tego funkcji.</span><span class="sxs-lookup"><span data-stu-id="7db8d-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7db8d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7db8d-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7db8d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7db8d-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="7db8d-108">[in] Identyfikator funkcji, do której kontrola jest przekazywana.</span><span class="sxs-lookup"><span data-stu-id="7db8d-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7db8d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7db8d-109">Remarks</span></span>  
 <span data-ttu-id="7db8d-110">`FunctionEnter` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="7db8d-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="7db8d-111">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="7db8d-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="7db8d-112">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7db8d-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="7db8d-113">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="7db8d-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="7db8d-114">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7db8d-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7db8d-115">Implementacja `FunctionEnter` nie powinny blokować, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7db8d-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="7db8d-116">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="7db8d-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7db8d-117">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionEnter` zwraca.</span><span class="sxs-lookup"><span data-stu-id="7db8d-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="7db8d-118">Ponadto `FunctionEnter` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="7db8d-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7db8d-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7db8d-119">Requirements</span></span>  
 <span data-ttu-id="7db8d-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7db8d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7db8d-121">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7db8d-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7db8d-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7db8d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7db8d-123">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="7db8d-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db8d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7db8d-124">See also</span></span>

- [<span data-ttu-id="7db8d-125">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="7db8d-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="7db8d-126">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="7db8d-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="7db8d-127">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="7db8d-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="7db8d-128">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="7db8d-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="7db8d-129">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="7db8d-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
