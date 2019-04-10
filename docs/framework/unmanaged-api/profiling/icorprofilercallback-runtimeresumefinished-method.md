---
title: ICorProfilerCallback::RuntimeResumeFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c7b3c3ea5e976645c265b34327caa38ef6a28fd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226992"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="5be31-102">ICorProfilerCallback::RuntimeResumeFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="5be31-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="5be31-103">Powiadamia program profilujący, że środowisko uruchomieniowe wznowił wszystkie wątki środowiska uruchomieniowego i ma powrót do normalnego działania.</span><span class="sxs-lookup"><span data-stu-id="5be31-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5be31-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5be31-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5be31-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5be31-105">Remarks</span></span>  
 <span data-ttu-id="5be31-106">`RuntimeResumeFinished` Wywołanie zwrotne nie jest gwarantowana w tym samym wątku jako [icorprofilercallback::runtimesuspendstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5be31-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="5be31-107">Jednak może wystąpić w tym samym wątku, jako [icorprofilercallback::runtimeresumestarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5be31-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5be31-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5be31-108">Requirements</span></span>  
 <span data-ttu-id="5be31-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5be31-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5be31-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5be31-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5be31-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5be31-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5be31-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5be31-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5be31-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5be31-113">See also</span></span>

- [<span data-ttu-id="5be31-114">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5be31-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
