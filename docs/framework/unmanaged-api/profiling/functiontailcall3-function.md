---
title: FunctionTailcall3 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 636ff5613b2681a73986cc5bfe9a28954f014588
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155483"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="df666-102">FunctionTailcall3 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="df666-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="df666-103">Powiadamia program profilujący, że aktualnie wykonywanej funkcji zostanie wykonywać wywołania tail do innej funkcji.</span><span class="sxs-lookup"><span data-stu-id="df666-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df666-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df666-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df666-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df666-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="df666-106">[in] Identyfikator aktualnie wykonywanej funkcji jest przeprowadzasz ogon wywołania.</span><span class="sxs-lookup"><span data-stu-id="df666-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df666-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df666-107">Remarks</span></span>  
 <span data-ttu-id="df666-108">`FunctionTailcall3` Funkcji wywołania zwrotnego powiadamia program profilujący, ponieważ wywoływane są funkcje.</span><span class="sxs-lookup"><span data-stu-id="df666-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="df666-109">Użyj [icorprofilerinfo3::setenterleavefunctionhooks3 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) zarejestrować implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="df666-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="df666-110">`FunctionTailcall3` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="df666-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="df666-111">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="df666-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="df666-112">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="df666-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="df666-113">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="df666-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="df666-114">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="df666-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="df666-115">Implementacja `FunctionTailcall3` powinien blokuje, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="df666-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="df666-116">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="df666-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="df666-117">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionTailcall3` zwraca.</span><span class="sxs-lookup"><span data-stu-id="df666-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="df666-118">`FunctionTailcall3` Funkcji nie może wywoływać kod zarządzany lub spowodować alokacji pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="df666-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df666-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df666-119">Requirements</span></span>  
 <span data-ttu-id="df666-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df666-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df666-121">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="df666-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="df666-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df666-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="df666-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="df666-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="df666-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df666-124">See also</span></span>

- [<span data-ttu-id="df666-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="df666-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="df666-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="df666-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="df666-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="df666-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="df666-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="df666-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="df666-129">FunctionTailcall3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="df666-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="df666-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="df666-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="df666-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="df666-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="df666-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="df666-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="df666-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="df666-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="df666-134">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="df666-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
