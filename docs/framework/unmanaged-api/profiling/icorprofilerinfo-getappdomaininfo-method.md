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
ms.openlocfilehash: 8c13ce443037d706f9eba49760ba76f47c5a6538
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448173"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>ICorProfilerInfo::GetAppDomainInfo — Metoda
Akceptuje identyfikator domeny aplikacji. Zwraca nazwę domeny aplikacji i identyfikator procesu, który go zawiera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a>Parametry  
 `appDomainId`  
 podczas Identyfikator domeny aplikacji.  
  
 `cchName`  
 podczas Długość (w znakach) `szName` buforu powrotu.  
  
 `pcchName`  
 określoną Wskaźnik do łącznej długości znaku nazwy domeny aplikacji.  
  
 `szName`  
 określoną Bufor znaków udostępniany przez obiekt wywołujący. Gdy metoda zwraca, `szName` będzie zawierać pełną lub częściową nazwę domeny aplikacji.  
  
 `pProcessId`  
 określoną Wskaźnik do identyfikatora procesu, który zawiera domenę aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Po powrocie tej metody należy sprawdzić, czy bufor `szName` był wystarczająco duży, aby zawierał pełną nazwę domeny aplikacji. W tym celu należy porównać wartość, która `pcchName` wskazuje na wartość parametru `cchName`. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy bufor `szName`, zaktualizuj `cchName` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetAppDomainInfo`.  
  
 Alternatywnie można najpierw wywołać `GetAppDomainInfo` z buforem `szName` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcchName` i ponownie wywołać `GetAppDomainInfo`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
