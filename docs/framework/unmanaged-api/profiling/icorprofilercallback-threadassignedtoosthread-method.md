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
ms.openlocfilehash: 182a82300183046ccb4a93a79af0dd8f23848c20
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503181"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="fafad-102">ICorProfilerCallback::ThreadAssignedToOSThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="fafad-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="fafad-103">Powiadamia program profilujący o implementacji wątku zarządzanego przy użyciu określonego wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="fafad-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fafad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fafad-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fafad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fafad-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="fafad-106">podczas Identyfikator zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="fafad-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="fafad-107">podczas Identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="fafad-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fafad-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fafad-108">Remarks</span></span>  
 <span data-ttu-id="fafad-109">`ThreadAssignedToOSThread`Wywołanie zwrotne istnieje, aby Profiler mógł zachować dokładne mapowanie w włókien wątków systemu operacyjnego do zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="fafad-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fafad-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fafad-110">Requirements</span></span>  
 <span data-ttu-id="fafad-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fafad-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fafad-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fafad-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fafad-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fafad-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fafad-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fafad-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fafad-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fafad-115">See also</span></span>

- [<span data-ttu-id="fafad-116">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fafad-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
