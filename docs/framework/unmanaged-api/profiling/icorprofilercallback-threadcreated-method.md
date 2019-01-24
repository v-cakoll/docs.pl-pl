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
ms.openlocfilehash: d85dcb462df0255ab5420db94f9d055cce2c78b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616940"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="198c2-102">ICorProfilerCallback::ThreadCreated — Metoda</span><span class="sxs-lookup"><span data-stu-id="198c2-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="198c2-103">Powiadamia program profilujący, że wątek został utworzony.</span><span class="sxs-lookup"><span data-stu-id="198c2-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="198c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="198c2-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="198c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="198c2-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="198c2-106">[in] Identyfikator wątku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="198c2-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="198c2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="198c2-107">Remarks</span></span>  
 <span data-ttu-id="198c2-108">`threadId` Wartość jest prawidłowa natychmiast.</span><span class="sxs-lookup"><span data-stu-id="198c2-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="198c2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="198c2-109">Requirements</span></span>  
 <span data-ttu-id="198c2-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="198c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="198c2-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="198c2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="198c2-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="198c2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="198c2-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="198c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198c2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="198c2-114">See also</span></span>
- [<span data-ttu-id="198c2-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="198c2-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="198c2-116">ThreadDestroyed, metoda</span><span class="sxs-lookup"><span data-stu-id="198c2-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
