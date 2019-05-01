---
title: ICorProfilerInfo3::GetModuleInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fadca931ca4a57c83257f24e34e847870c9f493
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040966"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="3a8d8-102">ICorProfilerInfo3::GetModuleInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a8d8-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="3a8d8-103">Podany identyfikator modułu zwraca nazwę pliku modułu, identyfikator elementu nadrzędnego modułu zestawu i masek bitowych, który opisuje właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a8d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a8d8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3a8d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a8d8-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="3a8d8-106">[in] Identyfikator modułu, dla którego będą pobierane informacje.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="3a8d8-107">[out] Adres podstawowy, ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3a8d8-108">[in] Długość w znakach, z `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3a8d8-109">[out] Wskaźnik do łączna liczba znaków nazwy pliku modułu, który jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="3a8d8-110">[out] Bufor dostarczane przez obiekt wywołujący znaku dwubajtowego.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="3a8d8-111">Po powrocie z metody tego buforu zawiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="3a8d8-112">[out] Wskaźnik do Identyfikatora modułu nadrzędnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="3a8d8-113">[out] Maska bitów wartości z [cor_prf_module_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) wyliczenie, które umożliwia określenie właściwości modułu.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a8d8-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a8d8-114">Remarks</span></span>  
 <span data-ttu-id="3a8d8-115">Dla modułów dynamicznych `szName` parametr jest nazwa metadane modułu, a adres podstawowy ma wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="3a8d8-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="3a8d8-116">Nazwa metadanych jest wartością w kolumnie Nazwa z tabeli modułu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="3a8d8-117">Jest to również widoczne jako <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> właściwości z kodem zarządzanym i jako `szName` parametru [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) metoda metadanych niezarządzanego kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="3a8d8-118">Mimo że `GetModuleInfo2` można wywołać metody, jak istnieje identyfikator modułu, identyfikator zestawu nadrzędnego nie będą dostępne, dopóki program profilujący nie otrzyma [icorprofilercallback::moduleattachedtoassembly —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="3a8d8-119">Gdy `GetModuleInfo2` zwróci wartość, należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby zawierały nazwę pełnego pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="3a8d8-120">Aby to zrobić, porównaj wartość która `pcchName` wskazuje z wartością `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="3a8d8-121">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większego `szName` buforu, zaktualizuj `cchName` przy użyciu nowych, większy rozmiar i Wywołaj `GetModuleInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="3a8d8-122">Alternatywnie, można wywołać `GetModuleInfo2` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="3a8d8-123">Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcchName` i wywołać `GetModuleInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="3a8d8-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a8d8-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a8d8-124">Requirements</span></span>  
 <span data-ttu-id="3a8d8-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a8d8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a8d8-126">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a8d8-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a8d8-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a8d8-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a8d8-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a8d8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a8d8-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a8d8-129">See also</span></span>

- [<span data-ttu-id="3a8d8-130">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a8d8-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="3a8d8-131">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3a8d8-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="3a8d8-132">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="3a8d8-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
