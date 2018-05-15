---
title: ICorProfilerCallback::ThreadDestroyed — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4929d9aaf7de9af72ec5ba93f5d7e35c712ac6cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="d1202-102">ICorProfilerCallback::ThreadDestroyed — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1202-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="d1202-103">Powiadamia profilera wątek został zlikwidowany.</span><span class="sxs-lookup"><span data-stu-id="d1202-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1202-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1202-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1202-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1202-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d1202-106">[in] Identyfikator wątku, który został zlikwidowany.</span><span class="sxs-lookup"><span data-stu-id="d1202-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1202-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1202-107">Remarks</span></span>  
 <span data-ttu-id="d1202-108">`threadId` Wartość nie jest już prawidłowy w tym czasie tego wywołania.</span><span class="sxs-lookup"><span data-stu-id="d1202-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1202-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1202-109">Requirements</span></span>  
 <span data-ttu-id="d1202-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1202-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1202-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1202-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1202-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1202-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1202-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1202-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1202-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1202-114">See Also</span></span>  
 [<span data-ttu-id="d1202-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1202-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d1202-116">ThreadCreated, metoda</span><span class="sxs-lookup"><span data-stu-id="d1202-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
