---
title: "ICorProfilerInfo3::GetModuleInfo2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetModuleInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b891f55ab79d32814f44eabf50343aa113b0835
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="d83d5-102">ICorProfilerInfo3::GetModuleInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="d83d5-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="d83d5-103">Podany identyfikator modułu zwraca nazwę modułu, identyfikator elementu nadrzędnego modułu zestawu i maski, który opisuje właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="d83d5-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d83d5-104">Syntax</span></span>  
  
```  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d83d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d83d5-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="d83d5-106">[in] Identyfikator modułu, dla których zostaną pobrane informacje.</span><span class="sxs-lookup"><span data-stu-id="d83d5-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="d83d5-107">[out] Adres podstawowy, w którym ładowany jest moduł.</span><span class="sxs-lookup"><span data-stu-id="d83d5-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d83d5-108">[in] Długość w znakach, z `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="d83d5-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d83d5-109">[out] Wskaźnik do całkowita liczba znaków nazwy pliku modułu, która jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="d83d5-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="d83d5-110">[out] Bufor dostarczane przez obiekt wywołujący znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="d83d5-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="d83d5-111">Gdy metoda zwróci wartość, ten bufor zawiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="d83d5-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="d83d5-112">[out] Wskaźnik do Identyfikatora zestawu nadrzędnego modułu.</span><span class="sxs-lookup"><span data-stu-id="d83d5-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="d83d5-113">[out] Maska bitowa wartości z [cor_prf_module_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) wyliczenia, która określa właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="d83d5-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d83d5-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d83d5-114">Remarks</span></span>  
 <span data-ttu-id="d83d5-115">Dynamiczne modułów `szName` parametru jest nazwa metadanych modułu, a adres podstawowy jest 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="d83d5-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="d83d5-116">Nazwa metadanych jest wartość kolumny z nazwami z tabeli modułu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="d83d5-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="d83d5-117">To jest również udostępniany jako <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> właściwości do kodu zarządzanego i jako `szName` parametr [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) metodę metadanych niezarządzanego kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="d83d5-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="d83d5-118">Mimo że `GetModuleInfo2` może zostać wywołana metoda, jak modułu o identyfikatorze istnieje, identyfikator zestawu nadrzędnego nie będą dostępne do momentu otrzymania przez profiler [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d83d5-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="d83d5-119">Gdy `GetModuleInfo2` zwróci wartość, należy sprawdzić, czy `szName` bufor był wystarczająco duży, aby zawierała Pełna nazwa pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="d83d5-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="d83d5-120">W tym celu należy porównać wartości który `pcchName` wskazuje wartość `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="d83d5-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="d83d5-121">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy `szName` buforu, zaktualizuj `cchName` z nowej, większy rozmiar i wywołanie `GetModuleInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="d83d5-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="d83d5-122">Alternatywnie można wywołać `GetModuleInfo2` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="d83d5-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d83d5-123">Rozmiar buforu można następnie ustawić wartość zwracana w `pcchName` i Wywołaj `GetModuleInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="d83d5-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d83d5-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d83d5-124">Requirements</span></span>  
 <span data-ttu-id="d83d5-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d83d5-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d83d5-126">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d83d5-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d83d5-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d83d5-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d83d5-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d83d5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83d5-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d83d5-129">See Also</span></span>  
 [<span data-ttu-id="d83d5-130">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="d83d5-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="d83d5-131">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d83d5-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d83d5-132">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="d83d5-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
