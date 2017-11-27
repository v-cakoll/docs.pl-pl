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
ms.openlocfilehash: ff9f63fc004d7249b571d980561171464e74b9a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="147ff-102">ICorProfilerInfo3::GetAppDomainsContainingModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="147ff-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="147ff-103">Pobiera identyfikatory domeny aplikacji, w których dany moduł został załadowany.</span><span class="sxs-lookup"><span data-stu-id="147ff-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="147ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="147ff-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="147ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="147ff-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="147ff-106">[in] Identyfikator załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="147ff-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="147ff-107">[in] Rozmiar `appDomainIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="147ff-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="147ff-108">[out] Wskaźnik do liczba zwróconych elementów.</span><span class="sxs-lookup"><span data-stu-id="147ff-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="147ff-109">[out] Tablica wartości Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="147ff-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="147ff-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="147ff-110">Remarks</span></span>  
 <span data-ttu-id="147ff-111">Metoda używa do wywołującego przydzielonych buforów.</span><span class="sxs-lookup"><span data-stu-id="147ff-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="147ff-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="147ff-112">Requirements</span></span>  
 <span data-ttu-id="147ff-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="147ff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="147ff-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="147ff-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="147ff-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="147ff-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="147ff-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="147ff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147ff-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="147ff-117">See Also</span></span>  
 [<span data-ttu-id="147ff-118">ICorProfilerFunctionEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="147ff-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="147ff-119">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="147ff-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="147ff-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="147ff-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="147ff-121">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="147ff-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
