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
ms.openlocfilehash: ccb970fb2eb387f1be795f9322d5bf9650593a35
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445767"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="d2583-102">ICorProfilerCallback::RemotingServerInvocationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2583-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="d2583-103">Powiadamia program profilujący, że proces wywołuje metodę w odpowiedzi na żądanie wywołania metody zdalnej.</span><span class="sxs-lookup"><span data-stu-id="d2583-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2583-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2583-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d2583-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2583-105">Requirements</span></span>  
 <span data-ttu-id="d2583-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2583-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2583-107">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d2583-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2583-108">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d2583-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2583-109">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2583-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2583-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2583-110">See also</span></span>

- [<span data-ttu-id="d2583-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2583-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
