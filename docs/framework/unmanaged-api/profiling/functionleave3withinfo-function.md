---
title: FunctionLeave3WithInfo — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4304c933b9802ef565b8d18f1e04591e7fa83cb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598821"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="65584-102">FunctionLeave3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="65584-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="65584-103">Powiadamia program profilujący, że kontrolki zwracana przez funkcję, a także uchwyt, który może być przekazywany do [icorprofilerinfo3::getfunctionleave3info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pobieranie ramki stosu i wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="65584-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65584-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65584-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65584-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65584-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="65584-106">[in] Identyfikator funkcji, z którego zwróceniem sterowania.</span><span class="sxs-lookup"><span data-stu-id="65584-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="65584-107">[in] Dojście nieprzezroczyste reprezentujący informacji na temat ramkę stosu w danym.</span><span class="sxs-lookup"><span data-stu-id="65584-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="65584-108">Tego dojścia jest prawidłowy tylko podczas wywołania zwrotnego, do którego jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="65584-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65584-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65584-109">Remarks</span></span>  
 <span data-ttu-id="65584-110">`FunctionLeave3WithInfo` Metody wywołania zwrotnego powiadamia program profilujący, funkcje są nazywane i pozwala profiler użyć [icorprofilerinfo3::getfunctionleave3info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) Aby sprawdzić wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="65584-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="65584-111">Dostęp do informacji o wartości zwracanej, `COR_PRF_ENABLE_FUNCTION_RETVAL` flagi musi zostać ustawione.</span><span class="sxs-lookup"><span data-stu-id="65584-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="65584-112">Można użyć programu profilującego [icorprofilerinfo::seteventmask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) można ustawić flagi zdarzenia, a następnie użyj [icorprofilerinfo3::setenterleavefunctionhooks3withinfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) można zarejestrować usługi Implementacja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="65584-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="65584-113">`FunctionLeave3WithInfo` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="65584-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="65584-114">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="65584-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="65584-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="65584-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="65584-116">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="65584-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="65584-117">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="65584-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="65584-118">Implementacja `FunctionLeave3WithInfo` powinien blokuje, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="65584-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="65584-119">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="65584-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="65584-120">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionLeave3WithInfo` zwraca.</span><span class="sxs-lookup"><span data-stu-id="65584-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="65584-121">`FunctionLeave3WithInfo` Funkcji nie może wywoływać kod zarządzany lub spowodować alokacji pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="65584-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65584-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65584-122">Requirements</span></span>  
 <span data-ttu-id="65584-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65584-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65584-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="65584-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="65584-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65584-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65584-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65584-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65584-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65584-127">See also</span></span>

- [<span data-ttu-id="65584-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="65584-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="65584-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="65584-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="65584-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="65584-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="65584-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="65584-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="65584-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="65584-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="65584-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="65584-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="65584-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="65584-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="65584-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="65584-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="65584-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="65584-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="65584-137">Setfunctionidmapper2 —</span><span class="sxs-lookup"><span data-stu-id="65584-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="65584-138">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="65584-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
