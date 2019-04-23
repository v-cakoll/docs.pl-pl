---
title: ICorProfilerInfo::GetAssemblyInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad4ebe4e1255ce13974063eef3d0a4feeb5dd92b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083060"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="11233-102">ICorProfilerInfo::GetAssemblyInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="11233-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="11233-103">Akceptuje identyfikator zestawu i zwraca nazwę zestawu i identyfikator jego manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="11233-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11233-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11233-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="11233-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11233-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="11233-106">[in] Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="11233-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="11233-107">[in] Długość w znakach, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="11233-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="11233-108">[out] Wskaźnik do znaku całkowita długość nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="11233-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="11233-109">[out] Bufor dostarczane przez obiekt wywołujący znaku dwubajtowego.</span><span class="sxs-lookup"><span data-stu-id="11233-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="11233-110">Po powrocie z tej funkcji będzie zawierać nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="11233-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="11233-111">[out] Wskaźnik do Identyfikatora domeny aplikacji, który zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="11233-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="11233-112">[out] Wskaźnik do Identyfikatora modułu manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="11233-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11233-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11233-113">Remarks</span></span>  
 <span data-ttu-id="11233-114">Po powrocie z tej metody należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby zawierać pełną nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="11233-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="11233-115">Aby to zrobić, porównaj wartość która `pcchName` wskazuje z wartością `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="11233-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="11233-116">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większego `szName` buforu, zaktualizuj `cchName` przy użyciu nowych, większy rozmiar i Wywołaj `GetAssemblyInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="11233-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="11233-117">Alternatywnie, można wywołać `GetAssemblyInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="11233-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="11233-118">Następnie można dostosować rozmiar buforu, w oparciu o wartości zwracanej w `pcchName` i wywołać `GetAssemblyInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="11233-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11233-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11233-119">Requirements</span></span>  
 <span data-ttu-id="11233-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11233-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11233-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11233-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11233-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11233-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11233-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11233-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11233-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11233-124">See also</span></span>

- [<span data-ttu-id="11233-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="11233-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="11233-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="11233-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="11233-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="11233-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
