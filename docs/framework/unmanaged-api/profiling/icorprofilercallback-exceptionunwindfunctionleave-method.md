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
ms.openlocfilehash: 305c8c7abf778ea68efe06f3bdb57af001ea1b9a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597353"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="e51ab-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave — Metoda</span><span class="sxs-lookup"><span data-stu-id="e51ab-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="e51ab-103">Powiadamia program profilujący fazy unwind dla obsługi wyjątków zakończenie rozwinięcia funkcji.</span><span class="sxs-lookup"><span data-stu-id="e51ab-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e51ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e51ab-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e51ab-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e51ab-105">Remarks</span></span>  
 <span data-ttu-id="e51ab-106">Gdy `ExceptionUnwindFunctionLeave` metoda jest wywoływana, wystąpienie funkcji i jej dane stosu są usuwane ze stosu.</span><span class="sxs-lookup"><span data-stu-id="e51ab-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="e51ab-107">Program profilujący nie powinny blokować podczas tego wywołania, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e51ab-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="e51ab-108">Jeśli próba zostanie podjęta te bloki profilera i wyrzucania elementów bezużytecznych, środowisko uruchomieniowe blokuje aż do momentu powrotu to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="e51ab-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="e51ab-109">Ponadto podczas tego wywołania, profiler nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="e51ab-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e51ab-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e51ab-110">Requirements</span></span>  
 <span data-ttu-id="e51ab-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e51ab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e51ab-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e51ab-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e51ab-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e51ab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e51ab-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e51ab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51ab-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e51ab-115">See also</span></span>

- [<span data-ttu-id="e51ab-116">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e51ab-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e51ab-117">ExceptionUnwindFunctionEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="e51ab-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
