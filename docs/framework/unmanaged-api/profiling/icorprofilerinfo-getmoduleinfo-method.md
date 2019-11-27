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
ms.openlocfilehash: aae6d33166a7685e07c4d82f654f803600e37eec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438895"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo — Metoda
Podanym IDENTYFIKATORem modułu zwraca nazwę pliku modułu i identyfikator zestawu nadrzędnego modułu.  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="remarks"></a>Uwagi  
 W przypadku modułów dynamicznych parametr `szName` jest pustym ciągiem, a adres podstawowy to 0 (zero).  
  
 Mimo że metoda `GetModuleInfo` może być wywoływana, gdy tylko identyfikator modułu istnieje, identyfikator zestawu nadrzędnego nie będzie dostępny do momentu otrzymania przez profiler wywołania zwrotnego [ICorProfilerCallback:: ModuleAttachedToAssembly —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) .  
  
 Gdy `GetModuleInfo` zwraca, należy sprawdzić, czy bufor `szName` był wystarczająco duży, aby zawierał pełną nazwę pliku modułu. W tym celu należy porównać wartość, która `pcchName` wskazuje na wartość parametru `cchName`. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy bufor `szName`, zaktualizuj `cchName` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetModuleInfo`.  
  
 Alternatywnie można najpierw wywołać `GetModuleInfo` z buforem `szName` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcchName` i ponownie wywołać `GetModuleInfo`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [GetModuleInfo2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
