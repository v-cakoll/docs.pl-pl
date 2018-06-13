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
ms.openlocfilehash: c6bd0c9796fa2c5d8eff8dfb9d3fa3f707ce4761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453248"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="d6d99-102">ICorProfilerCallback::UnmanagedToManagedTransition — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6d99-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="d6d99-103">Powiadamia profilera, że nastąpiło przejście z kodu niezarządzanego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d6d99-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6d99-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6d99-104">Syntax</span></span>  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6d99-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6d99-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d6d99-106">[in] Identyfikator funkcji, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d6d99-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="d6d99-107">[in] Wartość [cor_prf_transition_reason —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) wyliczenia, która wskazuje, czy przejście wystąpiły z powodu wywołania wewnątrz kodu zarządzanego kodu niezarządzanego lub ze względu na typ zwracany funkcji niezarządzanej wywoływane przez jednego zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d6d99-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6d99-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6d99-108">Remarks</span></span>  
 <span data-ttu-id="d6d99-109">Jeśli wartość `reason` jest COR_PRF_TRANSITION_RETURN i `functionId` jest nie null, funkcja identyfikator jest to, że niezarządzanej funkcji i zostanie nigdy nie zostały skompilowane przy użyciu kompilatora just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="d6d99-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="d6d99-110">Funkcje niezarządzane ma kilku podstawowych informacji związanych z nimi, takie jak nazwa i niektóre metadane.</span><span class="sxs-lookup"><span data-stu-id="d6d99-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="d6d99-111">Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, jest możliwe, że wywołanej funkcji (czyli funkcja zarządzanych) nie została jeszcze skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="d6d99-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6d99-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6d99-112">Requirements</span></span>  
 <span data-ttu-id="d6d99-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6d99-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6d99-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6d99-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6d99-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6d99-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6d99-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6d99-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d99-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6d99-117">See Also</span></span>  
 [<span data-ttu-id="d6d99-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6d99-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d6d99-119">ManagedToUnmanagedTransition, metoda</span><span class="sxs-lookup"><span data-stu-id="d6d99-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)  
 [<span data-ttu-id="d6d99-120">Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)</span><span class="sxs-lookup"><span data-stu-id="d6d99-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)  
 [<span data-ttu-id="d6d99-121">Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)</span><span class="sxs-lookup"><span data-stu-id="d6d99-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
