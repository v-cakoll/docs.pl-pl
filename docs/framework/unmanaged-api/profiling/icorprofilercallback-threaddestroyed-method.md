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
ms.openlocfilehash: 07041d06668d474a3d30968fb623854a24ebf0eb
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865821"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="8f4b1-102">ICorProfilerCallback::ThreadDestroyed — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f4b1-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="8f4b1-103">Powiadamia profiler o zniszczeniu wątku.</span><span class="sxs-lookup"><span data-stu-id="8f4b1-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f4b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f4b1-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f4b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f4b1-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="8f4b1-106">podczas Identyfikator wątku, który został zniszczony.</span><span class="sxs-lookup"><span data-stu-id="8f4b1-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f4b1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f4b1-107">Remarks</span></span>  
 <span data-ttu-id="8f4b1-108">Wartość `threadId` nie jest już prawidłowa w czasie tego wywołania.</span><span class="sxs-lookup"><span data-stu-id="8f4b1-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f4b1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f4b1-109">Requirements</span></span>  
 <span data-ttu-id="8f4b1-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f4b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f4b1-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8f4b1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f4b1-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8f4b1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f4b1-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f4b1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f4b1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f4b1-114">See also</span></span>

- [<span data-ttu-id="8f4b1-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f4b1-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8f4b1-116">ThreadCreated, metoda</span><span class="sxs-lookup"><span data-stu-id="8f4b1-116">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
