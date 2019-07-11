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
ms.openlocfilehash: 51c7235b4018fabb2ecf9c0db2800d5d9e54b327
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747141"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="738cf-102">ICorProfilerCallback::ThreadAssignedToOSThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="738cf-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="738cf-103">Powiadamia program profilujący, że wątków zarządzanych wdrażane za pomocą wątku określonego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="738cf-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="738cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="738cf-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="738cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="738cf-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="738cf-106">[in] Identyfikator wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="738cf-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="738cf-107">[in] Identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="738cf-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="738cf-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="738cf-108">Remarks</span></span>  
 <span data-ttu-id="738cf-109">`ThreadAssignedToOSThread` Wywołania zwrotnego istnieje tak, aby program profilujący może zachować dokładne mapowania między włókien wątków zarządzanych wątków systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="738cf-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="738cf-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="738cf-110">Requirements</span></span>  
 <span data-ttu-id="738cf-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="738cf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="738cf-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="738cf-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="738cf-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="738cf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="738cf-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="738cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738cf-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="738cf-115">See also</span></span>

- [<span data-ttu-id="738cf-116">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="738cf-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
