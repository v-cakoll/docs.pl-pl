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
ms.openlocfilehash: 37400e3b69b3884e31479fd7cdfccb473408bfbf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433395"
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
 [in. out] Tablica struktur [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , z których każdy zawiera tokeny i przesunięcia pól klasy.  
  
 `cFieldOffset`  
 podczas Rozmiar tablicy `rFieldOffset`.  
  
 `pcFieldOffset`  
 określoną Wskaźnik do łącznej liczby dostępnych elementów. Jeśli `cFieldOffset` wynosi 0, ta wartość wskazuje liczbę wymaganych elementów.  
  
 `pulClassSize`  
 określoną Wskaźnik do lokalizacji zawierającej rozmiar (w bajtach) klasy.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetClassLayout` zwraca tylko pola zdefiniowane przez samą klasę. Jeśli Klasa nadrzędna klasy ma również zdefiniowane pola, profiler musi wywołać `GetClassLayout` w klasie nadrzędnej, aby uzyskać te pola.  
  
 Jeśli używasz `GetClassLayout` z klasami ciągów, metoda zakończy się niepowodzeniem z kodem błędu E_INVALIDARG. Użyj [ICorProfilerInfo2:: GetStringLayout —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) , aby uzyskać informacje na temat układu ciągu. `GetClassLayout` również zakończy się niepowodzeniem w przypadku wywołania z klasą Array.  
  
 Po powrocie `GetClassLayout` należy sprawdzić, czy bufor `rFieldOffset` był wystarczająco duży, aby zawierał wszystkie dostępne struktury `COR_FIELD_OFFSET`. W tym celu należy porównać wartość `pcFieldOffset` punkty z rozmiarem `rFieldOffset` podzielonym przez rozmiar struktury `COR_FIELD_OFFSET`. Jeśli `rFieldOffset` nie jest wystarczająco duży, Przydziel większy bufor `rFieldOffset`, zaktualizuj `cFieldOffset` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetClassLayout`.  
  
 Alternatywnie można najpierw wywołać `GetClassLayout` z buforem `rFieldOffset` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcFieldOffset` i ponownie wywołać `GetClassLayout`.  
  
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
