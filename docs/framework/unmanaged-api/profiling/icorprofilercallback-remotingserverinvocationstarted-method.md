---
title: ICorProfilerCallback::RemotingServerInvocationStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de2a831e310ac7f770200a70cb793bc19645e31d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="32b21-102">ICorProfilerCallback::RemotingServerInvocationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="32b21-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="32b21-103">Powiadamia profilera, że proces jest wywoływanie metody w odpowiedzi na żądanie wywołania metody zdalnego.</span><span class="sxs-lookup"><span data-stu-id="32b21-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32b21-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32b21-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="32b21-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32b21-105">Requirements</span></span>  
 <span data-ttu-id="32b21-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32b21-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32b21-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32b21-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32b21-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32b21-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32b21-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32b21-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b21-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32b21-110">See Also</span></span>  
 [<span data-ttu-id="32b21-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="32b21-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
