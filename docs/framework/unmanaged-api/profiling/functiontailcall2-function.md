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
ms.openlocfilehash: db3c3d38e0200f9849c84d7605a436816d56b813
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427423"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="be14c-102">FunctionTailcall2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="be14c-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="be14c-103">Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji i zawiera informacje na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="be14c-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be14c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be14c-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be14c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be14c-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="be14c-106">podczas Identyfikator aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="be14c-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="be14c-107">podczas Identyfikator funkcji ponownie mapowanej, który Profiler wcześniej określił za pośrednictwem [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), obecnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="be14c-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="be14c-108">podczas Wartość `COR_PRF_FRAME_INFO`, która wskazuje na informacje o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="be14c-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="be14c-109">Profiler powinien być traktowany jako nieprzezroczysty uchwyt, który można przesłać z powrotem do aparatu wykonywania w metodzie [ICorProfilerInfo2:: GetFunctionInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="be14c-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be14c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be14c-110">Remarks</span></span>  
 <span data-ttu-id="be14c-111">Funkcja Target wywołania tail będzie używać bieżącej ramki stosu i zwróci się bezpośrednio do obiektu wywołującego funkcji, która wykonał wywołanie tail.</span><span class="sxs-lookup"><span data-stu-id="be14c-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="be14c-112">Oznacza to, że wywołanie zwrotne [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) nie zostanie wygenerowane dla funkcji, która jest elementem docelowym wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="be14c-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="be14c-113">Wartość parametru `func` jest nieprawidłowa po powrocie funkcji `FunctionTailcall2`, ponieważ wartość może ulec zmianie lub zostać zniszczona.</span><span class="sxs-lookup"><span data-stu-id="be14c-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="be14c-114">Funkcja `FunctionTailcall2` jest wywołaniem zwrotnym; należy zaimplementować go.</span><span class="sxs-lookup"><span data-stu-id="be14c-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="be14c-115">Implementacja musi używać atrybutu klasy magazynu `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="be14c-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="be14c-116">Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="be14c-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="be14c-117">We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).</span><span class="sxs-lookup"><span data-stu-id="be14c-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="be14c-118">Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="be14c-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="be14c-119">Implementacja `FunctionTailcall2` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="be14c-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="be14c-120">Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="be14c-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="be14c-121">Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionTailcall2` zwraca.</span><span class="sxs-lookup"><span data-stu-id="be14c-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="be14c-122">Ponadto funkcja `FunctionTailcall2` nie może wywoływać w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="be14c-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be14c-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be14c-123">Requirements</span></span>  
 <span data-ttu-id="be14c-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be14c-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be14c-125">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="be14c-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="be14c-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="be14c-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be14c-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be14c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be14c-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be14c-128">See also</span></span>

- [<span data-ttu-id="be14c-129">FunctionEnter2, funkcja</span><span class="sxs-lookup"><span data-stu-id="be14c-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="be14c-130">FunctionLeave2, funkcja</span><span class="sxs-lookup"><span data-stu-id="be14c-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="be14c-131">SetEnterLeaveFunctionHooks2, metoda</span><span class="sxs-lookup"><span data-stu-id="be14c-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="be14c-132">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="be14c-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
