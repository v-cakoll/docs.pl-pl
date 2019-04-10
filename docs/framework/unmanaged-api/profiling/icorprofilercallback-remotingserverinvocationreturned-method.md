---
title: ICorProfilerCallback::RemotingServerInvocationReturned — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationReturned
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned method [.NET Framework profiling]
- RemotingServerInvocationReturned method [.NET Framework profiling]
ms.assetid: a4de6805-e159-4280-99e5-3390c86166d0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00f5fd44d340a76200537871a9860f67601b66d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208712"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="ab66f-102">ICorProfilerCallback::RemotingServerInvocationReturned — Metoda</span><span class="sxs-lookup"><span data-stu-id="ab66f-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="ab66f-103">Powiadamia program profilujący, że proces zostanie zakończony, wywołania metody w odpowiedzi na żądanie wywołania zdalnej metody.</span><span class="sxs-lookup"><span data-stu-id="ab66f-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab66f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab66f-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ab66f-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab66f-105">Requirements</span></span>  
 <span data-ttu-id="ab66f-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab66f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab66f-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab66f-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab66f-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab66f-108">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ab66f-109">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ab66f-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab66f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab66f-110">See also</span></span>

- [<span data-ttu-id="ab66f-111">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ab66f-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
