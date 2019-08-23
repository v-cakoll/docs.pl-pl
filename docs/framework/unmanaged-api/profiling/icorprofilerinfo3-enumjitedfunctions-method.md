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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ceb1d22500f73a29ffdfa6f16907478628358c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969393"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="17a63-102">ICorProfilerInfo3::EnumJITedFunctions — Metoda</span><span class="sxs-lookup"><span data-stu-id="17a63-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="17a63-103">Zwraca moduł wyliczający dla wszystkich funkcji, które zostały poprzednio skompilowane JIT.</span><span class="sxs-lookup"><span data-stu-id="17a63-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17a63-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17a63-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17a63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17a63-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="17a63-106">określoną Wskaźnik do modułu wyliczającego [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="17a63-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17a63-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17a63-107">Remarks</span></span>  
 <span data-ttu-id="17a63-108">Ta metoda może nakładać `JITCompilation` się na wywołania zwrotne, takie jak Metoda [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="17a63-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="17a63-109">Moduł wyliczający zwrócony przez tę metodę nie zawiera funkcji ładowanych z obrazów natywnych generowanych za pomocą programu Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="17a63-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17a63-110">Zwrócone Wyliczenie zawiera tylko wartość "0" dla wartości `COR_PRF_FUNCTION::reJitId` pola.</span><span class="sxs-lookup"><span data-stu-id="17a63-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="17a63-111">Jeśli wymagane są prawidłowe `COR_PRF_FUNCTION::reJitId` wartości, należy użyć metody [ICorProfilerInfo4:: EnumJITedFunctions2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="17a63-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17a63-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17a63-112">Requirements</span></span>  
 <span data-ttu-id="17a63-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17a63-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17a63-114">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="17a63-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17a63-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17a63-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17a63-116">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17a63-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a63-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17a63-117">See also</span></span>

- [<span data-ttu-id="17a63-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="17a63-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="17a63-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="17a63-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="17a63-120">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="17a63-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
