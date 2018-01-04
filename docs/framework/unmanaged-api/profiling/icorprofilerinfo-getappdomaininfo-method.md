---
title: "ICorProfilerInfo::GetAppDomainInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAppDomainInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9f7f4db595966293e87b5b115437df1bec56c00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="7bf5e-102">ICorProfilerInfo::GetAppDomainInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="7bf5e-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="7bf5e-103">Akceptuje identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-103">Accepts an application domain ID.</span></span> <span data-ttu-id="7bf5e-104">Zwraca nazwę domeny aplikacji i identyfikator procesu, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf5e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bf5e-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bf5e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bf5e-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="7bf5e-107">[in] Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7bf5e-108">[in] Długość w znakach, z `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7bf5e-109">[out] Wskaźnik do całkowita liczba znaków nazwy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="7bf5e-110">[out] Bufor dostarczane przez obiekt wywołujący znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="7bf5e-111">Gdy metoda zwróci wartość, `szName` będzie zawierać nazwę domeny aplikacji pełnej lub częściowej.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="7bf5e-112">[out] Wskaźnik do Identyfikatora procesu, który zawiera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bf5e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bf5e-113">Remarks</span></span>  
 <span data-ttu-id="7bf5e-114">Po powrocie z tej metody, należy sprawdzić, czy `szName` bufor był wystarczająco duży, aby zawierała pełną nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="7bf5e-115">W tym celu należy porównać wartości który `pcchName` wskazuje wartość `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="7bf5e-116">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy `szName` buforu, zaktualizuj `cchName` z nowej, większy rozmiar i wywołanie `GetAppDomainInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="7bf5e-117">Alternatywnie można wywołać `GetAppDomainInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7bf5e-118">Rozmiar buforu można następnie ustawić wartość zwracana w `pcchName` i Wywołaj `GetAppDomainInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="7bf5e-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf5e-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7bf5e-119">Requirements</span></span>  
 <span data-ttu-id="7bf5e-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bf5e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf5e-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7bf5e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7bf5e-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bf5e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bf5e-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf5e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf5e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bf5e-124">See Also</span></span>  
 [<span data-ttu-id="7bf5e-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7bf5e-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="7bf5e-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="7bf5e-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="7bf5e-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="7bf5e-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
