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
ms.openlocfilehash: 5ead38d54d470c3f443ae5e27e4a2d045bc27c79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783034"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 — Metoda
Podany identyfikator modułu zwraca nazwę pliku modułu, identyfikator elementu nadrzędnego modułu zestawu i masek bitowych, który opisuje właściwości modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, dla którego będą pobierane informacje.  
  
 `ppBaseLoadAddress`  
 [out] Adres podstawowy, ładowania modułu.  
  
 `cchName`  
 [in] Długość w znakach, z `szName` buforze.  
  
 `pcchName`  
 [out] Wskaźnik do łączna liczba znaków nazwy pliku modułu, który jest zwracany.  
  
 `szName`  
 [out] Bufor dostarczane przez obiekt wywołujący znaku dwubajtowego. Po powrocie z metody tego buforu zawiera nazwę pliku modułu.  
  
 `pAssemblyId`  
 [out] Wskaźnik do Identyfikatora modułu nadrzędnego zestawu.  
  
 `pdwModuleFlags`  
 [out] Maska bitów wartości z [cor_prf_module_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) wyliczenie, które umożliwia określenie właściwości modułu.  
  
## <a name="remarks"></a>Uwagi  
 Dla modułów dynamicznych `szName` parametr jest nazwa metadane modułu, a adres podstawowy ma wartość 0 (zero). Nazwa metadanych jest wartością w kolumnie Nazwa z tabeli modułu w metadanych. Jest to również widoczne jako <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> właściwości z kodem zarządzanym i jako `szName` parametru [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) metoda metadanych niezarządzanego kodu klienta.  
  
 Mimo że `GetModuleInfo2` można wywołać metody, jak istnieje identyfikator modułu, identyfikator zestawu nadrzędnego nie będą dostępne, dopóki program profilujący nie otrzyma [icorprofilercallback::moduleattachedtoassembly —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotnego.  
  
 Gdy `GetModuleInfo2` zwróci wartość, należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby zawierały nazwę pełnego pliku modułu. Aby to zrobić, porównaj wartość która `pcchName` wskazuje z wartością `cchName` parametru. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większego `szName` buforu, zaktualizuj `cchName` przy użyciu nowych, większy rozmiar i Wywołaj `GetModuleInfo2` ponownie.  
  
 Alternatywnie, można wywołać `GetModuleInfo2` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcchName` i wywołać `GetModuleInfo2` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
