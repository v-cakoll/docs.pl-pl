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
ms.openlocfilehash: 7525d107fec7229d9b86eee63bde2aaf2d701b1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190304"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="95328-102">ICorProfilerInfo3::EnumJITedFunctions — Metoda</span><span class="sxs-lookup"><span data-stu-id="95328-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="95328-103">Zwraca moduł wyliczający dla wszystkich funkcji, które były wcześniej skompilowany JIT.</span><span class="sxs-lookup"><span data-stu-id="95328-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95328-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95328-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95328-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95328-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="95328-106">[out] Wskaźnik do [icorprofilerfunctionenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="95328-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95328-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95328-107">Remarks</span></span>  
 <span data-ttu-id="95328-108">Ta metoda może pokrywać się z `JITCompilation` wywołań zwrotnych, takie jak [icorprofilercallback::jitcompilationstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="95328-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="95328-109">Moduł wyliczający zwracanego przez tę metodę nie zawiera funkcje, które są ładowane z obrazy natywne generowane przez program Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="95328-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95328-110">Zwrócone wyliczenia zawiera tylko "0" dla wartości `COR_PRF_FUNCTION::reJitId` pola.</span><span class="sxs-lookup"><span data-stu-id="95328-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="95328-111">W razie potrzeby prawidłowe `COR_PRF_FUNCTION::reJitId` wartości, należy użyć [icorprofilerinfo4::enumjitedfunctions2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="95328-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95328-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95328-112">Requirements</span></span>  
 <span data-ttu-id="95328-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95328-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95328-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95328-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95328-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95328-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95328-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95328-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95328-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95328-117">See also</span></span>

- [<span data-ttu-id="95328-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="95328-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="95328-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="95328-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="95328-120">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="95328-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
