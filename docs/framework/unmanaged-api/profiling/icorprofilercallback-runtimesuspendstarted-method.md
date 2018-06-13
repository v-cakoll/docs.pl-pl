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
ms.openlocfilehash: 1197f066332ee131e4ee18fee6487b78b36e5081
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452774"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="802fc-102">ICorProfilerCallback::RuntimeSuspendStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="802fc-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="802fc-103">Powiadamia profilera środowiska uruchomieniowego o zbliżającym się zawiesić wszystkie wątki środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="802fc-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="802fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="802fc-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="802fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="802fc-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="802fc-106">[in] Wartość [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) wyliczenia, która wskazuje przyczynę zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="802fc-106">[in] A value of the [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="802fc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="802fc-107">Remarks</span></span>  
 <span data-ttu-id="802fc-108">Wszystkie wątki środowiska uruchomieniowego należących do kodu niezarządzanego, mogą nadal działać do chwili próbują ponownie wprowadzić środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="802fc-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="802fc-109">W tym momencie one zostaną również zawieszone, dopóki nie zostanie wznowione środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="802fc-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="802fc-110">Dotyczy to również nowy wątków, które należy wprowadzić środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="802fc-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="802fc-111">Wszystkie wątki w środowisku uruchomieniowym są albo zawieszone natychmiast, jeśli są one już przerywania kodu lub użytkownicy zostaną poproszeni o zawiesić po upływie przerywania kodu.</span><span class="sxs-lookup"><span data-stu-id="802fc-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="802fc-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="802fc-112">Requirements</span></span>  
 <span data-ttu-id="802fc-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="802fc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="802fc-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="802fc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="802fc-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="802fc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="802fc-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="802fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="802fc-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="802fc-117">See Also</span></span>  
 [<span data-ttu-id="802fc-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="802fc-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="802fc-119">RuntimeSuspendAborted, metoda</span><span class="sxs-lookup"><span data-stu-id="802fc-119">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)  
 [<span data-ttu-id="802fc-120">RuntimeSuspendFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="802fc-120">RuntimeSuspendFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
