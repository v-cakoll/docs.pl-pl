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
ms.openlocfilehash: b5cec1022c9d4a2c96e4216aa09d4c0f7795b4f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751828"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout — Metoda
Pobiera informacje o układu, w pamięci, pól zdefiniowanych przez określonej klasy. Oznacza to, że ta metoda pobiera przesunięcia pól tej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `classID`  
 [in] Identyfikator klasy, dla którego będą pobierane układu.  
  
 `rFieldOffset`  
 [out w] Tablica [cor_field_offset —](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktur, z których każdy zawiera tokeny i przesunięcia pól tej klasy.  
  
 `cFieldOffset`  
 [in] Rozmiar `rFieldOffset` tablicy.  
  
 `pcFieldOffset`  
 [out] Wskaźnik do całkowitej liczby dostępnych elementów. Jeśli `cFieldOffset` wynosi 0, ta wartość wskazuje liczbę potrzebnych elementów.  
  
 `pulClassSize`  
 [out] Wskaźnik do lokalizacji, która zawiera rozmiar w bajtach klasy.  
  
## <a name="remarks"></a>Uwagi  
 `GetClassLayout` Metoda zwraca tylko te pola, które są definiowane przez samej klasy. Jeśli klasa nadrzędna klasy została zdefiniowana również pola, program profilujący musi wywołać `GetClassLayout` na klasy nadrzędnej w celu uzyskania tych pól.  
  
 Jeśli używasz `GetClassLayout` przy użyciu klas parametrów metody zakończy się niepowodzeniem z kodem błędu E_INVALIDARG. Użyj [icorprofilerinfo2::getstringlayout —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) można pobrać informacji o układzie ciągu. `GetClassLayout` zostanie również zakończyć się niepowodzeniem po wywołaniu z klasą tablicy.  
  
 Po `GetClassLayout` zwróci wartość, należy sprawdzić, czy `rFieldOffset` bufor jest wystarczająco duży, aby zawierała wszystkich dostępnych `COR_FIELD_OFFSET` struktury. Aby to zrobić, porównaj wartość która `pcFieldOffset` wskazuje z rozmiarem `rFieldOffset` podzielonej przez rozmiar `COR_FIELD_OFFSET` struktury. Jeśli `rFieldOffset` nie jest duży, Przydziel wystarczająca, większego `rFieldOffset` buforu, zaktualizuj `cFieldOffset` przy użyciu nowych, większy rozmiar i Wywołaj `GetClassLayout` ponownie.  
  
 Alternatywnie, można wywołać `GetClassLayout` o zerowej długości `rFieldOffset` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcFieldOffset` i wywołać `GetClassLayout` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
