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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5658ac87c7a938381639442216df03853f02998
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195790"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="45a9a-102">ICorProfilerInfo3::GetAppDomainsContainingModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="45a9a-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="45a9a-103">Pobiera identyfikatory domen aplikacji, w których dany moduł został załadowany.</span><span class="sxs-lookup"><span data-stu-id="45a9a-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45a9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45a9a-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45a9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45a9a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="45a9a-106">[in] Identyfikator załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="45a9a-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="45a9a-107">[in] Rozmiar `appDomainIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="45a9a-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="45a9a-108">[out] Wskaźnik do całkowitą liczbę zwróconych elementów.</span><span class="sxs-lookup"><span data-stu-id="45a9a-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="45a9a-109">[out] Tablica wartości Identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45a9a-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45a9a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45a9a-110">Remarks</span></span>  
 <span data-ttu-id="45a9a-111">Metoda używa obiektu wywołującego przydzielone buforów.</span><span class="sxs-lookup"><span data-stu-id="45a9a-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45a9a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45a9a-112">Requirements</span></span>  
 <span data-ttu-id="45a9a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45a9a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45a9a-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45a9a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45a9a-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45a9a-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="45a9a-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="45a9a-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45a9a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45a9a-117">See also</span></span>

- [<span data-ttu-id="45a9a-118">ICorProfilerFunctionEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="45a9a-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="45a9a-119">ICorProfilerInfo3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="45a9a-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="45a9a-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="45a9a-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="45a9a-121">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="45a9a-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
