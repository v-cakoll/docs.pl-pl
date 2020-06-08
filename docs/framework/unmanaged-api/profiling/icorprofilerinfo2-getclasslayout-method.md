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
ms.openlocfilehash: ac35b18ce8c45c95bb2fb8e820423470ca1b75bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497156"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout — Metoda
Pobiera informacje o układzie, w pamięci, pól zdefiniowanych przez określoną klasę. Oznacza to, że ta metoda pobiera przesunięcia pól klasy.  
  
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
 podczas Identyfikator klasy, dla której zostanie pobrany układ.  
  
 `rFieldOffset`  
 [in. out] Tablica struktur [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) , z których każdy zawiera tokeny i przesunięcia pól klasy.  
  
 `cFieldOffset`  
 podczas Rozmiar `rFieldOffset` tablicy.  
  
 `pcFieldOffset`  
 określoną Wskaźnik do łącznej liczby dostępnych elementów. Jeśli `cFieldOffset` jest równa 0, ta wartość wskazuje wymaganą liczbę elementów.  
  
 `pulClassSize`  
 określoną Wskaźnik do lokalizacji zawierającej rozmiar (w bajtach) klasy.  
  
## <a name="remarks"></a>Uwagi  
 `GetClassLayout`Metoda zwraca tylko pola zdefiniowane przez samą klasę. Jeśli Klasa nadrzędna klasy ma również zdefiniowane pola, profiler musi wywołać `GetClassLayout` klasy nadrzędnej, aby uzyskać te pola.  
  
 Jeśli używasz `GetClassLayout` z klasami ciągów, metoda zakończy się niepowodzeniem z kodem błędu E_INVALIDARG. Użyj [ICorProfilerInfo2:: GetStringLayout —](icorprofilerinfo2-getstringlayout-method.md) , aby uzyskać informacje na temat układu ciągu. `GetClassLayout`również zakończy się niepowodzeniem w przypadku wywołania z klasą Array.  
  
 Po `GetClassLayout` powrocie należy sprawdzić, czy `rFieldOffset` bufor jest wystarczająco duży, aby można było zawierać wszystkie dostępne `COR_FIELD_OFFSET` struktury. W tym celu należy porównać wartość, która `pcFieldOffset` wskazuje na wielkość `rFieldOffset` podzieloną przez rozmiar `COR_FIELD_OFFSET` struktury. Jeśli `rFieldOffset` nie jest wystarczająco duży, Przydziel większy `rFieldOffset` bufor, zaktualizuj `cFieldOffset` go przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetClassLayout` .  
  
 Alternatywnie, można najpierw wywołać `GetClassLayout` z buforem o zerowej długości, `rFieldOffset` Aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwracaną w `pcFieldOffset` i `GetClassLayout` ponownie wywołać.  
  
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
