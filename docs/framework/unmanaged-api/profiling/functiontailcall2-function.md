---
title: FunctionTailcall2 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175190"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="55e09-102">FunctionTailcall2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="55e09-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="55e09-103">Powiadamia profiler, że funkcja aktualnie wykonywania ma zamiar wykonać wywołanie ogona do innej funkcji i zawiera informacje o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="55e09-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e09-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55e09-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55e09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55e09-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="55e09-106">\[w] Identyfikator aktualnie wykonywanej funkcji, która ma na celu wywołanie ogona.</span><span class="sxs-lookup"><span data-stu-id="55e09-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="55e09-107">\[w] Reemapped identyfikator funkcji, który profiler wcześniej określone za pośrednictwem [FunctionIDMapper](functionidmapper-function.md), funkcji aktualnie wykonywania, który ma zamiar dokonać wywołania ogona.</span><span class="sxs-lookup"><span data-stu-id="55e09-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="55e09-108">\[w] `COR_PRF_FRAME_INFO` Wartość, która wskazuje informacje o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="55e09-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="55e09-109">Profiler należy traktować to jako nieprzezroczysty dojście, które mogą być przekazywane z powrotem do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="55e09-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="55e09-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55e09-110">Remarks</span></span>  
 <span data-ttu-id="55e09-111">Funkcja docelowa wywołania ogona użyje bieżącej ramki stosu i powróci bezpośrednio do obiektu wywołującego funkcji, która wykonała wywołanie ogona.</span><span class="sxs-lookup"><span data-stu-id="55e09-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="55e09-112">Oznacza to, że [FunctionLeave2](functionleave2-function.md) wywołania zwrotnego nie zostaną wystawione dla funkcji, która jest celem wywołania ogona.</span><span class="sxs-lookup"><span data-stu-id="55e09-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="55e09-113">Wartość parametru `func` nie jest prawidłowa po powrocie `FunctionTailcall2` funkcji, ponieważ wartość może ulec zmianie lub zostać zniszczona.</span><span class="sxs-lookup"><span data-stu-id="55e09-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="55e09-114">Funkcja `FunctionTailcall2` jest wywołaniem zwrotnym; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="55e09-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="55e09-115">Implementacja musi `__declspec`używać`naked`atrybutu () klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="55e09-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="55e09-116">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="55e09-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="55e09-117">Przy wprowadzaniu należy zapisać wszystkie używane rejestry, w tym rejestry w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="55e09-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="55e09-118">Po wyjściu należy przywrócić stosu przez popping off wszystkie parametry, które zostały wypchnięte przez jego wywołującego.</span><span class="sxs-lookup"><span data-stu-id="55e09-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="55e09-119">Implementacja `FunctionTailcall2` nie należy blokować, ponieważ opóźni wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="55e09-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="55e09-120">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznym dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="55e09-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="55e09-121">Jeśli zostanie podjęta próba wyrzucania elementów `FunctionTailcall2` bezużytecznych, środowisko uruchomieniowe zostanie zablokowane, dopóki nie zwróci.</span><span class="sxs-lookup"><span data-stu-id="55e09-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="55e09-122">Ponadto `FunctionTailcall2` funkcja nie może wywoływać kodu zarządzanego lub w jakikolwiek sposób powodować alokacji pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="55e09-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55e09-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55e09-123">Requirements</span></span>  
 <span data-ttu-id="55e09-124">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55e09-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55e09-125">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="55e09-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="55e09-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55e09-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55e09-127">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55e09-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e09-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55e09-128">See also</span></span>

- [<span data-ttu-id="55e09-129">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="55e09-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="55e09-130">FunctionLeave2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="55e09-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="55e09-131">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="55e09-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="55e09-132">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="55e09-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
