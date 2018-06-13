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
ms.openlocfilehash: e3579020ce268cd59a091e685fae2e97b3191c55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456126"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>ICorProfilerInfo::GetAssemblyInfo — Metoda
Akceptuje identyfikator zestawu i zwraca nazwę zestawu i identyfikator jej manifestu modułu.  
  
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
 [out] Bufor dostarczane przez obiekt wywołujący znaków dwubajtowych. Po powrocie z funkcji, będzie zawierać nazwy zestawu.  
  
 `pAppDomainId`  
 [out] Wskaźnik do identyfikator domeny aplikacji, która zawiera zestaw.  
  
 `pModuleId`  
 [out] Wskaźnik do Identyfikatora modułu manifestu zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Po powrocie z tej metody, należy sprawdzić, czy `szName` bufor był wystarczająco duży, aby zawierać pełnej nazwy zestawu. W tym celu należy porównać wartości który `pcchName` wskazuje wartość `cchName` parametru. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy `szName` buforu, zaktualizuj `cchName` z nowej, większy rozmiar i wywołanie `GetAssemblyInfo` ponownie.  
  
 Alternatywnie można wywołać `GetAssemblyInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można dostosować rozmiar buforu, na podstawie wartości zwracane w `pcchName` i Wywołaj `GetAssemblyInfo` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
