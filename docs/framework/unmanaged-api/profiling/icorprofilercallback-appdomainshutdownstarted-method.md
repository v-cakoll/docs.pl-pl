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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd1e5daada8793e94980afc5f0cf509915bd288e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450932"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="8e8fe-102">ICorProfilerCallback::AppDomainShutdownStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="8e8fe-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="8e8fe-103">Powiadamia profilera, że z procesem Zwalnianie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e8fe-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e8fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e8fe-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e8fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e8fe-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="8e8fe-106">[in] Identyfikuje domenę, w której są przechowywane zestawów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e8fe-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e8fe-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e8fe-107">Remarks</span></span>  
 <span data-ttu-id="8e8fe-108">Wartość `appDomainId` jest nieprawidłowa dla żądania żadnych informacji po `AppDomainShutdownStarted` metoda zwraca — jest to profilera ostatnia możliwość uzyskania informacji na temat tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e8fe-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e8fe-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e8fe-109">Requirements</span></span>  
 <span data-ttu-id="8e8fe-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e8fe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e8fe-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e8fe-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e8fe-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e8fe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e8fe-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e8fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e8fe-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e8fe-114">See Also</span></span>  
 [<span data-ttu-id="8e8fe-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e8fe-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
