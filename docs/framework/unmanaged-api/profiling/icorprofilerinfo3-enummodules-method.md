---
title: ICorProfilerInfo3::EnumModules — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 0bb2ba56ed93af7861e53d683a0a777107578a6b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449755"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="a27e4-102">ICorProfilerInfo3::EnumModules — Metoda</span><span class="sxs-lookup"><span data-stu-id="a27e4-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="a27e4-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span><span class="sxs-lookup"><span data-stu-id="a27e4-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a27e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a27e4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a27e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a27e4-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a27e4-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="a27e4-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a27e4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a27e4-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a27e4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a27e4-108">Requirements</span></span>  
 <span data-ttu-id="a27e4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a27e4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a27e4-110">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a27e4-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a27e4-111">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a27e4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a27e4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a27e4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27e4-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a27e4-113">See also</span></span>

- [<span data-ttu-id="a27e4-114">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a27e4-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="a27e4-115">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="a27e4-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a27e4-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a27e4-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a27e4-117">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="a27e4-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
