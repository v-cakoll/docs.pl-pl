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
ms.openlocfilehash: 9b53030fe860e02b0afd0dce3055ac3cf29e3491
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500003"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="6c34f-102">ICorProfilerCallback::ManagedToUnmanagedTransition — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c34f-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="6c34f-103">Powiadamia profiler o wystąpieniu przejścia z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6c34f-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c34f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c34f-104">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c34f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c34f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6c34f-106">podczas Identyfikator funkcji, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="6c34f-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="6c34f-107">podczas Wartość wyliczenia [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) , która wskazuje, czy przejście wystąpiło z powodu wywołania do niezarządzanego kodu z kodu zarządzanego lub z powodu powrotu z funkcji zarządzanej wywołanej przez niezarządzaną metodę.</span><span class="sxs-lookup"><span data-stu-id="6c34f-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c34f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c34f-108">Remarks</span></span>  
 <span data-ttu-id="6c34f-109">Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, identyfikator funkcji jest niezarządzana funkcja, która nigdy nie zostanie skompilowana przy użyciu kompilatora just in Time.</span><span class="sxs-lookup"><span data-stu-id="6c34f-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="6c34f-110">Z niezarządzanymi funkcjami są skojarzone podstawowe informacje, takie jak nazwa i niektóre metadane.</span><span class="sxs-lookup"><span data-stu-id="6c34f-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="6c34f-111">Jeśli funkcja niezarządzana została wywołana przy użyciu niejawnego wywołania platformy (PInvoke), środowisko uruchomieniowe nie może ustalić miejsca docelowego wywołania, a wartość `functionId` będzie równa null.</span><span class="sxs-lookup"><span data-stu-id="6c34f-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="6c34f-112">Aby uzyskać więcej informacji na temat niejawnego elementu PInvoke, zobacz [using C++ Interop (niejawne PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="6c34f-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c34f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c34f-113">Requirements</span></span>  
 <span data-ttu-id="6c34f-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c34f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c34f-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6c34f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c34f-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6c34f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c34f-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c34f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c34f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c34f-118">See also</span></span>

- [<span data-ttu-id="6c34f-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6c34f-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6c34f-120">UnmanagedToManagedTransition, metoda</span><span class="sxs-lookup"><span data-stu-id="6c34f-120">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="6c34f-121">Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)</span><span class="sxs-lookup"><span data-stu-id="6c34f-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
