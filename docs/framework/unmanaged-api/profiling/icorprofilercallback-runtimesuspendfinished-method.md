---
title: ICorProfilerCallback::RuntimeSuspendFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f69c39938384c7feca28ae40aba3e80a0ba28ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706657"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="de663-102">ICorProfilerCallback::RuntimeSuspendFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="de663-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="de663-103">Powiadamia program profilujący, że środowisko uruchomieniowe ukończono zawieszenia wszystkie wątki środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="de663-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de663-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de663-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="de663-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de663-105">Remarks</span></span>  
 <span data-ttu-id="de663-106">Wszystkie wątki środowiska uruchomieniowego, które są w niezarządzanym kodzie są może być kontynuowane, dopóki użytkownik podejmie próbę ponownego wprowadzania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="de663-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="de663-107">W tym momencie one zostaną również zawieszone, dopóki nie zostanie wznowione środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="de663-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="de663-108">Dotyczy to również nowe wątki, które wprowadzać środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="de663-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="de663-109">Albo zawieszone natychmiast, gdy są one już przerywania kodu lub użytkownicy zostaną poproszeni o wstrzymać, gdy osiągną oni limit kodu są to wszystkie wątki w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="de663-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="de663-110">`RuntimeSuspendFinished` Wywołania zwrotnego jest gwarantowane, odbywa się na tym samym wątku jako [icorprofilercallback::runtimesuspendstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="de663-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de663-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de663-111">Requirements</span></span>  
 <span data-ttu-id="de663-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de663-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de663-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="de663-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de663-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de663-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de663-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de663-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de663-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de663-116">See also</span></span>
- [<span data-ttu-id="de663-117">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="de663-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="de663-118">RuntimeSuspendAborted, metoda</span><span class="sxs-lookup"><span data-stu-id="de663-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
