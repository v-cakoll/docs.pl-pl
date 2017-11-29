---
title: "ICorProfilerCallback::RuntimeSuspendAborted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendAborted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d1c181a471763ea0220c081d64af915ca6be149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="6d8cc-102">ICorProfilerCallback::RuntimeSuspendAborted — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d8cc-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="6d8cc-103">Powiadamia profilera, że środowisko wykonawcze została przerwana zawieszenia środowiska uruchomieniowego, które powtarzało się.</span><span class="sxs-lookup"><span data-stu-id="6d8cc-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d8cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d8cc-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6d8cc-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d8cc-105">Remarks</span></span>  
 <span data-ttu-id="6d8cc-106">Zawieszenie środowiska wykonawczego może przerwane w przypadku dwóch wątków jednocześnie próba wstrzymać środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6d8cc-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="6d8cc-107">Albo [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) wywołania zwrotnego lub `RuntimeSuspendAborted` wywołania zwrotnego nastąpi po jednym wątku [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) Wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="6d8cc-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="6d8cc-108">`RuntimeSuspendAborted` Wywołania zwrotnego jest gwarantowana występuje w tym samym wątku, co `RuntimeSuspendStarted` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6d8cc-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d8cc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d8cc-109">Requirements</span></span>  
 <span data-ttu-id="6d8cc-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d8cc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d8cc-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d8cc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d8cc-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d8cc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d8cc-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d8cc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d8cc-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d8cc-114">See Also</span></span>  
 [<span data-ttu-id="6d8cc-115">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="6d8cc-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
