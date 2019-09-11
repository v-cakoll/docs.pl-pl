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
ms.openlocfilehash: 12ec27277fe57bd1a291c2cfe491ea2c6f40c30e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851161"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="c154f-102">FunctionTailcall — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c154f-102">FunctionTailcall Function</span></span>
<span data-ttu-id="c154f-103">Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c154f-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c154f-104">`FunctionTailcall` Funkcja jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="c154f-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c154f-105">Będzie ona nadal działała, ale nastąpi spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="c154f-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="c154f-106">Zamiast tego użyj funkcji [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c154f-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c154f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c154f-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c154f-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="c154f-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="c154f-109">podczas Identyfikator aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="c154f-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c154f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c154f-110">Remarks</span></span>  
 <span data-ttu-id="c154f-111">Funkcja Target wywołania tail będzie używać bieżącej ramki stosu i zwróci się bezpośrednio do obiektu wywołującego funkcji, która wykonał wywołanie tail.</span><span class="sxs-lookup"><span data-stu-id="c154f-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="c154f-112">Oznacza to, że wywołanie zwrotne [FunctionLeave —](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) nie zostanie wygenerowane dla funkcji, która jest elementem docelowym wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="c154f-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="c154f-113">`FunctionTailcall` Funkcja jest wywołaniem zwrotnym, należy ją zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="c154f-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="c154f-114">Implementacja musi używać `__declspec`atrybutu klasy magazynu`naked`().</span><span class="sxs-lookup"><span data-stu-id="c154f-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="c154f-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c154f-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c154f-116">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="c154f-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c154f-117">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="c154f-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c154f-118">Implementacja `FunctionTailcall` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c154f-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="c154f-119">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c154f-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c154f-120">W przypadku próby wyrzucania elementów bezużytecznych środowisko uruchomieniowe `FunctionTailcall` zostanie zablokowane do momentu powracania.</span><span class="sxs-lookup"><span data-stu-id="c154f-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="c154f-121">`FunctionTailcall` Ponadto funkcja nie może wywołać kodu zarządzanego lub w jakikolwiek sposób może spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="c154f-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c154f-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c154f-122">Requirements</span></span>  
 <span data-ttu-id="c154f-123">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c154f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c154f-124">**Nagłówki** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="c154f-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c154f-125">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c154f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c154f-126">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="c154f-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c154f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c154f-127">See also</span></span>

- [<span data-ttu-id="c154f-128">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="c154f-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="c154f-129">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="c154f-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="c154f-130">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="c154f-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="c154f-131">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="c154f-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
