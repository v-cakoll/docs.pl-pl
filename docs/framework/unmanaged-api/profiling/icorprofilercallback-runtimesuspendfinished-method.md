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
ms.openlocfilehash: 64611fa7368f05de906b71b08bda8f1e7c460bf3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503240"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="5b723-102">ICorProfilerCallback::RuntimeSuspendFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="5b723-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="5b723-103">Powiadamia profiler o zakończeniu przez środowisko uruchomieniowe wszystkich wątków środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5b723-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b723-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b723-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5b723-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b723-105">Remarks</span></span>  
 <span data-ttu-id="5b723-106">Wszystkie wątki środowiska uruchomieniowego, które znajdują się w kodzie niezarządzanym, mogą kontynuować działanie, dopóki nie spróbują ponownie wprowadzić środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5b723-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="5b723-107">W tym momencie zostaną one również zawieszone do momentu wznowienia działania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5b723-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="5b723-108">Dotyczy to również nowych wątków, które wprowadzają środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="5b723-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="5b723-109">Wszystkie wątki w środowisku uruchomieniowym są zawieszane natychmiast, jeśli znajdują się już w kodzie przerywania lub są proszeni o zawieszenie, gdy osiągną kod przerywania.</span><span class="sxs-lookup"><span data-stu-id="5b723-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="5b723-110">`RuntimeSuspendFinished`Wywołanie zwrotne jest gwarantowane w tym samym wątku, co wywołanie zwrotne [ICorProfilerCallback:: RuntimeSuspendStarted —](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5b723-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b723-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b723-111">Requirements</span></span>  
 <span data-ttu-id="5b723-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b723-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b723-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5b723-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b723-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5b723-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b723-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b723-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b723-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b723-116">See also</span></span>

- [<span data-ttu-id="5b723-117">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5b723-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5b723-118">RuntimeSuspendAborted, metoda</span><span class="sxs-lookup"><span data-stu-id="5b723-118">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
