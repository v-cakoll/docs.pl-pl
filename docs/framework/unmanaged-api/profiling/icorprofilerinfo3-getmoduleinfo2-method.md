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
ms.openlocfilehash: d2b7e93866bf0aa79849925234a4d6e4cc9b5b52
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502824"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 — Metoda
Podano identyfikator modułu, zwraca nazwę pliku modułu, identyfikator zestawu nadrzędnego modułu i maskę bitów opisującą właściwości modułu.  
  
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
 podczas Identyfikator modułu, dla którego będą pobierane informacje.  
  
 `ppBaseLoadAddress`  
 określoną Adres podstawowy, z którego moduł jest załadowany.  
  
 `cchName`  
 podczas Długość (w znakach) `szName` buforu powrotu.  
  
 `pcchName`  
 określoną Wskaźnik do łącznej długości znaku nazwy pliku modułu, który jest zwracany.  
  
 `szName`  
 określoną Bufor znaków udostępniany przez obiekt wywołujący. Gdy metoda zwraca, ten bufor zawiera nazwę pliku modułu.  
  
 `pAssemblyId`  
 określoną Wskaźnik do identyfikatora zestawu nadrzędnego modułu.  
  
 `pdwModuleFlags`  
 określoną Maska bitów wartości z wyliczenia [COR_PRF_MODULE_FLAGS](cor-prf-module-flags-enumeration.md) , która określa właściwości modułu.  
  
## <a name="remarks"></a>Uwagi  
 Dla modułów dynamicznych `szName` parametr jest nazwą metadanych modułu, a adres podstawowy to 0 (zero). Nazwa metadanych jest wartością w kolumnie Nazwa z tabeli modułu w metadanych. Jest to również uwidocznione jako <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> Właściwość do kodu zarządzanego, a jako `szName` parametr metody [IMetaDataImport:: GetScopeProps —](../metadata/imetadataimport-getscopeprops-method.md) do niezarządzanego kodu klienta metadanych.  
  
 Mimo że `GetModuleInfo2` Metoda może być wywoływana, gdy tylko identyfikator modułu już istnieje, identyfikator zestawu nadrzędnego nie będzie dostępny do momentu otrzymania przez profiler wywołania zwrotnego [ICorProfilerCallback:: ModuleAttachedToAssembly —](icorprofilercallback-moduleattachedtoassembly-method.md) .  
  
 Gdy `GetModuleInfo2` zwraca, należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby można było zawierać pełną nazwę pliku modułu. W tym celu należy porównać wartość wskazującą wartość `pcchName` `cchName` parametru. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName` , Przydziel większy `szName` bufor, zaktualizuj `cchName` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetModuleInfo2` .  
  
 Alternatywnie, można najpierw wywołać `GetModuleInfo2` z buforem o zerowej długości, `szName` Aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwracaną w `pcchName` i `GetModuleInfo2` ponownie wywołać.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
