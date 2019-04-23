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
ms.openlocfilehash: d4c45290b1ef4360e51b5ed8e1b0fac3dcdde727
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217344"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="7a5a1-102">ICorProfilerCallback::ThreadDestroyed — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a5a1-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="7a5a1-103">Powiadamia program profilujący wątku została zniszczona.</span><span class="sxs-lookup"><span data-stu-id="7a5a1-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a5a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a5a1-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a5a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a5a1-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="7a5a1-106">[in] Identyfikator wątku, który został zniszczony.</span><span class="sxs-lookup"><span data-stu-id="7a5a1-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a5a1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a5a1-107">Remarks</span></span>  
 <span data-ttu-id="7a5a1-108">`threadId` Wartość nie jest już prawidłowy w czasie tego wywołania.</span><span class="sxs-lookup"><span data-stu-id="7a5a1-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a5a1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a5a1-109">Requirements</span></span>  
 <span data-ttu-id="7a5a1-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a5a1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a5a1-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a5a1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a5a1-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a5a1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a5a1-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a5a1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a5a1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a5a1-114">See also</span></span>

- [<span data-ttu-id="7a5a1-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a5a1-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7a5a1-116">ThreadCreated, metoda</span><span class="sxs-lookup"><span data-stu-id="7a5a1-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
