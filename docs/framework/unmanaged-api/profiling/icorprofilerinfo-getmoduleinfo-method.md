---
title: ICorProfilerInfo::GetModuleInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ceca2133068d3ed011b9499024d127a3dd9279ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782769"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="91e47-102">ICorProfilerInfo::GetModuleInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="91e47-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="91e47-103">Podany identyfikator modułu zwraca nazwę pliku modułu i identyfikator zestawu nadrzędnego modułu.</span><span class="sxs-lookup"><span data-stu-id="91e47-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91e47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91e47-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91e47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91e47-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="91e47-106">[in] Identyfikator modułu, dla którego będą pobierane informacje.</span><span class="sxs-lookup"><span data-stu-id="91e47-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="91e47-107">[out] Adres podstawowy, ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="91e47-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="91e47-108">[in] Długość w znakach, z `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="91e47-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="91e47-109">[out] Wskaźnik do łączna liczba znaków nazwy pliku modułu, który jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="91e47-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="91e47-110">[out] Bufor dostarczane przez obiekt wywołujący znaku dwubajtowego.</span><span class="sxs-lookup"><span data-stu-id="91e47-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="91e47-111">Po powrocie z metody tego buforu zawiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="91e47-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="91e47-112">[out] Wskaźnik do Identyfikatora modułu nadrzędnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="91e47-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91e47-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91e47-113">Remarks</span></span>  
 <span data-ttu-id="91e47-114">Dla modułów dynamicznych `szName` parametr jest pustym ciągiem, a adres podstawowy ma wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="91e47-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="91e47-115">Mimo że `GetModuleInfo` można wywołać metody, jak istnieje identyfikator modułu, identyfikator zestawu nadrzędnego nie będą dostępne, dopóki program profilujący nie otrzyma [icorprofilercallback::moduleattachedtoassembly —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="91e47-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="91e47-116">Gdy `GetModuleInfo` zwróci wartość, należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby zawierały nazwę pełnego pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="91e47-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="91e47-117">Aby to zrobić, porównaj wartość która `pcchName` wskazuje z wartością `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="91e47-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="91e47-118">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większego `szName` buforu, zaktualizuj `cchName` przy użyciu nowych, większy rozmiar i Wywołaj `GetModuleInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="91e47-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="91e47-119">Alternatywnie, można wywołać `GetModuleInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="91e47-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="91e47-120">Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcchName` i wywołać `GetModuleInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="91e47-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91e47-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91e47-121">Requirements</span></span>  
 <span data-ttu-id="91e47-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91e47-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91e47-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91e47-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91e47-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91e47-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91e47-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91e47-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e47-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91e47-126">See also</span></span>

- [<span data-ttu-id="91e47-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="91e47-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="91e47-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="91e47-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="91e47-129">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="91e47-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [<span data-ttu-id="91e47-130">GetModuleInfo2, metoda</span><span class="sxs-lookup"><span data-stu-id="91e47-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
