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
ms.openlocfilehash: af83fbeb64ad33910b45d49f987ffae130a2179e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="3b621-102">ICorProfilerInfo::GetAppDomainInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b621-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="3b621-103">Akceptuje identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b621-103">Accepts an application domain ID.</span></span> <span data-ttu-id="3b621-104">Zwraca nazwę domeny aplikacji i identyfikator procesu, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="3b621-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b621-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b621-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b621-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b621-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="3b621-107">[in] Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b621-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3b621-108">[in] Długość w znakach, z `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="3b621-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3b621-109">[out] Wskaźnik do całkowita liczba znaków nazwy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b621-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="3b621-110">[out] Bufor dostarczane przez obiekt wywołujący znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="3b621-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="3b621-111">Gdy metoda zwróci wartość, `szName` będzie zawierać nazwę domeny aplikacji pełnej lub częściowej.</span><span class="sxs-lookup"><span data-stu-id="3b621-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="3b621-112">[out] Wskaźnik do Identyfikatora procesu, który zawiera domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b621-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b621-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b621-113">Remarks</span></span>  
 <span data-ttu-id="3b621-114">Po powrocie z tej metody, należy sprawdzić, czy `szName` bufor był wystarczająco duży, aby zawierała pełną nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b621-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="3b621-115">W tym celu należy porównać wartości który `pcchName` wskazuje wartość `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="3b621-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="3b621-116">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy `szName` buforu, zaktualizuj `cchName` z nowej, większy rozmiar i wywołanie `GetAppDomainInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="3b621-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="3b621-117">Alternatywnie można wywołać `GetAppDomainInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="3b621-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="3b621-118">Rozmiar buforu można następnie ustawić wartość zwracana w `pcchName` i Wywołaj `GetAppDomainInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="3b621-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b621-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b621-119">Requirements</span></span>  
 <span data-ttu-id="3b621-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b621-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b621-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b621-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b621-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b621-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b621-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b621-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b621-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b621-124">See Also</span></span>  
 [<span data-ttu-id="3b621-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b621-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="3b621-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3b621-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="3b621-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="3b621-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
