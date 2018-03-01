---
title: "ICorProfilerCallback::ExceptionUnwindFinallyEnter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3480761c2708fa2f15454a7a99c34e84ee34eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="a5a0c-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="a5a0c-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="a5a0c-103">Powiadamia profiler fazy unwind wyjątek wprowadzania Obsługa `finally` klauzuli zawartych w określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5a0c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5a0c-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5a0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5a0c-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a5a0c-106">[in] Funkcja, która zawiera identyfikator `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5a0c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5a0c-107">Remarks</span></span>  
 <span data-ttu-id="a5a0c-108">Profilera nie należy zablokować w jej implementacja tej metody, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="a5a0c-109">Jeśli profilera blokuje tutaj i nastąpiła wyrzucanie elementów bezużytecznych, środowisko uruchomieniowe zablokuje dopóki zwraca tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="a5a0c-110">Profiler implementacja tej metody nie powinny wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5a0c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5a0c-111">Requirements</span></span>  
 <span data-ttu-id="a5a0c-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5a0c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5a0c-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5a0c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5a0c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5a0c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5a0c-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5a0c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a0c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5a0c-116">See Also</span></span>  
 [<span data-ttu-id="a5a0c-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5a0c-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a5a0c-118">GetNotifiedExceptionClauseInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="a5a0c-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)  
 [<span data-ttu-id="a5a0c-119">ExceptionUnwindFinallyLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="a5a0c-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
