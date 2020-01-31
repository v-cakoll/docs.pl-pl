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
ms.openlocfilehash: 56221c6b3ac40595e999f2a2a3739f023441c46d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862415"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="8f622-102">ICorProfilerInfo3::GetAppDomainsContainingModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f622-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="8f622-103">Pobiera identyfikatory domen aplikacji, w których dany moduł został załadowany.</span><span class="sxs-lookup"><span data-stu-id="8f622-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f622-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f622-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f622-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f622-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="8f622-106">podczas Identyfikator załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="8f622-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="8f622-107">podczas Rozmiar tablicy `appDomainIds`.</span><span class="sxs-lookup"><span data-stu-id="8f622-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="8f622-108">określoną Wskaźnik do łącznej liczby zwróconych elementów.</span><span class="sxs-lookup"><span data-stu-id="8f622-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="8f622-109">określoną Tablica wartości identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f622-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f622-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f622-110">Remarks</span></span>  
 <span data-ttu-id="8f622-111">Metoda używa buforów przyznanych przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8f622-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f622-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f622-112">Requirements</span></span>  
 <span data-ttu-id="8f622-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f622-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f622-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8f622-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f622-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8f622-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f622-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f622-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f622-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f622-117">See also</span></span>

- [<span data-ttu-id="8f622-118">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f622-118">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="8f622-119">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f622-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="8f622-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="8f622-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8f622-121">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="8f622-121">Profiling</span></span>](index.md)
