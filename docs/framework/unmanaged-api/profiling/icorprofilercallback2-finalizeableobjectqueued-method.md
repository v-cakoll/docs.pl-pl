---
title: "ICorProfilerCallback2::FinalizeableObjectQueued — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.FinalizeableObjectQueued
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ed9c66f7d588d855daa550031c832810b914d49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="ddcc5-102">ICorProfilerCallback2::FinalizeableObjectQueued — Metoda</span><span class="sxs-lookup"><span data-stu-id="ddcc5-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="ddcc5-103">Powiadamia profilera kodu, że obiekt o finalizator zostało umieszczone w kolejce do wątku finalizatora dla wykonywania jego `Finalize` metody.</span><span class="sxs-lookup"><span data-stu-id="ddcc5-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddcc5-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddcc5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddcc5-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="ddcc5-106">[in] Wartość [cor_prf_finalizer_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) wyliczenie opisujące aspektów finalizatora.</span><span class="sxs-lookup"><span data-stu-id="ddcc5-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="ddcc5-107">[in] Identyfikator obiektu, które zostało umieszczone w kolejce.</span><span class="sxs-lookup"><span data-stu-id="ddcc5-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddcc5-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddcc5-108">Requirements</span></span>  
 <span data-ttu-id="ddcc5-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddcc5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddcc5-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ddcc5-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ddcc5-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddcc5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddcc5-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddcc5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcc5-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddcc5-113">See Also</span></span>  
 [<span data-ttu-id="ddcc5-114">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ddcc5-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ddcc5-115">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ddcc5-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
