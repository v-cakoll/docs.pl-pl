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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041928"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="0304d-102">ICorProfilerCallback::RemotingServerInvocationReturned — Metoda</span><span class="sxs-lookup"><span data-stu-id="0304d-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="0304d-103">Powiadamia program profilujący, że proces zostanie zakończony, wywołania metody w odpowiedzi na żądanie wywołania zdalnej metody.</span><span class="sxs-lookup"><span data-stu-id="0304d-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0304d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0304d-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0304d-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0304d-105">Requirements</span></span>  
 <span data-ttu-id="0304d-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0304d-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0304d-107">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0304d-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0304d-108">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0304d-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0304d-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0304d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0304d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0304d-110">See also</span></span>

- [<span data-ttu-id="0304d-111">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="0304d-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
