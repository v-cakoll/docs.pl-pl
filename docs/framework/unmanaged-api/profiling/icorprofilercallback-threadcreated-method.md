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
ms.openlocfilehash: 7fb58c0eb2446253bd658434fc9d68bb857fe0e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175125"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="93885-102">ICorProfilerCallback::ThreadCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="93885-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="93885-103">Powiadamia profiler, że wątek został utworzony.</span><span class="sxs-lookup"><span data-stu-id="93885-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93885-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93885-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="93885-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93885-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="93885-106">[w] Identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="93885-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93885-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93885-107">Remarks</span></span>  
 <span data-ttu-id="93885-108">Wartość `threadId` jest natychmiast prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="93885-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93885-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93885-109">Requirements</span></span>  
 <span data-ttu-id="93885-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93885-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93885-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="93885-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93885-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93885-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93885-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93885-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93885-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93885-114">See also</span></span>

- [<span data-ttu-id="93885-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93885-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="93885-116">ThreadDestroyed, metoda</span><span class="sxs-lookup"><span data-stu-id="93885-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
