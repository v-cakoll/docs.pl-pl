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
ms.openlocfilehash: 83c9a4aa165057f1345de2c6f5bda80e4317d06c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221811"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="41065-102">ICorProfilerCallback::RemotingServerInvocationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="41065-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="41065-103">Powiadamia program profilujący, że proces jest wywoływanie metody w odpowiedzi na żądanie wywołania zdalnej metody.</span><span class="sxs-lookup"><span data-stu-id="41065-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41065-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41065-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="41065-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41065-105">Requirements</span></span>  
 <span data-ttu-id="41065-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41065-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41065-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41065-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41065-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41065-108">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="41065-109">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="41065-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="41065-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41065-110">See also</span></span>

- [<span data-ttu-id="41065-111">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="41065-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
