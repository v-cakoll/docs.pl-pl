---
title: FunctionTailcall3WithInfo — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cd301ac9d82dd49fc9680d2724714f267ed88ae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763284"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="bec9e-102">FunctionTailcall3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="bec9e-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="bec9e-103">Powiadamia program profilujący, które ma wykonywać wywołania tail do innej funkcji aktualnie wykonywanej funkcji i zapewnia uchwyt, który może być przekazywany do [icorprofilerinfo3::getfunctiontailcall3info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) do pobrania ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="bec9e-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bec9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bec9e-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bec9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bec9e-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="bec9e-106">[in] Identyfikator aktualnie wykonywanej funkcji jest przeprowadzasz ogon wywołania.</span><span class="sxs-lookup"><span data-stu-id="bec9e-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="bec9e-107">[in] Dojście nieprzezroczyste reprezentujący informacji na temat ramkę stosu w danym.</span><span class="sxs-lookup"><span data-stu-id="bec9e-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="bec9e-108">Tego dojścia jest prawidłowy tylko podczas wywołania zwrotnego, do którego jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="bec9e-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bec9e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bec9e-109">Remarks</span></span>  
 <span data-ttu-id="bec9e-110">`FunctionTailcall3WithInfo` Metody wywołania zwrotnego powiadamia program profilujący, funkcje są nazywane i pozwala profiler użyć [icorprofilerinfo3::getfunctiontailcall3info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) Aby sprawdzić ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="bec9e-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="bec9e-111">Dostęp do informacji ramki stosu, `COR_PRF_ENABLE_FRAME_INFO` flagi musi zostać ustawione.</span><span class="sxs-lookup"><span data-stu-id="bec9e-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="bec9e-112">Można użyć programu profilującego [icorprofilerinfo::seteventmask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) można ustawić flagi zdarzenia, a następnie użyj [icorprofilerinfo3::setenterleavefunctionhooks3withinfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) można zarejestrować usługi Implementacja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="bec9e-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="bec9e-113">`FunctionTailcall3WithInfo` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="bec9e-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="bec9e-114">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="bec9e-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="bec9e-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="bec9e-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="bec9e-116">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="bec9e-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="bec9e-117">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="bec9e-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="bec9e-118">Implementacja `FunctionTailcall3WithInfo` powinien blokuje, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bec9e-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="bec9e-119">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="bec9e-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="bec9e-120">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionTailcall3WithInfo` zwraca.</span><span class="sxs-lookup"><span data-stu-id="bec9e-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="bec9e-121">Functiontailcall3withinfo — funkcja nie musi ponadto mogą wywoływać kodu zarządzanego lub spowodować alokacji pamięci zarządzanej w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="bec9e-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bec9e-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bec9e-122">Requirements</span></span>  
 <span data-ttu-id="bec9e-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bec9e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bec9e-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="bec9e-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bec9e-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bec9e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bec9e-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bec9e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec9e-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bec9e-127">See also</span></span>

- [<span data-ttu-id="bec9e-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="bec9e-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="bec9e-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="bec9e-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="bec9e-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="bec9e-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="bec9e-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bec9e-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="bec9e-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bec9e-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="bec9e-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="bec9e-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="bec9e-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bec9e-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="bec9e-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="bec9e-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="bec9e-136">Setfunctionidmapper2 —</span><span class="sxs-lookup"><span data-stu-id="bec9e-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="bec9e-137">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="bec9e-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
