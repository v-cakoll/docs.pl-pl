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
ms.openlocfilehash: 96cde35c7151bb7ce58715f2826feaa59b30efab
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862311"
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
 Dla modułów dynamicznych parametr `szName` jest nazwą metadanych modułu, a adres podstawowy to 0 (zero). Nazwa metadanych jest wartością w kolumnie Nazwa z tabeli modułu w metadanych. Jest to również uwidocznione jako właściwość <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> do kodu zarządzanego, a jako parametr `szName` metody [IMetaDataImport:: GetScopeProps —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) do niezarządzanego kodu klienta metadanych.  
  
 Mimo że metoda `GetModuleInfo2` może być wywoływana, gdy tylko identyfikator modułu istnieje, identyfikator zestawu nadrzędnego nie będzie dostępny do momentu otrzymania przez profiler wywołania zwrotnego [ICorProfilerCallback:: ModuleAttachedToAssembly —](icorprofilercallback-moduleattachedtoassembly-method.md) .  
  
 Gdy `GetModuleInfo2` zwraca, należy sprawdzić, czy bufor `szName` był wystarczająco duży, aby zawierał pełną nazwę pliku modułu. W tym celu należy porównać wartość, która `pcchName` wskazuje na wartość parametru `cchName`. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy bufor `szName`, zaktualizuj `cchName` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetModuleInfo2`.  
  
 Alternatywnie można najpierw wywołać `GetModuleInfo2` z buforem `szName` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcchName` i ponownie wywołać `GetModuleInfo2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
