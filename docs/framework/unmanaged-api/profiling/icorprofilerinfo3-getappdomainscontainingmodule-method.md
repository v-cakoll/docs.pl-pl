---
title: ICorProfilerInfo3::GetAppDomainsContainingModule — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
ms.openlocfilehash: 93c042d760eab4bcb1846701ad92ac38cb473c69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449735"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="c1889-102">ICorProfilerInfo3::GetAppDomainsContainingModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1889-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="c1889-103">Gets the identifiers of the application domains in which the given module has been loaded.</span><span class="sxs-lookup"><span data-stu-id="c1889-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1889-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1889-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1889-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1889-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c1889-106">[in] The ID of the loaded module.</span><span class="sxs-lookup"><span data-stu-id="c1889-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="c1889-107">[in] The size of the `appDomainIds` array.</span><span class="sxs-lookup"><span data-stu-id="c1889-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="c1889-108">[out] A pointer to the total number of returned elements.</span><span class="sxs-lookup"><span data-stu-id="c1889-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="c1889-109">[out] An array of application domain ID values.</span><span class="sxs-lookup"><span data-stu-id="c1889-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1889-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1889-110">Remarks</span></span>  
 <span data-ttu-id="c1889-111">The method uses caller allocated buffers.</span><span class="sxs-lookup"><span data-stu-id="c1889-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1889-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1889-112">Requirements</span></span>  
 <span data-ttu-id="c1889-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1889-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1889-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1889-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1889-115">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1889-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1889-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1889-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1889-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1889-117">See also</span></span>

- [<span data-ttu-id="c1889-118">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1889-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="c1889-119">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1889-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c1889-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c1889-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="c1889-121">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="c1889-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
