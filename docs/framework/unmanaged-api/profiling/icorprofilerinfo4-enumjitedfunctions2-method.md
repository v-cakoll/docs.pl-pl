---
title: "ICorProfilerInfo4::EnumJITedFunctions2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumJITedFunctions2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7dc381848307ea0606f6989d6946c11aa5ef9a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="5dd35-102">ICorProfilerInfo4::EnumJITedFunctions2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="5dd35-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="5dd35-103">Zwraca moduł wyliczający dla wszystkich funkcji, które były wcześniej kompilacji JIT i ponownie kompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="5dd35-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="5dd35-104">Ta metoda zastępuje [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metodę, która Wylicza identyfikatory ponownie kompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="5dd35-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dd35-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5dd35-105">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5dd35-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5dd35-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5dd35-107">[out] Wskaźnik do [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="5dd35-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dd35-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5dd35-108">Remarks</span></span>  
 <span data-ttu-id="5dd35-109">Ta metoda może nakładać się na `JITCompilation` wywołań zwrotnych, takich jak [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="5dd35-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="5dd35-110">Zawiera wyliczenie zwracane wartości `COR_PRF_FUNCTION::reJitId` pola.</span><span class="sxs-lookup"><span data-stu-id="5dd35-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="5dd35-111">[ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metodę, która zastępuje tę metodę, wylicza identyfikatory ponownie kompilowana JIT, ponieważ `COR_PRF_FUNCTION::reJitId` pole jest zawsze równa 0.</span><span class="sxs-lookup"><span data-stu-id="5dd35-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="5dd35-112">`ICorProfilerInfo4::EnumJITedFunctions` — Metoda wyliczania identyfikatory ponownie kompilowana JIT, ponieważ `COR_PRF_FUNCTION::reJitId` pole jest ustawione prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="5dd35-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="5dd35-113">Należy pamiętać, że [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metody może wyzwolić wyrzucania elementów bezużytecznych, podczas gdy [ICorProfilerInfo3::EnumJITedFunctions — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) nie.</span><span class="sxs-lookup"><span data-stu-id="5dd35-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="5dd35-114">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="5dd35-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dd35-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5dd35-115">Requirements</span></span>  
 <span data-ttu-id="5dd35-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dd35-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dd35-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5dd35-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5dd35-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dd35-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dd35-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dd35-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd35-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5dd35-120">See Also</span></span>  
 [<span data-ttu-id="5dd35-121">EnumJITedFunctions, metoda</span><span class="sxs-lookup"><span data-stu-id="5dd35-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)  
 [<span data-ttu-id="5dd35-122">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="5dd35-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="5dd35-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="5dd35-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5dd35-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="5dd35-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
