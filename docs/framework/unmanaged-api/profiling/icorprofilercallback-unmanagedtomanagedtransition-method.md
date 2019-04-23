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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 312f133c263becfd815f1b4ad48dff4892963aaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227854"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="ea8d6-102">ICorProfilerCallback::UnmanagedToManagedTransition — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea8d6-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="ea8d6-103">Powiadamia program profilujący, że nastąpiło przejście z niezarządzanego kodu do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea8d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea8d6-104">Syntax</span></span>  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea8d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea8d6-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ea8d6-106">[in] Identyfikator funkcji, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="ea8d6-107">[in] Wartość [cor_prf_transition_reason —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) wyliczenia, która wskazuje, czy przejście wystąpiły z powodu wywołanie kodu zarządzanego z niezarządzanego kodu lub ze względu na powrót z funkcji niezarządzanej wywoływana przez zarządzane.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea8d6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea8d6-108">Remarks</span></span>  
 <span data-ttu-id="ea8d6-109">Jeśli wartość `reason` jest COR_PRF_TRANSITION_RETURN i `functionId` jest nie jest to null, funkcja identyfikator jest to, że funkcji niezarządzanych i będzie nigdy nie zostały skompilowane przy użyciu kompilatora just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="ea8d6-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="ea8d6-110">Niezarządzane funkcje ma niektórych podstawowych informacji z nimi związane, takie jak nazwa i niektóre metadane.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="ea8d6-111">Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, jest możliwe, że funkcja o nazwie (czyli funkcji zarządzanej) nie została jeszcze kompilowany dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea8d6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea8d6-112">Requirements</span></span>  
 <span data-ttu-id="ea8d6-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea8d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea8d6-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea8d6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea8d6-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea8d6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea8d6-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea8d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea8d6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea8d6-117">See also</span></span>

- [<span data-ttu-id="ea8d6-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea8d6-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ea8d6-119">ManagedToUnmanagedTransition, metoda</span><span class="sxs-lookup"><span data-stu-id="ea8d6-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="ea8d6-120">Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)</span><span class="sxs-lookup"><span data-stu-id="ea8d6-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="ea8d6-121">Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)</span><span class="sxs-lookup"><span data-stu-id="ea8d6-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
