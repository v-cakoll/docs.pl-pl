---
title: FunctionEnter2 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f01117d52ba49012120546db5095ccad8baa6e73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531626"
---
# <a name="functionenter2-function"></a><span data-ttu-id="589fe-102">FunctionEnter2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="589fe-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="589fe-103">Powiadamia program profilujący, że kontroli jest przekazywany do funkcji i zawiera informacje o stosie argumenty ramki i funkcji.</span><span class="sxs-lookup"><span data-stu-id="589fe-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="589fe-104">Ta funkcja zastępuje [functionenter —](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="589fe-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="589fe-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="589fe-105">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="589fe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="589fe-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="589fe-107">[in] Identyfikator funkcji, do której kontrola jest przekazywana.</span><span class="sxs-lookup"><span data-stu-id="589fe-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="589fe-108">[in] Identyfikator funkcji ponownie zmapowany, który program profilujący wcześniej określone za pomocą [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="589fe-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="589fe-109">[in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="589fe-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="589fe-110">Program profilujący powinien traktować to jako nieprzezroczysty uchwyt, który może być przekazywany do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="589fe-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="589fe-111">[in] Wskaźnik do [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) strukturę, która określa lokalizacje w pamięci w procentach argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="589fe-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="589fe-112">Aby uzyskać dostęp do informacji argumentu `COR_PRF_ENABLE_FUNCTION_ARGS` musi zostać ustawiona flaga.</span><span class="sxs-lookup"><span data-stu-id="589fe-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="589fe-113">Można użyć programu profilującego [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić flagi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="589fe-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="589fe-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="589fe-114">Remarks</span></span>  
 <span data-ttu-id="589fe-115">Wartości `func` i `argumentInfo` parametry nie są prawidłowe po `FunctionEnter2` funkcja zwraca wartości mogą ulec zmianie lub zostać zniszczone.</span><span class="sxs-lookup"><span data-stu-id="589fe-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="589fe-116">`FunctionEnter2` Funkcji jest wywołanie zwrotne; należy go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="589fe-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="589fe-117">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="589fe-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="589fe-118">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="589fe-118">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="589fe-119">Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="589fe-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="589fe-120">Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="589fe-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="589fe-121">Implementacja `FunctionEnter2` nie powinny blokować, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="589fe-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="589fe-122">Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="589fe-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="589fe-123">Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionEnter2` zwraca.</span><span class="sxs-lookup"><span data-stu-id="589fe-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="589fe-124">Ponadto `FunctionEnter2` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="589fe-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="589fe-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="589fe-125">Requirements</span></span>  
 <span data-ttu-id="589fe-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="589fe-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="589fe-127">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="589fe-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="589fe-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="589fe-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="589fe-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="589fe-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="589fe-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="589fe-130">See also</span></span>
- [<span data-ttu-id="589fe-131">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="589fe-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="589fe-132">FunctionTailcall2, funkcja</span><span class="sxs-lookup"><span data-stu-id="589fe-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="589fe-133">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="589fe-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="589fe-134">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="589fe-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
