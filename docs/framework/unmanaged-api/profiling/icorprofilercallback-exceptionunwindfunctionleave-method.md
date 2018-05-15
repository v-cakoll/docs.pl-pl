---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a79a9c925392b0ab5e50269479b2f693f1a9b58d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="3048b-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="3048b-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="3048b-103">Powiadamia profilera fazy unwind dla obsługi wyjątków zakończenie rozwinięcia funkcji.</span><span class="sxs-lookup"><span data-stu-id="3048b-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3048b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3048b-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3048b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3048b-105">Remarks</span></span>  
 <span data-ttu-id="3048b-106">Gdy `ExceptionUnwindFunctionLeave` metoda jest wywoływana, wystąpienie funkcji i jej dane stosu są usuwane ze stosu.</span><span class="sxs-lookup"><span data-stu-id="3048b-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="3048b-107">Profiler nie należy zablokować podczas tego wywołania, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="3048b-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="3048b-108">Bloki profilera w tym miejscu i wyrzucanie elementów bezużytecznych próbie środowiska uruchomieniowego zablokuje dopóki zwraca tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3048b-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="3048b-109">Ponadto podczas tego wywołania profilera nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="3048b-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3048b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3048b-110">Requirements</span></span>  
 <span data-ttu-id="3048b-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3048b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3048b-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3048b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3048b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3048b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3048b-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3048b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3048b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3048b-115">See Also</span></span>  
 [<span data-ttu-id="3048b-116">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="3048b-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3048b-117">ExceptionUnwindFunctionEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="3048b-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
