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
ms.workload: dotnet
ms.openlocfilehash: 325db939c692a5dc7740e6cf813644ebffe9fc12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 — Metoda
Podany identyfikator modułu zwraca nazwę modułu, identyfikator elementu nadrzędnego modułu zestawu i maski, który opisuje właściwości modułu.  
  
## <a name="syntax"></a>Składnia  
  
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
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, dla których zostaną pobrane informacje.  
  
 `ppBaseLoadAddress`  
 [out] Adres podstawowy, w którym ładowany jest moduł.  
  
 `cchName`  
 [in] Długość w znakach, z `szName` buforze.  
  
 `pcchName`  
 [out] Wskaźnik do całkowita liczba znaków nazwy pliku modułu, która jest zwracana.  
  
 `szName`  
 [out] Bufor dostarczane przez obiekt wywołujący znaków dwubajtowych. Gdy metoda zwróci wartość, ten bufor zawiera nazwę pliku modułu.  
  
 `pAssemblyId`  
 [out] Wskaźnik do Identyfikatora zestawu nadrzędnego modułu.  
  
 `pdwModuleFlags`  
 [out] Maska bitowa wartości z [cor_prf_module_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) wyliczenia, która określa właściwości modułu.  
  
## <a name="remarks"></a>Uwagi  
 Dynamiczne modułów `szName` parametru jest nazwa metadanych modułu, a adres podstawowy jest 0 (zero). Nazwa metadanych jest wartość kolumny z nazwami z tabeli modułu w metadanych. To jest również udostępniany jako <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> właściwości do kodu zarządzanego i jako `szName` parametr [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) metodę metadanych niezarządzanego kodu klienta.  
  
 Mimo że `GetModuleInfo2` może zostać wywołana metoda, jak modułu o identyfikatorze istnieje, identyfikator zestawu nadrzędnego nie będą dostępne do momentu otrzymania przez profiler [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotnego.  
  
 Gdy `GetModuleInfo2` zwróci wartość, należy sprawdzić, czy `szName` bufor był wystarczająco duży, aby zawierała Pełna nazwa pliku modułu. W tym celu należy porównać wartości który `pcchName` wskazuje wartość `cchName` parametru. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy `szName` buforu, zaktualizuj `cchName` z nowej, większy rozmiar i wywołanie `GetModuleInfo2` ponownie.  
  
 Alternatywnie można wywołać `GetModuleInfo2` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne. Rozmiar buforu można następnie ustawić wartość zwracana w `pcchName` i Wywołaj `GetModuleInfo2` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
