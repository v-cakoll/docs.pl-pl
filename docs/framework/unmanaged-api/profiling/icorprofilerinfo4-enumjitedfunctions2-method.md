---
title: ICorProfilerInfo4::EnumJITedFunctions2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92bc16091abd3e21ebd226fb13dd47b55b0c9cc4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166832"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="374a9-102">ICorProfilerInfo4::EnumJITedFunctions2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="374a9-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="374a9-103">Zwraca moduł wyliczający dla wszystkich funkcji, które wcześniej były skompilowane JIT i ponownie skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="374a9-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="374a9-104">Ta metoda zastępuje [icorprofilerinfo3::enumjitedfunctions —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metody, która nie wyliczyć identyfikatory ponownie skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="374a9-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="374a9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="374a9-105">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="374a9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="374a9-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="374a9-107">[out] Wskaźnik do [icorprofilerfunctionenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="374a9-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="374a9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="374a9-108">Remarks</span></span>  
 <span data-ttu-id="374a9-109">Ta metoda może pokrywać się z `JITCompilation` wywołań zwrotnych, takie jak [icorprofilercallback::jitcompilationstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="374a9-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="374a9-110">Zwrócone wyliczenia zawiera wartości `COR_PRF_FUNCTION::reJitId` pola.</span><span class="sxs-lookup"><span data-stu-id="374a9-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="374a9-111">[Icorprofilerinfo3::enumjitedfunctions —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metody, która zastępuje tę metodę, wyliczyć identyfikatory ponownie skompilowana JIT, ponieważ `COR_PRF_FUNCTION::reJitId` pole jest zawsze równa 0.</span><span class="sxs-lookup"><span data-stu-id="374a9-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="374a9-112">`ICorProfilerInfo4::EnumJITedFunctions` Metoda wyliczyć identyfikatory ponownie skompilowana JIT, ponieważ `COR_PRF_FUNCTION::reJitId` pole jest ustawione prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="374a9-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="374a9-113">Należy pamiętać, że [icorprofilerinfo4::enumjitedfunctions2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metody, które mogą wyzwalać wyrzucania elementów bezużytecznych, natomiast [icorprofilerinfo3::enumjitedfunctions — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) nie będzie.</span><span class="sxs-lookup"><span data-stu-id="374a9-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="374a9-114">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="374a9-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="374a9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="374a9-115">Requirements</span></span>  
 <span data-ttu-id="374a9-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="374a9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="374a9-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="374a9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="374a9-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="374a9-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="374a9-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="374a9-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="374a9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="374a9-120">See also</span></span>

- [<span data-ttu-id="374a9-121">EnumJITedFunctions, metoda</span><span class="sxs-lookup"><span data-stu-id="374a9-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="374a9-122">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="374a9-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="374a9-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="374a9-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="374a9-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="374a9-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
