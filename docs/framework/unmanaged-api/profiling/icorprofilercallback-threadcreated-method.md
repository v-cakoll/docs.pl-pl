---
title: ICorProfilerCallback::ThreadCreated — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f8eca3e8eb755e31e704e557ae614a6e5c1f534
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107773"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="325fd-102">ICorProfilerCallback::ThreadCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="325fd-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="325fd-103">Powiadamia program profilujący, że wątek został utworzony.</span><span class="sxs-lookup"><span data-stu-id="325fd-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="325fd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="325fd-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="325fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="325fd-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="325fd-106">[in] Identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="325fd-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="325fd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="325fd-107">Remarks</span></span>  
 <span data-ttu-id="325fd-108">`threadId` Wartość jest prawidłowa natychmiast.</span><span class="sxs-lookup"><span data-stu-id="325fd-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="325fd-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="325fd-109">Requirements</span></span>  
 <span data-ttu-id="325fd-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="325fd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="325fd-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="325fd-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="325fd-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="325fd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="325fd-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="325fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="325fd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="325fd-114">See also</span></span>

- [<span data-ttu-id="325fd-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="325fd-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="325fd-116">ThreadDestroyed, metoda</span><span class="sxs-lookup"><span data-stu-id="325fd-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
