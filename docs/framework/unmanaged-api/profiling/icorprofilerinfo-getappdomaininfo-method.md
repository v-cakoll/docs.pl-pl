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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168769"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="a12f9-102">ICorProfilerInfo::GetAppDomainInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="a12f9-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="a12f9-103">Akceptuje identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a12f9-103">Accepts an application domain ID.</span></span> <span data-ttu-id="a12f9-104">Zwraca nazwę domeny aplikacji i identyfikator procesu, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="a12f9-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a12f9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a12f9-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a12f9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a12f9-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="a12f9-107">[in] Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a12f9-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a12f9-108">[in] Długość w znakach, z `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="a12f9-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a12f9-109">[out] Wskaźnik do łączna liczba znaków nazwy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a12f9-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="a12f9-110">[out] Bufor dostarczane przez obiekt wywołujący znaku dwubajtowego.</span><span class="sxs-lookup"><span data-stu-id="a12f9-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="a12f9-111">Po powrocie z metody `szName` będzie zawierać nazwę domeny aplikacji pełnej lub częściowej.</span><span class="sxs-lookup"><span data-stu-id="a12f9-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="a12f9-112">[out] Wskaźnik do Identyfikatora procesu, który zawiera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a12f9-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a12f9-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a12f9-113">Remarks</span></span>  
 <span data-ttu-id="a12f9-114">Po powrocie z tej metody należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby zawierała pełną nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a12f9-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="a12f9-115">Aby to zrobić, porównaj wartość która `pcchName` wskazuje z wartością `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="a12f9-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="a12f9-116">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większego `szName` buforu, zaktualizuj `cchName` przy użyciu nowych, większy rozmiar i Wywołaj `GetAppDomainInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="a12f9-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="a12f9-117">Alternatywnie, można wywołać `GetAppDomainInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="a12f9-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a12f9-118">Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcchName` i wywołać `GetAppDomainInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="a12f9-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a12f9-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a12f9-119">Requirements</span></span>  
 <span data-ttu-id="a12f9-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a12f9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a12f9-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a12f9-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a12f9-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a12f9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a12f9-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a12f9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a12f9-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a12f9-124">See also</span></span>

- [<span data-ttu-id="a12f9-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a12f9-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="a12f9-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a12f9-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a12f9-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="a12f9-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
