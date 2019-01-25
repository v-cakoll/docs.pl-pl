---
title: FunctionEnter3WithInfo — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35b77e282fd23ee01ea5e7d65bec64f8fb2ecc31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533104"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="04cf1-102">FunctionEnter3WithInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="04cf1-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="04cf1-103">Powiadamia program profilujący, że formant jest przekazywany do funkcji, a także uchwyt, który może być przekazywany do [icorprofilerinfo3::getfunctionenter3info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) można pobrać argumenty ramki i funkcję stosu.</span><span class="sxs-lookup"><span data-stu-id="04cf1-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04cf1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04cf1-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04cf1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04cf1-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="04cf1-106">[in] Identyfikator funkcji, do której kontrola jest przekazywana.</span><span class="sxs-lookup"><span data-stu-id="04cf1-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="04cf1-107">[in] Dojście nieprzezroczyste reprezentujący informacji na temat ramkę stosu w danym.</span><span class="sxs-lookup"><span data-stu-id="04cf1-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="04cf1-108">Tego dojścia jest prawidłowy tylko podczas wywołania zwrotnego, do którego jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="04cf1-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04cf1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04cf1-109">Remarks</span></span>  
 <span data-ttu-id="04cf1-110">`FunctionEnter3WithInfo` Metody wywołania zwrotnego powiadamia program profilujący, ponieważ funkcje są nazywane i włącza program profilujący do użycia [icorprofilerinfo3::getfunctionenter3info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) Aby sprawdzić wartości argumentu.</span><span class="sxs-lookup"><span data-stu-id="04cf1-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="04cf1-111">Dostęp do informacji argumentu `COR_PRF_ENABLE_FUNCTION_ARGS` flagi musi zostać ustawione.</span><span class="sxs-lookup"><span data-stu-id="04cf1-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="04cf1-112">Można użyć programu profilującego [icorprofilerinfo::seteventmask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) można ustawić flagi zdarzenia, a następnie użyj [icorprofilerinfo3::setenterleavefunctionhooks3withinfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) można zarejestrować usługi Implementacja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="04cf1-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="04cf1-113">`FunctionEnter3WithInfo` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="04cf1-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="04cf1-114">Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="04cf1-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="04cf1-115">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="04cf1-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="04cf1-116">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="04cf1-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="04cf1-117">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="04cf1-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="04cf1-118">Implementacja `FunctionEnter3WithInfo` powinien blokuje, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="04cf1-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="04cf1-119">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="04cf1-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="04cf1-120">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionEnter3WithInfo` zwraca.</span><span class="sxs-lookup"><span data-stu-id="04cf1-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="04cf1-121">`FunctionEnter3WithInfo` Funkcji nie może wywoływać kod zarządzany lub spowodować alokacji pamięci zarządzanej w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="04cf1-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04cf1-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04cf1-122">Requirements</span></span>  
 <span data-ttu-id="04cf1-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04cf1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04cf1-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="04cf1-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="04cf1-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04cf1-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04cf1-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04cf1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04cf1-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04cf1-127">See also</span></span>
- [<span data-ttu-id="04cf1-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="04cf1-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="04cf1-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="04cf1-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="04cf1-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="04cf1-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="04cf1-131">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="04cf1-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
