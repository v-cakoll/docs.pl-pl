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
ms.openlocfilehash: 1e08d246136b33ffaaea91367d428e0bf2db99c1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864131"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="f3278-102">ICorProfilerInfo::GetAssemblyInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3278-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="f3278-103">Akceptuje identyfikator zestawu i zwraca nazwę zestawu oraz identyfikator modułu manifestu.</span><span class="sxs-lookup"><span data-stu-id="f3278-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3278-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3278-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3278-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3278-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="f3278-106">podczas Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="f3278-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f3278-107">podczas Długość (w znakach) `szName`.</span><span class="sxs-lookup"><span data-stu-id="f3278-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f3278-108">określoną Wskaźnik do łącznej długości znaku nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="f3278-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="f3278-109">określoną Bufor znaków udostępniany przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="f3278-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="f3278-110">Gdy funkcja zwraca, będzie zawierać nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="f3278-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="f3278-111">określoną Wskaźnik do identyfikatora domeny aplikacji, który zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="f3278-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="f3278-112">określoną Wskaźnik do identyfikatora modułu manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="f3278-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3278-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3278-113">Remarks</span></span>  
 <span data-ttu-id="f3278-114">Po powrocie tej metody należy sprawdzić, czy bufor `szName` był wystarczająco duży, aby zawierał pełną nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="f3278-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="f3278-115">W tym celu należy porównać wartość, która `pcchName` wskazuje na wartość parametru `cchName`.</span><span class="sxs-lookup"><span data-stu-id="f3278-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="f3278-116">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy bufor `szName`, zaktualizuj `cchName` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetAssemblyInfo`.</span><span class="sxs-lookup"><span data-stu-id="f3278-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="f3278-117">Alternatywnie można najpierw wywołać `GetAssemblyInfo` z buforem `szName` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="f3278-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f3278-118">Następnie można dostosować rozmiar buforu na podstawie wartości zwróconej w `pcchName` i ponownie wywołać `GetAssemblyInfo`.</span><span class="sxs-lookup"><span data-stu-id="f3278-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3278-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3278-119">Requirements</span></span>  
 <span data-ttu-id="f3278-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3278-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3278-121">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f3278-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3278-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3278-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3278-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3278-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3278-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3278-124">See also</span></span>

- [<span data-ttu-id="f3278-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3278-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f3278-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f3278-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f3278-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="f3278-127">Profiling</span></span>](index.md)
