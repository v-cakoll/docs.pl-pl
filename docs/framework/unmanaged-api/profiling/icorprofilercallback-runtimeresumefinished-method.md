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
ms.openlocfilehash: 5cafbca75992a5fe8a7d3d95628e0018f1a2e8fa
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865951"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="686eb-102">ICorProfilerCallback::RuntimeResumeFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="686eb-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="686eb-103">Powiadamia program profilujący, że środowisko uruchomieniowe wznowił wszystkie wątki środowiska uruchomieniowego i wróciło do normalnego działania.</span><span class="sxs-lookup"><span data-stu-id="686eb-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="686eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="686eb-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="686eb-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="686eb-105">Remarks</span></span>  
 <span data-ttu-id="686eb-106">Wywołanie zwrotne `RuntimeResumeFinished` nie jest gwarantowane w tym samym wątku, co wywołanie zwrotne [ICorProfilerCallback:: RuntimeSuspendStarted —](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="686eb-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="686eb-107">Jednak jest on gwarantowany w tym samym wątku co [ICorProfilerCallback:: RuntimeResumeStarted —](icorprofilercallback-runtimeresumestarted-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="686eb-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="686eb-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="686eb-108">Requirements</span></span>  
 <span data-ttu-id="686eb-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="686eb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="686eb-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="686eb-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="686eb-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="686eb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="686eb-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="686eb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686eb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="686eb-113">See also</span></span>

- [<span data-ttu-id="686eb-114">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="686eb-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
