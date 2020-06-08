---
title: ICorProfilerCallback::AppDomainShutdownStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: 1b973cdeaffbec0dad1f2d082c44e8001647fdcc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500458"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="c9e92-102">ICorProfilerCallback::AppDomainShutdownStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9e92-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="c9e92-103">Powiadamia profiler o tym, że domena aplikacji jest zwalniana z procesu.</span><span class="sxs-lookup"><span data-stu-id="c9e92-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e92-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9e92-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9e92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9e92-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="c9e92-106">\[w programie] identyfikuje domenę, w której są przechowywane zestawy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9e92-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9e92-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9e92-107">Remarks</span></span>  
 <span data-ttu-id="c9e92-108">Wartość `appDomainId` nie jest prawidłowa dla żadnych żądań informacji po `AppDomainShutdownStarted` powrocie metody — jest to Ostatnia szansa dla profilera, aby uzyskać informacje o tej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9e92-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e92-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9e92-109">Requirements</span></span>  
 <span data-ttu-id="c9e92-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9e92-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9e92-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c9e92-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9e92-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c9e92-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9e92-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9e92-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e92-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9e92-114">See also</span></span>

- [<span data-ttu-id="c9e92-115">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c9e92-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
