---
title: ICorProfilerCallback::ManagedToUnmanagedTransition — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b00394d0b08e7e4a02b95437908dd65a51d0a042
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084612"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="e418e-102">ICorProfilerCallback::ManagedToUnmanagedTransition — Metoda</span><span class="sxs-lookup"><span data-stu-id="e418e-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="e418e-103">Powiadamia program profilujący, że nastąpiło przejście z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e418e-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e418e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e418e-104">Syntax</span></span>  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e418e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e418e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e418e-106">[in] Identyfikator funkcji, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="e418e-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="e418e-107">[in] Wartość [cor_prf_transition_reason —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) wyliczenia, która wskazuje, czy przejście wystąpiły z powodu wywołania kodu niezarządzanego z kodu zarządzanego lub ze względu na powrót z funkcji zarządzanej wywoływane przez jeden z niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e418e-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e418e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e418e-108">Remarks</span></span>  
 <span data-ttu-id="e418e-109">Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, funkcja identyfikator to, że funkcji niezarządzanych, który będzie nigdy nie zostały skompilowane przy użyciu kompilatora just-in-time.</span><span class="sxs-lookup"><span data-stu-id="e418e-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="e418e-110">Funkcje niezarządzane mają podstawowe informacje z nimi związane, takie jak nazwa i niektóre metadane.</span><span class="sxs-lookup"><span data-stu-id="e418e-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="e418e-111">Jeśli niezarządzane funkcja została wywołana przy użyciu platformy niejawne wywołania (funkcja PInvoke), środowisko uruchomieniowe nie może określić docelową wywołania i wartości `functionId` będzie miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="e418e-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="e418e-112">Aby uzyskać więcej informacji na temat niejawna funkcja PInvoke, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="e418e-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e418e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e418e-113">Requirements</span></span>  
 <span data-ttu-id="e418e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e418e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e418e-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e418e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e418e-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e418e-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e418e-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e418e-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e418e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e418e-118">See also</span></span>

- [<span data-ttu-id="e418e-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e418e-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e418e-120">UnmanagedToManagedTransition, metoda</span><span class="sxs-lookup"><span data-stu-id="e418e-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="e418e-121">Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)</span><span class="sxs-lookup"><span data-stu-id="e418e-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
