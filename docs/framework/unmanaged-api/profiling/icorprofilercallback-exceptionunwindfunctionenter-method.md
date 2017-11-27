---
title: "ICorProfilerCallback::ExceptionUnwindFunctionEnter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc41dc95776ca31178153402d2e145a3d2c13bf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="05cb1-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="05cb1-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="05cb1-103">Powiadamia profilera, że cofnąć funkcji rozpoczął fazy unwind dla obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="05cb1-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05cb1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05cb1-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05cb1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05cb1-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="05cb1-106">[in] Identyfikator funkcji, która jest trwa odwinięty.</span><span class="sxs-lookup"><span data-stu-id="05cb1-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05cb1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05cb1-107">Remarks</span></span>  
 <span data-ttu-id="05cb1-108">Profilera nie należy zablokować w jej implementacja tej metody, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="05cb1-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="05cb1-109">Jeśli profilera blokuje tutaj i nastąpiła wyrzucanie elementów bezużytecznych, środowisko uruchomieniowe zablokuje dopóki zwraca tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="05cb1-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="05cb1-110">Profiler implementacja tej metody nie powinny wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="05cb1-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05cb1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05cb1-111">Requirements</span></span>  
 <span data-ttu-id="05cb1-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05cb1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05cb1-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05cb1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05cb1-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05cb1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05cb1-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05cb1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05cb1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05cb1-116">See Also</span></span>  
 [<span data-ttu-id="05cb1-117">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="05cb1-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="05cb1-118">ExceptionUnwindFunctionLeave — metoda</span><span class="sxs-lookup"><span data-stu-id="05cb1-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
