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
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865886"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="50bc2-102">ICorProfilerCallback::RuntimeSuspendStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="50bc2-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="50bc2-103">Powiadamia profiler, że środowisko uruchomieniowe ma wstrzymać wszystkie wątki środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="50bc2-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50bc2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50bc2-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50bc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50bc2-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="50bc2-106">podczas Wartość wyliczenia [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) , która wskazuje przyczynę zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="50bc2-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50bc2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50bc2-107">Remarks</span></span>  
 <span data-ttu-id="50bc2-108">Wszystkie wątki środowiska uruchomieniowego, które znajdują się w kodzie niezarządzanym, mogą kontynuować działanie, dopóki nie spróbują ponownie wprowadzić środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="50bc2-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="50bc2-109">W tym momencie zostaną one również zawieszone do momentu wznowienia działania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="50bc2-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="50bc2-110">Dotyczy to również nowych wątków, które wprowadzają środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="50bc2-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="50bc2-111">Wszystkie wątki w środowisku uruchomieniowym są zawieszane natychmiast, jeśli znajdują się już w kodzie przerywania lub są proszeni o zawieszenie, gdy osiągną kod przerywania.</span><span class="sxs-lookup"><span data-stu-id="50bc2-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50bc2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50bc2-112">Requirements</span></span>  
 <span data-ttu-id="50bc2-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50bc2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50bc2-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="50bc2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50bc2-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="50bc2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50bc2-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50bc2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50bc2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50bc2-117">See also</span></span>

- [<span data-ttu-id="50bc2-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="50bc2-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="50bc2-119">RuntimeSuspendAborted, metoda</span><span class="sxs-lookup"><span data-stu-id="50bc2-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="50bc2-120">RuntimeSuspendFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="50bc2-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
