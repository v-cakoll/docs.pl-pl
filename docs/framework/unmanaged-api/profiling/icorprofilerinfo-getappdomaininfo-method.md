---
title: ICorProfilerInfo::GetAppDomainInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af83fbeb64ad33910b45d49f987ffae130a2179e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455386"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>ICorProfilerInfo::GetAppDomainInfo — Metoda
Akceptuje identyfikator domeny aplikacji. Zwraca nazwę domeny aplikacji i identyfikator procesu, który go zawiera.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `appDomainId`  
 [in] Identyfikator domeny aplikacji.  
  
 `cchName`  
 [in] Długość w znakach, z `szName` buforze.  
  
 `pcchName`  
 [out] Wskaźnik do całkowita liczba znaków nazwy domeny aplikacji.  
  
 `szName`  
 [out] Bufor dostarczane przez obiekt wywołujący znaków dwubajtowych. Gdy metoda zwróci wartość, `szName` będzie zawierać nazwę domeny aplikacji pełnej lub częściowej.  
  
 `pProcessId`  
 [out] Wskaźnik do Identyfikatora procesu, który zawiera domeny aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Po powrocie z tej metody, należy sprawdzić, czy `szName` bufor był wystarczająco duży, aby zawierała pełną nazwę domeny aplikacji. W tym celu należy porównać wartości który `pcchName` wskazuje wartość `cchName` parametru. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy `szName` buforu, zaktualizuj `cchName` z nowej, większy rozmiar i wywołanie `GetAppDomainInfo` ponownie.  
  
 Alternatywnie można wywołać `GetAppDomainInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne. Rozmiar buforu można następnie ustawić wartość zwracana w `pcchName` i Wywołaj `GetAppDomainInfo` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
