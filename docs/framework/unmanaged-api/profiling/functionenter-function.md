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
ms.openlocfilehash: caea1d3d526017c0118f95bb138ee4ac45d2c137
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866999"
---
# <a name="functionenter-function"></a><span data-ttu-id="0e086-102">FunctionEnter — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0e086-102">FunctionEnter Function</span></span>
<span data-ttu-id="0e086-103">Powiadamia profiler, że sterowanie jest przesyłane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="0e086-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e086-104">Funkcja `FunctionEnter` jest przestarzała w .NET Framework wersji 2,0, a jej użycie spowoduje spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="0e086-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="0e086-105">Zamiast tego użyj funkcji [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="0e086-105">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e086-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e086-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e086-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e086-107">Parameters</span></span>

- `funcID`

  <span data-ttu-id="0e086-108">\[in) identyfikator funkcji, do której jest przenoszona kontrola.</span><span class="sxs-lookup"><span data-stu-id="0e086-108">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e086-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e086-109">Remarks</span></span>  
 <span data-ttu-id="0e086-110">Funkcja `FunctionEnter` jest wywołaniem zwrotnym; należy zaimplementować go.</span><span class="sxs-lookup"><span data-stu-id="0e086-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="0e086-111">Implementacja musi używać atrybutu klasy magazynu `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="0e086-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="0e086-112">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0e086-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="0e086-113">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="0e086-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="0e086-114">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="0e086-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="0e086-115">Implementacja `FunctionEnter` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0e086-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="0e086-116">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0e086-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="0e086-117">Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionEnter` zwraca.</span><span class="sxs-lookup"><span data-stu-id="0e086-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="0e086-118">Ponadto funkcja `FunctionEnter` nie może wywoływać w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0e086-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e086-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e086-119">Requirements</span></span>  
 <span data-ttu-id="0e086-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e086-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e086-121">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="0e086-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0e086-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0e086-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e086-123">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="0e086-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e086-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e086-124">See also</span></span>

- [<span data-ttu-id="0e086-125">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="0e086-125">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="0e086-126">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="0e086-126">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="0e086-127">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="0e086-127">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="0e086-128">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="0e086-128">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="0e086-129">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="0e086-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
