---
title: "ICorProfilerCallback::ThreadDestroyed — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadDestroyed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 419a8a0797761429f41f7472d812aaebdbbf706c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="e9169-102">ICorProfilerCallback::ThreadDestroyed — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9169-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="e9169-103">Powiadamia profilera wątek został zlikwidowany.</span><span class="sxs-lookup"><span data-stu-id="e9169-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9169-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9169-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9169-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9169-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="e9169-106">[in] Identyfikator wątku, który został zlikwidowany.</span><span class="sxs-lookup"><span data-stu-id="e9169-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9169-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9169-107">Remarks</span></span>  
 <span data-ttu-id="e9169-108">`threadId` Wartość nie jest już prawidłowy w tym czasie tego wywołania.</span><span class="sxs-lookup"><span data-stu-id="e9169-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9169-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9169-109">Requirements</span></span>  
 <span data-ttu-id="e9169-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9169-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9169-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9169-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9169-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9169-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9169-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9169-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9169-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9169-114">See Also</span></span>  
 [<span data-ttu-id="e9169-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9169-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e9169-116">ThreadCreated, metoda</span><span class="sxs-lookup"><span data-stu-id="e9169-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
