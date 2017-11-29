---
title: "ICorProfilerInfo::GetModuleInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 23dc0208b4537530f18c2c282fbe8c3495ba301f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="1637d-102">ICorProfilerInfo::GetModuleInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="1637d-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="1637d-103">Podany identyfikator modułu zwraca nazwę modułu i identyfikator zestawu nadrzędnego modułu.</span><span class="sxs-lookup"><span data-stu-id="1637d-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1637d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1637d-104">Syntax</span></span>  
  
```  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1637d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1637d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1637d-106">[in] Identyfikator modułu, dla których zostaną pobrane informacje.</span><span class="sxs-lookup"><span data-stu-id="1637d-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="1637d-107">[out] Adres podstawowy, w którym ładowany jest moduł.</span><span class="sxs-lookup"><span data-stu-id="1637d-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1637d-108">[in] Długość w znakach, z `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="1637d-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1637d-109">[out] Wskaźnik do całkowita liczba znaków nazwy pliku modułu, która jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="1637d-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="1637d-110">[out] Bufor dostarczane przez obiekt wywołujący znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="1637d-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="1637d-111">Gdy metoda zwróci wartość, ten bufor zawiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="1637d-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="1637d-112">[out] Wskaźnik do Identyfikatora zestawu nadrzędnego modułu.</span><span class="sxs-lookup"><span data-stu-id="1637d-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1637d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1637d-113">Remarks</span></span>  
 <span data-ttu-id="1637d-114">Dynamiczne modułów `szName` parametr jest pustym ciągiem, a adres podstawowy jest 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="1637d-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="1637d-115">Mimo że `GetModuleInfo` może zostać wywołana metoda, jak modułu o identyfikatorze istnieje, identyfikator zestawu nadrzędnego nie będą dostępne do momentu otrzymania przez profiler [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1637d-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="1637d-116">Gdy `GetModuleInfo` zwróci wartość, należy sprawdzić, czy `szName` bufor był wystarczająco duży, aby zawierała Pełna nazwa pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="1637d-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="1637d-117">W tym celu należy porównać wartości który `pcchName` wskazuje wartość `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="1637d-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="1637d-118">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy `szName` buforu, zaktualizuj `cchName` z nowej, większy rozmiar i wywołanie `GetModuleInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="1637d-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="1637d-119">Alternatywnie można wywołać `GetModuleInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="1637d-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="1637d-120">Rozmiar buforu można następnie ustawić wartość zwracana w `pcchName` i Wywołaj `GetModuleInfo` ponownie.</span><span class="sxs-lookup"><span data-stu-id="1637d-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1637d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1637d-121">Requirements</span></span>  
 <span data-ttu-id="1637d-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1637d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1637d-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1637d-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1637d-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1637d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1637d-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1637d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1637d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1637d-126">See Also</span></span>  
 [<span data-ttu-id="1637d-127">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="1637d-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="1637d-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="1637d-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="1637d-129">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="1637d-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [<span data-ttu-id="1637d-130">GetModuleInfo2 — metoda</span><span class="sxs-lookup"><span data-stu-id="1637d-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
