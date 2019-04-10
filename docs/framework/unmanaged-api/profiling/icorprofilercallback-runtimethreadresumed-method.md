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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 810875d1b91265fe886ce3cd11970cad7fee122d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228864"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="240e9-102">ICorProfilerCallback::RuntimeThreadResumed — Metoda</span><span class="sxs-lookup"><span data-stu-id="240e9-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="240e9-103">Powiadamia program profilujący, że określony wątek została wznowiona po wstrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="240e9-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="240e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="240e9-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="240e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="240e9-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="240e9-106">[in] Identyfikator wątku, który zostało wznowione.</span><span class="sxs-lookup"><span data-stu-id="240e9-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="240e9-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="240e9-107">Requirements</span></span>  
 <span data-ttu-id="240e9-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="240e9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="240e9-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="240e9-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="240e9-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="240e9-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="240e9-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="240e9-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="240e9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="240e9-112">See also</span></span>

- [<span data-ttu-id="240e9-113">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="240e9-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="240e9-114">RuntimeThreadSuspended, metoda</span><span class="sxs-lookup"><span data-stu-id="240e9-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
