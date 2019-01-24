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
ms.openlocfilehash: 3a64941c35630e76e05ac982725c9eb3f5583d12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495998"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="f0946-102">ICorProfilerCallback::RemotingServerInvocationReturned — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0946-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="f0946-103">Powiadamia program profilujący, że proces zostanie zakończony, wywołania metody w odpowiedzi na żądanie wywołania zdalnej metody.</span><span class="sxs-lookup"><span data-stu-id="f0946-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0946-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0946-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f0946-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0946-105">Requirements</span></span>  
 <span data-ttu-id="f0946-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0946-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0946-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0946-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0946-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0946-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0946-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0946-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0946-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0946-110">See also</span></span>
- [<span data-ttu-id="f0946-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0946-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
