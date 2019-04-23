---
title: ICorProfilerCallback::RuntimeSuspendStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5606a556dd7aeafe6d7a6408d236f2bee8dc773
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168977"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="84e28-102">ICorProfilerCallback::RuntimeSuspendStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="84e28-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="84e28-103">Powiadamia program profilujący, że środowisko uruchomieniowe zostanie wstrzymać wszystkie wątki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="84e28-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84e28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84e28-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84e28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84e28-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="84e28-106">[in] Wartość [cor_prf_suspend_reason —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) wyliczenia, która wskazuje powodem zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="84e28-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84e28-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84e28-107">Remarks</span></span>  
 <span data-ttu-id="84e28-108">Wszystkie wątki środowiska uruchomieniowego, które są w niezarządzanym kodzie są może być kontynuowane, dopóki użytkownik podejmie próbę ponownego wprowadzania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="84e28-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="84e28-109">W tym momencie one zostaną również zawieszone, dopóki nie zostanie wznowione środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="84e28-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="84e28-110">Dotyczy to również nowe wątki, które wprowadzać środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="84e28-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="84e28-111">Albo zawieszone natychmiast, gdy są one już przerywania kodu lub użytkownicy zostaną poproszeni o wstrzymać, gdy osiągną oni limit kodu są to wszystkie wątki w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="84e28-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84e28-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84e28-112">Requirements</span></span>  
 <span data-ttu-id="84e28-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84e28-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84e28-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84e28-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84e28-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84e28-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84e28-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84e28-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e28-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84e28-117">See also</span></span>

- [<span data-ttu-id="84e28-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="84e28-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="84e28-119">RuntimeSuspendAborted, metoda</span><span class="sxs-lookup"><span data-stu-id="84e28-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="84e28-120">RuntimeSuspendFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="84e28-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
