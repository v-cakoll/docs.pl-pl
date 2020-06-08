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
ms.openlocfilehash: 8734fa9c9418b818cbe14ebe87ce2af6fa59c078
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499847"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="89f80-102">ICorProfilerCallback::UnmanagedToManagedTransition — Metoda</span><span class="sxs-lookup"><span data-stu-id="89f80-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="89f80-103">Powiadamia profiler o wystąpieniu przejścia z niezarządzanego kodu do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="89f80-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89f80-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89f80-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89f80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89f80-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="89f80-106">podczas Identyfikator funkcji, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="89f80-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="89f80-107">podczas Wartość wyliczenia [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) , która wskazuje, czy przeprowadzono przejście do kodu zarządzanego z niezarządzanego kodu, czy z powodu powrotu z niezarządzanej funkcji wywołanej przez zarządzaną metodę.</span><span class="sxs-lookup"><span data-stu-id="89f80-107">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89f80-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89f80-108">Remarks</span></span>  
 <span data-ttu-id="89f80-109">Jeśli wartość `reason` jest COR_PRF_TRANSITION_RETURN i `functionId` nie ma wartości null, identyfikator funkcji jest niezarządzaną funkcją i nigdy nie zostanie skompilowany przy użyciu kompilatora just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="89f80-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="89f80-110">Funkcje niezarządzane mają skojarzone z nimi podstawowe informacje, takie jak nazwa i niektóre metadane.</span><span class="sxs-lookup"><span data-stu-id="89f80-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="89f80-111">Jeśli wartość `reason` jest COR_PRF_TRANSITION_CALL, istnieje możliwość, że wywołana funkcja (czyli funkcja zarządzana) nie została jeszcze skompilowana w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="89f80-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89f80-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89f80-112">Requirements</span></span>  
 <span data-ttu-id="89f80-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89f80-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89f80-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="89f80-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89f80-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="89f80-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89f80-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89f80-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f80-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89f80-117">See also</span></span>

- [<span data-ttu-id="89f80-118">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="89f80-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="89f80-119">ManagedToUnmanagedTransition, metoda</span><span class="sxs-lookup"><span data-stu-id="89f80-119">ManagedToUnmanagedTransition Method</span></span>](icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="89f80-120">Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)</span><span class="sxs-lookup"><span data-stu-id="89f80-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="89f80-121">Korzystanie z międzyoperacyjności języka C++ (niejawne PInvoke)</span><span class="sxs-lookup"><span data-stu-id="89f80-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
