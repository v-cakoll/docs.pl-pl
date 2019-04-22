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
ms.openlocfilehash: 69db53c03d68e30507ff3ab2b11b663970d59af0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090813"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo — Metoda
Podany identyfikator modułu zwraca nazwę pliku modułu i identyfikator zestawu nadrzędnego modułu.  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="remarks"></a>Uwagi  
 Dla modułów dynamicznych `szName` parametr jest pustym ciągiem, a adres podstawowy ma wartość 0 (zero).  
  
 Mimo że `GetModuleInfo` można wywołać metody, jak istnieje identyfikator modułu, identyfikator zestawu nadrzędnego nie będą dostępne, dopóki program profilujący nie otrzyma [icorprofilercallback::moduleattachedtoassembly —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotnego.  
  
 Gdy `GetModuleInfo` zwróci wartość, należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby zawierały nazwę pełnego pliku modułu. Aby to zrobić, porównaj wartość która `pcchName` wskazuje z wartością `cchName` parametru. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większego `szName` buforu, zaktualizuj `cchName` przy użyciu nowych, większy rozmiar i Wywołaj `GetModuleInfo` ponownie.  
  
 Alternatywnie, można wywołać `GetModuleInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcchName` i wywołać `GetModuleInfo` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [GetModuleInfo2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
