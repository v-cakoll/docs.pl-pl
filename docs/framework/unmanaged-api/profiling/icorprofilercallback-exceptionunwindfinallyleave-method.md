---
title: "ICorProfilerCallback::ExceptionUnwindFinallyLeave — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf373872ada8364fe755162597dc9baf5c527f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="be2f7-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="be2f7-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="be2f7-103">Powiadamia profiler fazy unwind wyjątek opuścił Obsługa `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="be2f7-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be2f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be2f7-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="be2f7-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be2f7-105">Remarks</span></span>  
 <span data-ttu-id="be2f7-106">Profiler nie należy zablokować podczas tego wywołania, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="be2f7-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="be2f7-107">Bloki profilera w tym miejscu i wyrzucanie elementów bezużytecznych próbie środowiska uruchomieniowego zablokuje dopóki zwraca tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="be2f7-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="be2f7-108">Ponadto podczas tego wywołania profilera nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="be2f7-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be2f7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be2f7-109">Requirements</span></span>  
 <span data-ttu-id="be2f7-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be2f7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be2f7-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be2f7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be2f7-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be2f7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be2f7-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be2f7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2f7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be2f7-114">See Also</span></span>  
 [<span data-ttu-id="be2f7-115">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="be2f7-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="be2f7-116">ExceptionUnwindFinallyEnter — metoda</span><span class="sxs-lookup"><span data-stu-id="be2f7-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
