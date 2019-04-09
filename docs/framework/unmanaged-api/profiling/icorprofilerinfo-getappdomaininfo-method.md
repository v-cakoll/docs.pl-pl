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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83468e13e1e028b031c31791910c4dd2d792f232
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168769"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="e2512-102">ICorProfilerInfo::GetAppDomainInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2512-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="e2512-103">Akceptuje identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2512-103">Accepts an application domain ID.</span></span> <span data-ttu-id="e2512-104">Zwraca nazwę domeny aplikacji i identyfikator procesu, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="e2512-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2512-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2512-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2512-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2512-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="e2512-107">[in] Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2512-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e2512-108">[in] Długość w znakach, z `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="e2512-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e2512-109">[out] Wskaźnik do łączna liczba znaków nazwy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2512-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="e2512-110">[out] Bufor dostarczane przez obiekt wywołujący znaku dwubajtowego.</span><span class="sxs-lookup"><span data-stu-id="e2512-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="e2512-111">Po powrocie z metody `szName` będzie zawierać nazwę domeny aplikacji pełnej lub częściowej.</span><span class="sxs-lookup"><span data-stu-id="e2512-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="e2512-112">[out] Wskaźnik do Identyfikatora procesu, który zawiera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2512-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2512-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2512-113">Remarks</span></span>  
 <span data-ttu-id="e2512-114">Po powrocie z tej metody należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby zawierała pełną nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2512-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="e2512-115">Aby to zrobić, porównaj wartość która `pcchName` wskazuje z wartością `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="e2512-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e2512-116">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większego `szName` buforu, zaktualizuj `cchName` przy użyciu nowych, większy rozmiar i Wywołaj `GetAppDomainInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="e2512-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="e2512-117">Alternatywnie, można wywołać `GetAppDomainInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="e2512-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e2512-118">Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcchName` i wywołać `GetAppDomainInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="e2512-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2512-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2512-119">Requirements</span></span>  
 <span data-ttu-id="e2512-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2512-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2512-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e2512-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2512-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2512-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e2512-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e2512-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e2512-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2512-124">See also</span></span>

- [<span data-ttu-id="e2512-125">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e2512-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e2512-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="e2512-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="e2512-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="e2512-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
