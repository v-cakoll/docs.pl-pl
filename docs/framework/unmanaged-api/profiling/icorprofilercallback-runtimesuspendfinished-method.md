---
title: "ICorProfilerCallback::RuntimeSuspendFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6127d0c5f3b193dad1586cdaf92beb8d8734376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="261dc-102">ICorProfilerCallback::RuntimeSuspendFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="261dc-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="261dc-103">Powiadamia profilera, czy środowisko uruchomieniowe zostało zakończone zawieszenia wszystkie wątki środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="261dc-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="261dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="261dc-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="261dc-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="261dc-105">Remarks</span></span>  
 <span data-ttu-id="261dc-106">Wszystkie wątki środowiska uruchomieniowego należących do kodu niezarządzanego, mogą nadal działać do chwili próbują ponownie wprowadzić środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="261dc-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="261dc-107">W tym momencie one zostaną również zawieszone, dopóki nie zostanie wznowione środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="261dc-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="261dc-108">Dotyczy to również nowy wątków, które należy wprowadzić środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="261dc-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="261dc-109">Wszystkie wątki w środowisku uruchomieniowym są albo zawieszone natychmiast, jeśli są one już przerywania kodu lub użytkownicy zostaną poproszeni o zawiesić po upływie przerywania kodu.</span><span class="sxs-lookup"><span data-stu-id="261dc-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="261dc-110">`RuntimeSuspendFinished` Wywołania zwrotnego jest gwarantowana występuje w tym samym wątku, co [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="261dc-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="261dc-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="261dc-111">Requirements</span></span>  
 <span data-ttu-id="261dc-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="261dc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="261dc-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="261dc-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="261dc-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="261dc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="261dc-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="261dc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261dc-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="261dc-116">See Also</span></span>  
 [<span data-ttu-id="261dc-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="261dc-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="261dc-118">RuntimeSuspendAborted, metoda</span><span class="sxs-lookup"><span data-stu-id="261dc-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
