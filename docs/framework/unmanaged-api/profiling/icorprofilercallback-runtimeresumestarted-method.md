---
title: "ICorProfilerCallback::RuntimeResumeStarted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeResumeStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf63dd0882784750747a3fe5a68bb8dd432c4a78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="8461b-102">ICorProfilerCallback::RuntimeResumeStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="8461b-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="8461b-103">Powiadamia profilera, że środowisko wykonawcze jest wznawianie wszystkie wątki środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="8461b-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8461b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8461b-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="8461b-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8461b-105">Requirements</span></span>  
 <span data-ttu-id="8461b-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8461b-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8461b-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8461b-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8461b-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8461b-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8461b-109">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8461b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8461b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8461b-110">See Also</span></span>  
 [<span data-ttu-id="8461b-111">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="8461b-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8461b-112">RuntimeResumeFinished — metoda</span><span class="sxs-lookup"><span data-stu-id="8461b-112">RuntimeResumeFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)
