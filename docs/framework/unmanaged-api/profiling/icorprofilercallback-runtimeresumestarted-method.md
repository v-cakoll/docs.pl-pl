---
title: ICorProfilerCallback::RuntimeResumeStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type:
- apiref
ms.openlocfilehash: c7b52954a6be449de0c3633f0ac648980c6d13f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865925"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="dd2e1-102">ICorProfilerCallback::RuntimeResumeStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd2e1-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="dd2e1-103">Powiadamia program profilujący, że środowisko uruchomieniowe wznawia wszystkie wątki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dd2e1-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd2e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd2e1-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="dd2e1-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd2e1-105">Requirements</span></span>  
 <span data-ttu-id="dd2e1-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd2e1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd2e1-107">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dd2e1-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd2e1-108">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dd2e1-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd2e1-109">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd2e1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd2e1-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd2e1-110">See also</span></span>

- [<span data-ttu-id="dd2e1-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd2e1-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="dd2e1-112">RuntimeResumeFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="dd2e1-112">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
