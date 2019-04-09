---
title: ICorProfilerCallback2::FinalizeableObjectQueued — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b99a942d5c5fb205a84dd3766c99cc1126998de8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190403"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="9de33-102">ICorProfilerCallback2::FinalizeableObjectQueued — Metoda</span><span class="sxs-lookup"><span data-stu-id="9de33-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="9de33-103">Powiadamia program profilujący kodu, że obiekt z finalizatorem została umieszczona w kolejce do wątku finalizatora do wykonywania swoich `Finalize` metody.</span><span class="sxs-lookup"><span data-stu-id="9de33-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9de33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9de33-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9de33-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9de33-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="9de33-106">[in] Wartość [cor_prf_finalizer_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) wyliczenie, które opisano aspekty finalizatora.</span><span class="sxs-lookup"><span data-stu-id="9de33-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="9de33-107">[in] Identyfikator obiektu, który zostało umieszczone w kolejce.</span><span class="sxs-lookup"><span data-stu-id="9de33-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9de33-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9de33-108">Requirements</span></span>  
 <span data-ttu-id="9de33-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9de33-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9de33-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9de33-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9de33-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9de33-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9de33-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9de33-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9de33-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9de33-113">See also</span></span>

- [<span data-ttu-id="9de33-114">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9de33-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9de33-115">ICorProfilerCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9de33-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
