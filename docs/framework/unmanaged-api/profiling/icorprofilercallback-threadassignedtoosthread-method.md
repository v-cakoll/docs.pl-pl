---
title: ICorProfilerCallback::ThreadAssignedToOSThread — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eefcd4436a28fdf52cbe55da5d4bb7eea4449463
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158460"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="91854-102">ICorProfilerCallback::ThreadAssignedToOSThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="91854-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="91854-103">Powiadamia program profilujący, że wątków zarządzanych wdrażane za pomocą wątku określonego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="91854-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91854-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91854-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91854-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91854-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="91854-106">[in] Identyfikator wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="91854-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="91854-107">[in] Identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="91854-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91854-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91854-108">Remarks</span></span>  
 <span data-ttu-id="91854-109">`ThreadAssignedToOSThread` Wywołania zwrotnego istnieje tak, aby program profilujący może zachować dokładne mapowania między włókien wątków zarządzanych wątków systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="91854-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91854-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91854-110">Requirements</span></span>  
 <span data-ttu-id="91854-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91854-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91854-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91854-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91854-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91854-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="91854-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="91854-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="91854-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91854-115">See also</span></span>

- [<span data-ttu-id="91854-116">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="91854-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
