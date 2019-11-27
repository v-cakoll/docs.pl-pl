---
title: ICorProfilerInfo3::EnumJITedFunctions — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: d21a793a88cd7561da9acb7daab2dc3bfecf0fc7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449760"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="30fc9-102">ICorProfilerInfo3::EnumJITedFunctions — Metoda</span><span class="sxs-lookup"><span data-stu-id="30fc9-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="30fc9-103">Zwraca moduł wyliczający dla wszystkich funkcji, które zostały poprzednio skompilowane JIT.</span><span class="sxs-lookup"><span data-stu-id="30fc9-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30fc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="30fc9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30fc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30fc9-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="30fc9-106">określoną Wskaźnik do modułu wyliczającego [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="30fc9-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30fc9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30fc9-107">Remarks</span></span>  
 <span data-ttu-id="30fc9-108">Ta metoda może nakładać się na wywołania zwrotne `JITCompilation`, takie jak Metoda [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="30fc9-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="30fc9-109">Moduł wyliczający zwrócony przez tę metodę nie zawiera funkcji ładowanych z obrazów natywnych generowanych za pomocą programu Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="30fc9-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30fc9-110">Zwrócone Wyliczenie zawiera tylko wartość "0" dla wartości pola `COR_PRF_FUNCTION::reJitId`.</span><span class="sxs-lookup"><span data-stu-id="30fc9-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="30fc9-111">Jeśli wymagane są prawidłowe wartości `COR_PRF_FUNCTION::reJitId`, użyj metody [ICorProfilerInfo4:: EnumJITedFunctions2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="30fc9-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30fc9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30fc9-112">Requirements</span></span>  
 <span data-ttu-id="30fc9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30fc9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30fc9-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="30fc9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30fc9-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="30fc9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30fc9-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30fc9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30fc9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30fc9-117">See also</span></span>

- [<span data-ttu-id="30fc9-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="30fc9-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="30fc9-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="30fc9-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="30fc9-120">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="30fc9-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
