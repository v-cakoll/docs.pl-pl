---
title: FunctionLeave3 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee72974d42842f63347c76586c4f1316f2a8f3a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683365"
---
# <a name="functionleave3-function"></a><span data-ttu-id="4deaf-102">FunctionLeave3 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4deaf-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="4deaf-103">Powiadamia program profilujący, że kontrolki zwracana przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="4deaf-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4deaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4deaf-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4deaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4deaf-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="4deaf-106">[in] Identyfikator funkcji, z którego zwróceniem sterowania.</span><span class="sxs-lookup"><span data-stu-id="4deaf-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4deaf-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4deaf-107">Remarks</span></span>  
 <span data-ttu-id="4deaf-108">`FunctionLeave3` Funkcji wywołania zwrotnego powiadamia program profilujący, funkcje wywoływane są, ale nie obsługuje inspekcji wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="4deaf-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="4deaf-109">Użyj [icorprofilerinfo3::setenterleavefunctionhooks3 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) zarejestrować implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="4deaf-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="4deaf-110">`FunctionLeave3` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="4deaf-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="4deaf-111">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="4deaf-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="4deaf-112">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="4deaf-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="4deaf-113">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="4deaf-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="4deaf-114">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4deaf-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="4deaf-115">Implementacja `FunctionLeave3` powinien blokuje, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4deaf-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="4deaf-116">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="4deaf-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="4deaf-117">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionLeave3` zwraca.</span><span class="sxs-lookup"><span data-stu-id="4deaf-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="4deaf-118">`FunctionLeave3` Funkcji nie może wywoływać kod zarządzany lub spowodować alokacji pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="4deaf-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4deaf-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4deaf-119">Requirements</span></span>  
 <span data-ttu-id="4deaf-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4deaf-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4deaf-121">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="4deaf-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4deaf-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4deaf-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4deaf-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4deaf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4deaf-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4deaf-124">See also</span></span>
- [<span data-ttu-id="4deaf-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="4deaf-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="4deaf-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="4deaf-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="4deaf-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4deaf-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="4deaf-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4deaf-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="4deaf-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4deaf-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="4deaf-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="4deaf-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="4deaf-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4deaf-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="4deaf-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="4deaf-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="4deaf-133">Setfunctionidmapper2 —</span><span class="sxs-lookup"><span data-stu-id="4deaf-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="4deaf-134">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="4deaf-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
