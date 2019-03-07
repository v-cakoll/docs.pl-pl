---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86eec8b80631b7504daea30ad50a5c5e29f00893
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476246"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="65425-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="65425-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="65425-103">Powiadamia program profilujący, że na odpoczynek, funkcja rozpoczął fazy unwind dla obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="65425-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65425-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65425-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65425-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65425-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="65425-106">[in] Identyfikator funkcji, która jest on odwinięty.</span><span class="sxs-lookup"><span data-stu-id="65425-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65425-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65425-107">Remarks</span></span>  
 <span data-ttu-id="65425-108">Program profilujący nie powinna blokować w jego implementacja tej metody, ponieważ stos może nie być w stanie umożliwiającym wyrzucania elementów bezużytecznych, a w związku z tym nie można włączyć preemptive wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="65425-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="65425-109">Jeśli program profilujący blokuje tutaj i wyrzucania elementów bezużytecznych jest podejmowana próba, środowisko uruchomieniowe spowoduje zablokowanie, dopóki nie zwróci to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="65425-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="65425-110">Implementacja tej metody program profilujący nie powinien wywoływać wywołanie kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="65425-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65425-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65425-111">Requirements</span></span>  
 <span data-ttu-id="65425-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65425-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65425-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65425-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65425-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65425-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65425-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65425-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65425-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65425-116">See also</span></span>
- [<span data-ttu-id="65425-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="65425-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="65425-118">ExceptionUnwindFunctionLeave, metoda</span><span class="sxs-lookup"><span data-stu-id="65425-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
