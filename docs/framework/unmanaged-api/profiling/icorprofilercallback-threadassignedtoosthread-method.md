---
title: "ICorProfilerCallback::ThreadAssignedToOSThread — Metoda"
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
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 42c23a8190ea611d0333ebd96a31428574191b23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="5fafb-102">ICorProfilerCallback::ThreadAssignedToOSThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="5fafb-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="5fafb-103">Powiadamia profilera, że zarządzanego wątku jest implementowana przy użyciu wątku określonym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="5fafb-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fafb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fafb-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fafb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fafb-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="5fafb-106">[in] Identyfikator zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="5fafb-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="5fafb-107">[in] Identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5fafb-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fafb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5fafb-108">Remarks</span></span>  
 <span data-ttu-id="5fafb-109">`ThreadAssignedToOSThread` Wywołania zwrotnego istnieje, dzięki czemu profilera można zachować dokładne mapowania między włókien wątków zarządzanych wątków i systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5fafb-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fafb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5fafb-110">Requirements</span></span>  
 <span data-ttu-id="5fafb-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fafb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fafb-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5fafb-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5fafb-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fafb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fafb-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fafb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fafb-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fafb-115">See Also</span></span>  
 [<span data-ttu-id="5fafb-116">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="5fafb-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
