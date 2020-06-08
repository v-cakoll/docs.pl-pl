---
title: ICorProfilerInfo::GetAssemblyInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 41083b2fcd61a9a726e835c3d5710308aa634600
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498651"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>ICorProfilerInfo::GetAssemblyInfo — Metoda
Akceptuje identyfikator zestawu i zwraca nazwę zestawu oraz identyfikator modułu manifestu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a>Parametry  
 `assemblyId`  
 podczas Identyfikator zestawu.  
  
 `cchName`  
 podczas Długość, w znakach, z `szName` .  
  
 `pcchName`  
 określoną Wskaźnik do łącznej długości znaku nazwy zestawu.  
  
 `szName`  
 określoną Bufor znaków udostępniany przez obiekt wywołujący. Gdy funkcja zwraca, będzie zawierać nazwę zestawu.  
  
 `pAppDomainId`  
 określoną Wskaźnik do identyfikatora domeny aplikacji, który zawiera zestaw.  
  
 `pModuleId`  
 określoną Wskaźnik do identyfikatora modułu manifestu zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Po powrocie tej metody należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby pomieścić pełną nazwę zestawu. W tym celu należy porównać wartość wskazującą wartość `pcchName` `cchName` parametru. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName` , Przydziel większy `szName` bufor, zaktualizuj `cchName` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetAssemblyInfo` .  
  
 Alternatywnie, można najpierw wywołać `GetAssemblyInfo` z buforem o zerowej długości, `szName` Aby uzyskać prawidłowy rozmiar buforu. Następnie można dostosować rozmiar buforu na podstawie wartości zwróconej w `pcchName` i `GetAssemblyInfo` ponownie wywołać.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
