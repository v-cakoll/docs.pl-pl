---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ba62ab2c4df73b570fb1c76adaee44a2a2ce8c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117809"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="87e85-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="87e85-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="87e85-103">Powiadamia program profilujący, że fazy odwijanie wyjątków opuścił obsługi `finally` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="87e85-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e85-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87e85-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="87e85-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87e85-105">Remarks</span></span>  
 <span data-ttu-id="87e85-106">Program profilujący nie powinny blokować podczas tego wywołania, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="87e85-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="87e85-107">Jeśli próba zostanie podjęta te bloki profilera i wyrzucania elementów bezużytecznych, środowisko uruchomieniowe blokuje aż do momentu powrotu to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="87e85-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="87e85-108">Ponadto podczas tego wywołania, profiler nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="87e85-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e85-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87e85-109">Requirements</span></span>  
 <span data-ttu-id="87e85-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87e85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e85-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87e85-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87e85-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87e85-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="87e85-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="87e85-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="87e85-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87e85-114">See also</span></span>

- [<span data-ttu-id="87e85-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="87e85-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="87e85-116">ExceptionUnwindFinallyEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="87e85-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
