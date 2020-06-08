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
ms.openlocfilehash: e2e01c396a67614464e3d4ca50de992388961463
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499829"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="1fe88-102">ICorProfilerCallback2::FinalizeableObjectQueued — Metoda</span><span class="sxs-lookup"><span data-stu-id="1fe88-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="1fe88-103">Powiadamia profiler kodu o tym, że obiekt z finalizatorem został umieszczony w kolejce finalizatora w celu wykonania jego `Finalize` metody.</span><span class="sxs-lookup"><span data-stu-id="1fe88-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fe88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fe88-104">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fe88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fe88-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="1fe88-106">podczas Wartość wyliczenia [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) opisująca aspekty finalizatora.</span><span class="sxs-lookup"><span data-stu-id="1fe88-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="1fe88-107">podczas Identyfikator obiektu, który został umieszczony w kolejce.</span><span class="sxs-lookup"><span data-stu-id="1fe88-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fe88-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1fe88-108">Requirements</span></span>  
 <span data-ttu-id="1fe88-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fe88-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fe88-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1fe88-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1fe88-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1fe88-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fe88-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fe88-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe88-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fe88-113">See also</span></span>

- [<span data-ttu-id="1fe88-114">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1fe88-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1fe88-115">ICorProfilerCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1fe88-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
