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
ms.openlocfilehash: 3903ebf1ad35bd7eb1ba49b4f1acda9024678423
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862207"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="0da1e-102">ICorProfilerInfo4::EnumJITedFunctions2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="0da1e-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="0da1e-103">Zwraca moduł wyliczający dla wszystkich funkcji, które były poprzednio skompilowane JIT i ponownie skompilowane w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="0da1e-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="0da1e-104">Ta metoda zastępuje metodę [ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) , która nie WYLICZA identyfikatorów JIT-ponownie kompilowanych.</span><span class="sxs-lookup"><span data-stu-id="0da1e-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da1e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0da1e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0da1e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0da1e-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="0da1e-107">określoną Wskaźnik do modułu wyliczającego [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0da1e-107">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0da1e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0da1e-108">Remarks</span></span>  
 <span data-ttu-id="0da1e-109">Ta metoda może nakładać się na wywołania zwrotne `JITCompilation`, takie jak Metoda [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0da1e-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="0da1e-110">Zwrócone Wyliczenie zawiera wartości pola `COR_PRF_FUNCTION::reJitId`.</span><span class="sxs-lookup"><span data-stu-id="0da1e-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="0da1e-111">Metoda [ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) , która zastępuje tę metodę, nie wylicza identyfikatorów, które ponownie skompilowano JIT, ponieważ pole `COR_PRF_FUNCTION::reJitId` ma zawsze wartość 0.</span><span class="sxs-lookup"><span data-stu-id="0da1e-111">The [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="0da1e-112">Metoda `ICorProfilerInfo4::EnumJITedFunctions` wylicza identyfikatory ponownie skompilowane JIT, ponieważ pole `COR_PRF_FUNCTION::reJitId` jest ustawione prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="0da1e-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="0da1e-113">Należy pamiętać, że metoda [ICorProfilerInfo4:: EnumJITedFunctions2 —](icorprofilerinfo4-enumjitedfunctions2-method.md) może wyzwolić wyrzucanie elementów bezużytecznych, natomiast [Metoda ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) nie będzie.</span><span class="sxs-lookup"><span data-stu-id="0da1e-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="0da1e-114">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="0da1e-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0da1e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0da1e-115">Requirements</span></span>  
 <span data-ttu-id="0da1e-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0da1e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0da1e-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0da1e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0da1e-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0da1e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0da1e-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0da1e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da1e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0da1e-120">See also</span></span>

- [<span data-ttu-id="0da1e-121">EnumJITedFunctions, metoda</span><span class="sxs-lookup"><span data-stu-id="0da1e-121">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="0da1e-122">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="0da1e-122">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="0da1e-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="0da1e-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0da1e-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="0da1e-124">Profiling</span></span>](index.md)
