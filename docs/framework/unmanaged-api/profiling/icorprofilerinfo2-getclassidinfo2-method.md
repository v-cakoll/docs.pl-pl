---
title: ICorProfilerInfo2::GetClassIDInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: 8ce02b8b44074bed2da9e302f95a67a528601bf8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433440"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 — Metoda
Pobiera moduł nadrzędny i token metadanych dla otwartej definicji ogólnej określonej klasy, `ClassID` jej klasy nadrzędnej i `ClassID` dla każdego argumentu typu, jeśli istnieje, klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 podczas Identyfikator klasy, dla której będą pobierane informacje.  
  
 `pModuleId`  
 określoną Wskaźnik na identyfikator modułu nadrzędnego dla otwartej definicji ogólnej dla określonej klasy.  
  
 `pTypeDefToken`  
 określoną Wskaźnik do tokenu metadanych dla otwartej definicji ogólnej określonej klasy.  
  
 `pParentClassId`  
 określoną Wskaźnik na identyfikator klasy nadrzędnej.  
  
 `cNumTypeArgs`  
 podczas Rozmiar tablicy `typeArgs`.  
  
 `pcNumTypeArgs`  
 określoną Wskaźnik do całkowitej liczby dostępnych elementów.  
  
 `typeArgs`  
 określoną Tablica wartości `ClassID`, z których każdy reprezentuje identyfikator argumentu typu klasy. Gdy metoda zwraca, `typeArgs` będzie zawierać niektóre lub wszystkie dostępne `ClassID` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetClassIDInfo2` jest podobna do metody [ICorProfilerInfo:: GetClassIDInfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) , ale `GetClassIDInfo2` uzyskuje dodatkowe informacje o typie ogólnym.  
  
 Kod profilera może wywołać [ICorProfilerInfo:: GetModuleMetaData —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) w celu uzyskania interfejsu [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) dla danego modułu. Token metadanych, który jest zwracany do lokalizacji, do której odwołuje się `pTypeDefToken`, może następnie zostać użyty w celu uzyskania dostępu do metadanych dla klasy.  
  
 Po powrocie `GetClassIDInfo2` należy sprawdzić, czy bufor `typeArgs` był wystarczająco duży, aby zawierał wszystkie wartości `ClassID`. W tym celu należy porównać wartość, która `pcNumTypeArgs` wskazuje na wartość parametru `cNumTypeArgs`. Jeśli `pcNumTypeArgs` wskazuje wartość, która jest większa niż `cNumTypeArgs`, Przydziel większy bufor `typeArgs`, zaktualizuj `cNumTypeArgs` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetClassIDInfo2`.  
  
 Alternatywnie można najpierw wywołać `GetClassIDInfo2` z buforem `typeArgs` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić `typeArgs` rozmiar buforu na wartość zwróconą w `pcNumTypeArgs` i ponownie wywołać `GetClassIDInfo2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
