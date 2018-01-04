---
title: "ICorProfilerInfo::GetAssemblyInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAssemblyInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3ac5bd35d12bb4c9d9308dcdff3e1fb8385f6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="9606f-102">ICorProfilerInfo::GetAssemblyInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="9606f-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="9606f-103">Akceptuje identyfikator zestawu i zwraca nazwę zestawu i identyfikator jej manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="9606f-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9606f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9606f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9606f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9606f-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="9606f-106">[in] Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="9606f-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9606f-107">[in] Długość w znakach, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="9606f-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9606f-108">[out] Wskaźnik do znaku całkowita długość nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="9606f-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="9606f-109">[out] Bufor dostarczane przez obiekt wywołujący znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="9606f-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="9606f-110">Po powrocie z funkcji, będzie zawierać nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="9606f-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="9606f-111">[out] Wskaźnik do identyfikator domeny aplikacji, która zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="9606f-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="9606f-112">[out] Wskaźnik do Identyfikatora modułu manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="9606f-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9606f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9606f-113">Remarks</span></span>  
 <span data-ttu-id="9606f-114">Po powrocie z tej metody, należy sprawdzić, czy `szName` bufor był wystarczająco duży, aby zawierać pełnej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="9606f-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="9606f-115">W tym celu należy porównać wartości który `pcchName` wskazuje wartość `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="9606f-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="9606f-116">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy `szName` buforu, zaktualizuj `cchName` z nowej, większy rozmiar i wywołanie `GetAssemblyInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="9606f-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="9606f-117">Alternatywnie można wywołać `GetAssemblyInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="9606f-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9606f-118">Następnie można dostosować rozmiar buforu, na podstawie wartości zwracane w `pcchName` i Wywołaj `GetAssemblyInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="9606f-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9606f-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9606f-119">Requirements</span></span>  
 <span data-ttu-id="9606f-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9606f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9606f-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9606f-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9606f-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9606f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9606f-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9606f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9606f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9606f-124">See Also</span></span>  
 [<span data-ttu-id="9606f-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="9606f-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="9606f-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="9606f-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="9606f-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="9606f-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
