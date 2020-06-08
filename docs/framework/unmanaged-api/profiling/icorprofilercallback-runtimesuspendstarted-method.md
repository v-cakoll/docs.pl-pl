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
ms.openlocfilehash: cc01254d9604ce39c964c7d78059ef4087483c77
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503227"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="832c4-102">ICorProfilerCallback::RuntimeSuspendStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="832c4-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>
<span data-ttu-id="832c4-103">Powiadamia profiler, że środowisko uruchomieniowe ma wstrzymać wszystkie wątki środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="832c4-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="832c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="832c4-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="832c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="832c4-105">Parameters</span></span>  
 `suspendReason`  
 <span data-ttu-id="832c4-106">podczas Wartość wyliczenia [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) , która wskazuje przyczynę zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="832c4-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="832c4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="832c4-107">Remarks</span></span>  
 <span data-ttu-id="832c4-108">Wszystkie wątki środowiska uruchomieniowego, które znajdują się w kodzie niezarządzanym, mogą kontynuować działanie, dopóki nie spróbują ponownie wprowadzić środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="832c4-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="832c4-109">W tym momencie zostaną one również zawieszone do momentu wznowienia działania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="832c4-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="832c4-110">Dotyczy to również nowych wątków, które wprowadzają środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="832c4-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="832c4-111">Wszystkie wątki w środowisku uruchomieniowym są zawieszane natychmiast, jeśli znajdują się już w kodzie przerywania lub są proszeni o zawieszenie, gdy osiągną kod przerywania.</span><span class="sxs-lookup"><span data-stu-id="832c4-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="832c4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="832c4-112">Requirements</span></span>  
 <span data-ttu-id="832c4-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="832c4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="832c4-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="832c4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="832c4-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="832c4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="832c4-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="832c4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="832c4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="832c4-117">See also</span></span>

- [<span data-ttu-id="832c4-118">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="832c4-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="832c4-119">RuntimeSuspendAborted, metoda</span><span class="sxs-lookup"><span data-stu-id="832c4-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="832c4-120">RuntimeSuspendFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="832c4-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
