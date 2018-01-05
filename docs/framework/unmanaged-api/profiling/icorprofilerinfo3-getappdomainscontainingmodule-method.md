---
title: "ICorProfilerInfo3::GetAppDomainsContainingModule — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa0aa6620f8465154ac31586618af3fe36f3dfe4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="f3786-102">ICorProfilerInfo3::GetAppDomainsContainingModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3786-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="f3786-103">Pobiera identyfikatory domeny aplikacji, w których dany moduł został załadowany.</span><span class="sxs-lookup"><span data-stu-id="f3786-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3786-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3786-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3786-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3786-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f3786-106">[in] Identyfikator załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="f3786-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="f3786-107">[in] Rozmiar `appDomainIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f3786-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="f3786-108">[out] Wskaźnik do liczba zwróconych elementów.</span><span class="sxs-lookup"><span data-stu-id="f3786-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="f3786-109">[out] Tablica wartości Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3786-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3786-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3786-110">Remarks</span></span>  
 <span data-ttu-id="f3786-111">Metoda używa do wywołującego przydzielonych buforów.</span><span class="sxs-lookup"><span data-stu-id="f3786-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3786-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3786-112">Requirements</span></span>  
 <span data-ttu-id="f3786-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3786-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3786-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3786-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3786-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3786-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3786-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3786-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3786-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3786-117">See Also</span></span>  
 [<span data-ttu-id="f3786-118">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3786-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="f3786-119">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3786-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="f3786-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f3786-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f3786-121">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="f3786-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
