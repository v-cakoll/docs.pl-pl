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
ms.openlocfilehash: 3725b73ab55f6e4dc789a1fde8d1224695a174d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499938"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="679f2-102">ICorProfilerCallback::RemotingServerInvocationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="679f2-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="679f2-103">Powiadamia program profilujący, że proces wywołuje metodę w odpowiedzi na żądanie wywołania metody zdalnej.</span><span class="sxs-lookup"><span data-stu-id="679f2-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="679f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="679f2-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="679f2-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="679f2-105">Requirements</span></span>  
 <span data-ttu-id="679f2-106">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="679f2-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="679f2-107">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="679f2-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="679f2-108">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="679f2-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="679f2-109">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="679f2-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="679f2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="679f2-110">See also</span></span>

- [<span data-ttu-id="679f2-111">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="679f2-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
