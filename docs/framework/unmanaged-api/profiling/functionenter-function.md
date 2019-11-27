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
ms.openlocfilehash: ad34592223433f0bf541c390674bcf96839b6ca8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440816"
---
# <a name="functionenter-function"></a><span data-ttu-id="73686-102">FunctionEnter — Funkcja</span><span class="sxs-lookup"><span data-stu-id="73686-102">FunctionEnter Function</span></span>
<span data-ttu-id="73686-103">Powiadamia profiler, że sterowanie jest przesyłane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="73686-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73686-104">Funkcja `FunctionEnter` jest przestarzała w .NET Framework wersji 2,0, a jej użycie spowoduje spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="73686-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="73686-105">Zamiast tego użyj funkcji [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="73686-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73686-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="73686-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73686-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="73686-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="73686-108">podczas Identyfikator funkcji, do której jest przenoszona kontrola.</span><span class="sxs-lookup"><span data-stu-id="73686-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73686-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73686-109">Remarks</span></span>  
 <span data-ttu-id="73686-110">Funkcja `FunctionEnter` jest wywołaniem zwrotnym; należy zaimplementować go.</span><span class="sxs-lookup"><span data-stu-id="73686-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="73686-111">Implementacja musi używać atrybutu klasy magazynu `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="73686-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="73686-112">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="73686-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="73686-113">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="73686-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="73686-114">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="73686-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="73686-115">Implementacja `FunctionEnter` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="73686-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="73686-116">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="73686-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="73686-117">Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionEnter` zwraca.</span><span class="sxs-lookup"><span data-stu-id="73686-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="73686-118">Ponadto funkcja `FunctionEnter` nie może wywoływać w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="73686-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73686-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73686-119">Requirements</span></span>  
 <span data-ttu-id="73686-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73686-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73686-121">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="73686-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="73686-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73686-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73686-123">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="73686-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73686-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73686-124">See also</span></span>

- [<span data-ttu-id="73686-125">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="73686-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="73686-126">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="73686-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="73686-127">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="73686-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="73686-128">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="73686-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="73686-129">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="73686-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
