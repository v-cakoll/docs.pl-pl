---
title: ICorProfilerInfo::GetAppDomainInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 8c13ce443037d706f9eba49760ba76f47c5a6538
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448173"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="35080-102">ICorProfilerInfo::GetAppDomainInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="35080-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="35080-103">Accepts an application domain ID.</span><span class="sxs-lookup"><span data-stu-id="35080-103">Accepts an application domain ID.</span></span> <span data-ttu-id="35080-104">Returns an application domain name and the ID of the process that contains it.</span><span class="sxs-lookup"><span data-stu-id="35080-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35080-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="35080-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35080-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="35080-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="35080-107">[in] The ID of the application domain.</span><span class="sxs-lookup"><span data-stu-id="35080-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="35080-108">[in] The length, in characters, of the `szName` return buffer.</span><span class="sxs-lookup"><span data-stu-id="35080-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="35080-109">[out] A pointer to the total character length of the application domain name.</span><span class="sxs-lookup"><span data-stu-id="35080-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="35080-110">[out] A caller-provided wide character buffer.</span><span class="sxs-lookup"><span data-stu-id="35080-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="35080-111">When the method returns, `szName` will contain the full or partial application domain name.</span><span class="sxs-lookup"><span data-stu-id="35080-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="35080-112">[out] A pointer to the ID of the process that contains the application domain.</span><span class="sxs-lookup"><span data-stu-id="35080-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35080-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35080-113">Remarks</span></span>  
 <span data-ttu-id="35080-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span><span class="sxs-lookup"><span data-stu-id="35080-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="35080-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span><span class="sxs-lookup"><span data-stu-id="35080-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="35080-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span><span class="sxs-lookup"><span data-stu-id="35080-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="35080-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span><span class="sxs-lookup"><span data-stu-id="35080-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="35080-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span><span class="sxs-lookup"><span data-stu-id="35080-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35080-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35080-119">Requirements</span></span>  
 <span data-ttu-id="35080-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35080-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35080-121">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="35080-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35080-122">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35080-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35080-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35080-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35080-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35080-124">See also</span></span>

- [<span data-ttu-id="35080-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="35080-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="35080-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="35080-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="35080-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="35080-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
