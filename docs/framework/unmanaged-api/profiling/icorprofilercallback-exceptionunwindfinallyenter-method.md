---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caf546798f3928a2cf809bfec63c4b3cd959ee75
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466469"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="9844d-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="9844d-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="9844d-103">Powiadamia program profilujący, że fazy odwijanie wyjątków wprowadzenie obsługi `finally` klauzuli zawarte w określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9844d-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9844d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9844d-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9844d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9844d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9844d-106">[in] Identyfikator funkcji, która zawiera `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9844d-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9844d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9844d-107">Remarks</span></span>  
 <span data-ttu-id="9844d-108">Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9844d-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9844d-109">Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="9844d-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9844d-110">Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="9844d-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9844d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9844d-111">Requirements</span></span>  
 <span data-ttu-id="9844d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9844d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9844d-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9844d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9844d-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9844d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9844d-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9844d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9844d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9844d-116">See also</span></span>
- [<span data-ttu-id="9844d-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="9844d-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9844d-118">GetNotifiedExceptionClauseInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="9844d-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="9844d-119">ExceptionUnwindFinallyLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="9844d-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
