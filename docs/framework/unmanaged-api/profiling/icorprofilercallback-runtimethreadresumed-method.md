---
title: ICorProfilerCallback::RuntimeThreadResumed — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: 5a9ca2f4587c4881820e1aa3d4134f90ce47d557
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865899"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="83f4b-102">ICorProfilerCallback::RuntimeThreadResumed — Metoda</span><span class="sxs-lookup"><span data-stu-id="83f4b-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="83f4b-103">Powiadamia program profilujący, że określony wątek został wznowiony po jego wstrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="83f4b-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f4b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83f4b-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83f4b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83f4b-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="83f4b-106">podczas Identyfikator wątku, który został wznowiony.</span><span class="sxs-lookup"><span data-stu-id="83f4b-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83f4b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83f4b-107">Requirements</span></span>  
 <span data-ttu-id="83f4b-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83f4b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f4b-109">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="83f4b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83f4b-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="83f4b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83f4b-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83f4b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f4b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83f4b-112">See also</span></span>

- [<span data-ttu-id="83f4b-113">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="83f4b-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="83f4b-114">RuntimeThreadSuspended, metoda</span><span class="sxs-lookup"><span data-stu-id="83f4b-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
