---
title: "ICorProfilerCallback::AppDomainShutdownStarted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainShutdownStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14e515ae13e0a445580dabcdfa30253da94fd216
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="60dab-102">ICorProfilerCallback::AppDomainShutdownStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="60dab-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="60dab-103">Powiadamia profilera, że z procesem Zwalnianie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60dab-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60dab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60dab-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60dab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60dab-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="60dab-106">[in] Identyfikuje domenę, w której są przechowywane zestawów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60dab-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60dab-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60dab-107">Remarks</span></span>  
 <span data-ttu-id="60dab-108">Wartość `appDomainId` jest nieprawidłowa dla żądania żadnych informacji po `AppDomainShutdownStarted` metoda zwraca — jest to profilera ostatnia możliwość uzyskania informacji na temat tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60dab-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60dab-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60dab-109">Requirements</span></span>  
 <span data-ttu-id="60dab-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60dab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60dab-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60dab-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60dab-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60dab-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60dab-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60dab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60dab-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60dab-114">See Also</span></span>  
 [<span data-ttu-id="60dab-115">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="60dab-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
