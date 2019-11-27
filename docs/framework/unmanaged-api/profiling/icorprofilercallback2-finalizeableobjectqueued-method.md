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
ms.openlocfilehash: ade0ba0517e47e9500683836b87d7a8ac1dfcfdb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439860"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="90921-102">ICorProfilerCallback2::FinalizeableObjectQueued — Metoda</span><span class="sxs-lookup"><span data-stu-id="90921-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="90921-103">Powiadamia profiler kodu o tym, że obiekt z finalizatorem został umieszczony w kolejce finalizatora na potrzeby wykonywania `Finalize` metodzie.</span><span class="sxs-lookup"><span data-stu-id="90921-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90921-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90921-104">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90921-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90921-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="90921-106">podczas Wartość wyliczenia [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) opisująca aspekty finalizatora.</span><span class="sxs-lookup"><span data-stu-id="90921-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="90921-107">podczas Identyfikator obiektu, który został umieszczony w kolejce.</span><span class="sxs-lookup"><span data-stu-id="90921-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90921-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90921-108">Requirements</span></span>  
 <span data-ttu-id="90921-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90921-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90921-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="90921-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90921-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="90921-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90921-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90921-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90921-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90921-113">See also</span></span>

- [<span data-ttu-id="90921-114">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="90921-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="90921-115">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="90921-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
