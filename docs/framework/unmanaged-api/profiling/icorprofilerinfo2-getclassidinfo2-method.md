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
ms.openlocfilehash: a33e51969dc0579d976f08470ebc6e2bcca04dd7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497169"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 — Metoda
Pobiera moduł nadrzędny i token metadanych dla otwartej definicji ogólnej określonej klasy, `ClassID` klasy nadrzędnej i `ClassID` argumentu dla każdego typu, jeśli istnieje, klasy.  
  
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
 podczas Rozmiar `typeArgs` tablicy.  
  
 `pcNumTypeArgs`  
 określoną Wskaźnik do całkowitej liczby dostępnych elementów.  
  
 `typeArgs`  
 określoną Tablica `ClassID` wartości, z których każdy reprezentuje identyfikator argumentu typu klasy. Gdy metoda zwraca, `typeArgs` będzie zawierać niektóre lub wszystkie dostępne `ClassID` wartości.  
  
## <a name="remarks"></a>Uwagi  
 `GetClassIDInfo2`Metoda jest podobna do metody [ICorProfilerInfo:: GetClassIDInfo —](icorprofilerinfo-getclassidinfo-method.md) , ale `GetClassIDInfo2` uzyskuje dodatkowe informacje o typie ogólnym.  
  
 Kod profilera może wywołać [ICorProfilerInfo:: GetModuleMetaData —](icorprofilerinfo-getmodulemetadata-method.md) w celu uzyskania interfejsu [metadanych](../metadata/index.md) dla danego modułu. Token metadanych, który jest zwracany do lokalizacji, do której się odwołuje się, `pTypeDefToken` może następnie zostać użyty w celu uzyskania dostępu do metadanych dla klasy.  
  
 Po `GetClassIDInfo2` powrocie należy sprawdzić, czy `typeArgs` bufor jest wystarczająco duży, aby można było zawierać wszystkie `ClassID` wartości. W tym celu należy porównać wartość wskazującą wartość `pcNumTypeArgs` `cNumTypeArgs` parametru. Jeśli `pcNumTypeArgs` wskazuje wartość, która jest większa niż `cNumTypeArgs` , Przydziel większy `typeArgs` bufor, zaktualizuj `cNumTypeArgs` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetClassIDInfo2` .  
  
 Alternatywnie, można najpierw wywołać `GetClassIDInfo2` z buforem o zerowej długości, `typeArgs` Aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić `typeArgs` rozmiar buforu na wartość zwracaną w `pcNumTypeArgs` i `GetClassIDInfo2` ponownie wywołać.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
