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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b8211e46b1a46d15befba17a52cd626d91f95fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616787"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>ICorProfilerInfo::GetAssemblyInfo — Metoda
Akceptuje identyfikator zestawu i zwraca nazwę zestawu i identyfikator jego manifestu modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `assemblyId`  
 [in] Identyfikator zestawu.  
  
 `cchName`  
 [in] Długość w znakach, z `szName`.  
  
 `pcchName`  
 [out] Wskaźnik do znaku całkowita długość nazwy zestawu.  
  
 `szName`  
 [out] Bufor dostarczane przez obiekt wywołujący znaku dwubajtowego. Po powrocie z tej funkcji będzie zawierać nazwę zestawu.  
  
 `pAppDomainId`  
 [out] Wskaźnik do Identyfikatora domeny aplikacji, który zawiera zestaw.  
  
 `pModuleId`  
 [out] Wskaźnik do Identyfikatora modułu manifestu zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Po powrocie z tej metody należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby zawierać pełną nazwę zestawu. Aby to zrobić, porównaj wartość która `pcchName` wskazuje z wartością `cchName` parametru. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większego `szName` buforu, zaktualizuj `cchName` przy użyciu nowych, większy rozmiar i Wywołaj `GetAssemblyInfo` ponownie.  
  
 Alternatywnie, można wywołać `GetAssemblyInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można dostosować rozmiar buforu, w oparciu o wartości zwracanej w `pcchName` i wywołać `GetAssemblyInfo` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
