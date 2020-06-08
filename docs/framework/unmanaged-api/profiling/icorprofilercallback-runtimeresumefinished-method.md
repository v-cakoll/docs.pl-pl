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
ms.openlocfilehash: 8bc97bb0d36a046353587a95aa2b79eff12866e0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499886"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="6d276-102">ICorProfilerCallback::RuntimeResumeFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d276-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="6d276-103">Powiadamia program profilujący, że środowisko uruchomieniowe wznowił wszystkie wątki środowiska uruchomieniowego i wróciło do normalnego działania.</span><span class="sxs-lookup"><span data-stu-id="6d276-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d276-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d276-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6d276-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d276-105">Remarks</span></span>  
 <span data-ttu-id="6d276-106">`RuntimeResumeFinished`Wywołanie zwrotne nie jest gwarantowane w tym samym wątku, co wywołanie zwrotne [ICorProfilerCallback:: RuntimeSuspendStarted —](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6d276-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="6d276-107">Jednak jest on gwarantowany w tym samym wątku co [ICorProfilerCallback:: RuntimeResumeStarted —](icorprofilercallback-runtimeresumestarted-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="6d276-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d276-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d276-108">Requirements</span></span>  
 <span data-ttu-id="6d276-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d276-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d276-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6d276-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d276-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6d276-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d276-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d276-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d276-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d276-113">See also</span></span>

- [<span data-ttu-id="6d276-114">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6d276-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
