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
ms.openlocfilehash: 120c31b61734cfb4cb0048489632bc0848a9430b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782178"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="f27a3-102">ICorProfilerInfo3::GetAppDomainsContainingModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="f27a3-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="f27a3-103">Pobiera identyfikatory domen aplikacji, w których dany moduł został załadowany.</span><span class="sxs-lookup"><span data-stu-id="f27a3-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f27a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f27a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f27a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f27a3-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f27a3-106">[in] Identyfikator załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="f27a3-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="f27a3-107">[in] Rozmiar `appDomainIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f27a3-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="f27a3-108">[out] Wskaźnik do całkowitą liczbę zwróconych elementów.</span><span class="sxs-lookup"><span data-stu-id="f27a3-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="f27a3-109">[out] Tablica wartości Identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f27a3-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f27a3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f27a3-110">Remarks</span></span>  
 <span data-ttu-id="f27a3-111">Metoda używa obiektu wywołującego przydzielone buforów.</span><span class="sxs-lookup"><span data-stu-id="f27a3-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f27a3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f27a3-112">Requirements</span></span>  
 <span data-ttu-id="f27a3-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f27a3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f27a3-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f27a3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f27a3-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f27a3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f27a3-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f27a3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f27a3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f27a3-117">See also</span></span>

- [<span data-ttu-id="f27a3-118">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="f27a3-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="f27a3-119">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="f27a3-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f27a3-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f27a3-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f27a3-121">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="f27a3-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
