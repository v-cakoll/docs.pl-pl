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
ms.openlocfilehash: 25a4b101388bfc0151ba7c9c52da6561d48f806b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503162"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="ec082-102">ICorProfilerCallback::ThreadCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec082-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="ec082-103">Powiadamia program profilujący o utworzeniu wątku.</span><span class="sxs-lookup"><span data-stu-id="ec082-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec082-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec082-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="ec082-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec082-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ec082-106">podczas Identyfikator utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="ec082-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec082-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec082-107">Remarks</span></span>  
 <span data-ttu-id="ec082-108">`threadId`Wartość jest natychmiast ważna.</span><span class="sxs-lookup"><span data-stu-id="ec082-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec082-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec082-109">Requirements</span></span>  
 <span data-ttu-id="ec082-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec082-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec082-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ec082-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec082-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ec082-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec082-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec082-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec082-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec082-114">See also</span></span>

- [<span data-ttu-id="ec082-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ec082-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ec082-116">ThreadDestroyed, metoda</span><span class="sxs-lookup"><span data-stu-id="ec082-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
