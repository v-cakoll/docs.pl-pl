---
title: ICorProfilerCallback::UnmanagedToManagedTransition — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 8c4e132b90fa1f51bc6f858d75c159af212ec019
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439893"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="c6ab9-102">ICorProfilerCallback::UnmanagedToManagedTransition — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6ab9-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="c6ab9-103">Powiadamia profiler o wystąpieniu przejścia z niezarządzanego kodu do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c6ab9-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ab9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6ab9-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6ab9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6ab9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c6ab9-106">podczas Identyfikator funkcji, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="c6ab9-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="c6ab9-107">podczas Wartość wyliczenia [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) , która wskazuje, czy przeprowadzono przejście do kodu zarządzanego z niezarządzanego kodu, czy z powodu powrotu z niezarządzanej funkcji wywołanej przez zarządzaną metodę.</span><span class="sxs-lookup"><span data-stu-id="c6ab9-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6ab9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6ab9-108">Remarks</span></span>  
 <span data-ttu-id="c6ab9-109">Jeśli wartość `reason` jest COR_PRF_TRANSITION_RETURN i `functionId` nie ma wartości null, identyfikator funkcji jest niezarządzaną funkcją i nigdy nie zostanie skompilowany przy użyciu kompilatora just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c6ab9-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="c6ab9-110">Funkcje niezarządzane mają skojarzone z nimi podstawowe informacje, takie jak nazwa i niektóre metadane.</span><span class="sxs-lookup"><span data-stu-id="c6ab9-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="c6ab9-111">Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, może być możliwe, że wywołana funkcja (czyli funkcja zarządzana) nie została jeszcze skompilowana w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="c6ab9-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ab9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6ab9-112">Requirements</span></span>  
 <span data-ttu-id="c6ab9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6ab9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ab9-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c6ab9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6ab9-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c6ab9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6ab9-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6ab9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ab9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6ab9-117">See also</span></span>

- [<span data-ttu-id="c6ab9-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6ab9-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c6ab9-119">ManagedToUnmanagedTransition, metoda</span><span class="sxs-lookup"><span data-stu-id="c6ab9-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="c6ab9-120">Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)</span><span class="sxs-lookup"><span data-stu-id="c6ab9-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="c6ab9-121">Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)</span><span class="sxs-lookup"><span data-stu-id="c6ab9-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
