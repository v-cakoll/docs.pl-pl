---
title: ICorProfilerInfo2::GetClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b826e9c30fbf7007ac6b0093608ab7d926cc499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout — Metoda
Pobiera informacje o układzie, w pamięci, pól zdefiniowanych przez określonej klasy. Oznacza to, że ta metoda pobiera przesunięcia pól tej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classID`  
 [in] Identyfikator klasy, dla którego mają zostać pobrane układu.  
  
 `rFieldOffset`  
 [w, out] Tablica [cor_field_offset —](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z których każdy zawiera tokeny i przesunięcia pól tej klasy.  
  
 `cFieldOffset`  
 [in] Rozmiar `rFieldOffset` tablicy.  
  
 `pcFieldOffset`  
 [out] Wskaźnik do całkowitej liczby dostępnych elementów. Jeśli `cFieldOffset` wynosi 0, ta wartość wskazuje liczbę potrzebnych elementów.  
  
 `pulClassSize`  
 [out] Wskaźnik do lokalizacji, która zawiera rozmiar w bajtach klasy.  
  
## <a name="remarks"></a>Uwagi  
 `GetClassLayout` Metoda zwraca tylko pola zdefiniowane przez samej klasy. Jeśli klasy nadrzędnej klasy zdefiniowano także pól, należy wywołać profilera `GetClassLayout` w klasie nadrzędnej w celu uzyskania tych pól.  
  
 Jeśli używasz `GetClassLayout` z klasami ciąg, metoda zakończy się niepowodzeniem z kodem błędu E_INVALIDARG. Użyj [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) można pobrać informacji o układzie ciągu. `GetClassLayout` również zakończą się po wywołaniu z klasą tablicy.  
  
 Po `GetClassLayout` zwróci wartość, należy sprawdzić, czy `rFieldOffset` bufor był wystarczająco duży, aby zawierała wszystkie dostępne `COR_FIELD_OFFSET` struktury. W tym celu należy porównać wartości który `pcFieldOffset` wskazuje rozmiar `rFieldOffset` podzielonej przez rozmiar `COR_FIELD_OFFSET` struktury. Jeśli `rFieldOffset` nie jest duży, Przydziel wystarczająca, większego `rFieldOffset` buforu, zaktualizuj `cFieldOffset` z nowej, większy rozmiar i wywołanie `GetClassLayout` ponownie.  
  
 Alternatywnie można wywołać `GetClassLayout` o zerowej długości `rFieldOffset` buforu w celu uzyskania rozmiar buforu poprawne. Rozmiar buforu można następnie ustawić wartość zwracana w `pcFieldOffset` i Wywołaj `GetClassLayout` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
